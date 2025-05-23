---
title: 從2.2.X升級至2.3.X後不會載入快取影像
description: 本文針對在雲端基礎結構2.2.X上從Adobe Commerce升級為2.3.X後無法顯示快取影像的問題提供解決方案。
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# 從2.2.X升級至2.3.X後不會載入快取影像

本文針對在雲端基礎結構2.2.X上從Adobe Commerce升級為2.3.X後無法顯示快取影像的問題提供解決方案。

## 受影響的版本和版本：

* 雲端基礎結構上的Adobe Commerce Pro計畫架構2.2.X、2.3.X

## 問題

Adobe Commerce從2.2.X升級至2.3.X後，將無法使用快取的產品影像，而會顯示404頁面。

問題是由於`.magento.app.yaml`中設定的Nginx設定不正確所造成： `index.php` （或無）用於`"/media"`位置而非`passthru: /get.php`。

## 解決方案

1. 在`"/media"`位置檢查您的`.magento.app.yaml`設定檔。 正確的設定如下所示：

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. 如果`passthru`未設定為`"/get.php"`且未設定`expires`，請執行下列步驟。
1. 修正組態檔。
   * 入門計畫：自行修正檔案並推送變更。
   * 專業計畫：
   * 整合：自行修正檔案並推送變更。
   * 測試和生產：自行修正檔案、推送變更，然後建立[Adobe Commerce支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以套用它。

1. 在Commerce管理員中啟用Fastly影像最佳化（必須先設定Fastly），如<https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>中所述。

如果設定正確，但您仍然遇到問題，請繼續調查或聯絡[Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
