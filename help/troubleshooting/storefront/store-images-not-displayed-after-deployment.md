---
title: 部署後未顯示存放區影像
description: 本文提供部署後影像無法正確顯示時的解決方案。
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
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

如果發生這種狀況，您可以使用Magento指令來重新產生影像快取並正確顯示影像。

若要執行此動作，您需要透過[雲端主控台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hant)取得的SSH資訊和存放區URL。

1. SSH至您的專案，此專案是[資料庫傾印](/help/how-to/general/create-database-dump-on-cloud.md)的來源，如開發人員檔案中的[SSH至環境](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/secure-connections)所述。
1. 執行下列步驟，重新產生影像快取：

   ```bash
   php bin/magento catalog:images:resize
   ```

1. 透過商店URL測試類別頁面。
