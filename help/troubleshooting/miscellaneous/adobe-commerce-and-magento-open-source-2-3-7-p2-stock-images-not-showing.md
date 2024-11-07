---
title: 不顯示庫存影像，Adobe Commerce和Magento Open Source 2.3.7-p2
description: 針對上傳至檔案系統目錄「pub/media」或「pub/media/catalog」的Adobe庫存影像未顯示在Media Gallery UI中的問題，本文提供解決方案。 這是因為影像在允許的媒體集目錄之外。 若要使用這些影像來顯示，商家需要刪除檔案系統上的影像，並重新上傳至允許的媒體集目錄。
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 不顯示庫存影像，Adobe Commerce和Magento Open Source 2.3.7-p2

本文解決上傳至檔案系統目錄`pub/media`或`pub/media/catalog`的Adobe庫存影像未顯示在Media Gallery UI中的問題。 這是因為影像在允許的媒體集目錄之外。 若要使用這些影像來顯示，商家需要刪除檔案系統上的影像，並重新上傳至允許的媒體集目錄。

## 受影響的產品和版本

* Adobe Commerce和Magento Open Source 2.3.7-p2


## 問題

商家可以將Adobe Stock影像上傳至媒體收藏館的「儲存根」，但這些影像未出現在UI中，且看起來就像是未上傳一樣。 這是因為系統注意到影像已上傳到檔案系統，儘管Media Gallery UI中沒有該影像。 這表示一旦商家將影像上傳到`pub/media`或`pub/media/catalog`，他們將無法使用該影像，直到該影像直接在檔案系統中被刪除。

<u>要再現的步驟</u>

1. 使用有效的API金鑰啟用Adobe Stock。
1. 開啟媒體集（**目錄** > **類別** > **內容**&#x200B;區段>按一下&#x200B;**從媒體集選取**）。
1. 按一下&#x200B;**搜尋Adobe Stock**。
1. 選取影像。 按一下&#x200B;**儲存預覽**。 請注意，您可能需要重設Adobe Stock格線才能讓影像顯示。

<u>預期結果</u>：

影像隨即顯示。

<u>實際結果</u>：

顯示錯誤訊息： *找不到影像。 我們在媒體集中找不到此影像。*

## 原因

影像可以透過Adobe Stock上傳至Media Gallery儲存根。

## 解決方案

上傳Adobe Stock影像之前，請先選取媒體集儲存根目錄的任何子目錄（不包括&#x200B;**儲存根目錄** > **目錄**）。
從Adobe Stock檔案系統上的`pub/media`和`pub/media/catalog`資料夾中刪除已上傳的Adobe Commerce影像，並改為將影像上傳到任何允許的媒體集儲存根子目錄中（不包括&#x200B;**儲存根** > **目錄**）。

## 相關閱讀

* 使用手冊中的[媒體儲存空間](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/storage/media-storage)。
