---
title: 雲端上的Adobe Commerce出現變數/匯出資料夾許可權問題
description: 此文章解決由於「var/export/email」資料夾中的伺服器檔案許可權問題而無法匯出產品資料的問題。 症狀包括使用者介面中無法使用產品和目錄匯出，但在使用SSH時可見。
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 雲端上的Adobe Commerce出現變數/匯出資料夾許可權問題

此文章針對伺服器在`var/export/email`資料夾中有檔案許可權問題，導致您無法匯出產品資料的問題，提供解決方案。 症狀包括使用者介面中無法使用產品和目錄匯出，但在使用SSH時可見。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce， 2.3.0-2.3.7-p2， 2.4.0-2.4.3-p1

## 問題

您無法匯出`var/export/email`或`var/export/archive`資料夾中的檔案。
由於`var/export/email`或`var/export/email/archive`的許可權，部署失敗，因為該封存資料夾是在電子郵件底下建立的，如果我只是執行匯出/電子郵件，有時仍會有問題)，除了新增專案到子資料夾`var/export/email/archive`的帳戶以外。

<u>要再現的步驟</u>：

在管理員中，移至&#x200B;**系統** > *資料傳輸* > **匯出**。
選取要儲存在`var/export/`資料夾中的CSV檔案。

<u>預期結果</u>：

CSV檔案是可見的，並且可以匯出。

<u>實際結果</u>：

CSV檔案不可見。 您也會看到許可權被拒絕的訊息： *RecursiveDirectoryIterator：：__construct(/app/project id>/var/export/email)：無法開啟目錄：許可權被拒絕*

所有匯出型態都會收到相同的訊息：進階定價、客戶財務、客戶主要檔案與客戶地址。

## 原因

這是因為`/var`中建立的資料夾具有不完整的許可權所造成： `d-wxrwsr-T`。 T粘性位元表示使用者只能刪除他們擁有的檔案，但缺少可執行檔表示他們無法在目錄中建立檔案。

當系統建立名為`export`的資料夾，該資料夾儲存名為`email`的資料夾，該資料夾儲存名為`archive`的資料夾時，經常會注意到這個問題。

若要檢查目錄是否有這些設定錯誤的許可權，請在CLI/終端機中執行以下命令：

`ls -ld var/export/`

如果許可權設定錯誤，輸出將為：

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## 解決方案

若要解決此問題，請執行以下命令，將資料夾的許可權更新為777，然後遞回更新所有檔案：

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## 相關閱讀

* 使用手冊中的[匯出](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/data-transfer/data-export)。
