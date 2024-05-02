---
title: 清除Commerce管理員中的快取時發生錯誤
description: '本文說明如何在Commerce管理員中清除快取時，識別錯誤訊息發生的原因。 當您嘗試透過「管理員」清除快取時，您會收到下列訊息：'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 清除Commerce管理員中的快取時發生錯誤

本文說明如何在Commerce管理員中清除快取時，識別發生錯誤訊息的原因。 當您嘗試透過「管理員」清除快取時，您會收到下列訊息：
*無法刪除/app/project-id/pub/media/catalog/product/cache/directory/filename」檔案。 警告！unlink(/app/project id/pub/media/catalog/product/cache/directory/filename)：沒有這樣的檔案或目錄*

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.3.0-2.3.7、2.4.0-2.4.2-p1

## 問題

當您嘗試透過「管理員」清除快取時，您會收到錯誤訊息。

<u>要再現的步驟：</u>

1. 在Admin中，前往 **系統** > **工具** > **快取管理**.
1. 選取任一清除快取選項。

<u>預期結果：</u>

您已成功排清Adobe Commerce快取，沒有錯誤。

<u>實際結果：</u>

您收到「無法刪除檔案」錯誤。

## 原因

此錯誤與啟動快取清除作業與報告其完成之間的延遲有關。

## 解決方案

1. 確認錯誤中提到的檔案不存在伺服器上（檢查快取清除是否成功）：

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

如果您看到以下輸出：

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

作業完成時，曾嘗試清除檔案。 這並非錯誤；而是預期有時會發生的訊息並行問題。 沒有需要疑難排解的問題。
不過，如果輸出顯示檔案仍在快取中，您需要 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## 相關閱讀

* [快取管理](https://docs.magento.com/user-guide/system/cache-management.html) （位於我們的開發人員檔案中）。
