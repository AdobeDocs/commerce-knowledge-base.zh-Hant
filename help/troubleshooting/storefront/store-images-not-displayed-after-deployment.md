---
title: 部署後未顯示存放區影像
description: 本文提供部署後影像無法正確顯示時的解決方案。
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# 部署後未顯示存放區影像

本文提供部署後影像無法正確顯示時的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

當您使用可調整影像大小的店面主題時，影像在部署時不會顯示或從目錄頁面中消失。

## 原因

由於從快取載入影像，因此可能會發生這種情況。

## 解決方案

如果發生這種狀況，您可以使用「Magento」指令來重新產生影像快取並正確顯示影像。

若要執行此動作，您需要透過[雲端主控台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)取得的SSH資訊和存放區URL。

1. SSH至您的專案，此專案是[資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md)的來源，如開發人員檔案中的[SSH至環境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)所述。
1. 執行下列步驟，重新產生影像快取：

   ```bash
   php bin/magento catalog:images:resize
   ```

1. 透過商店URL測試類別頁面。
