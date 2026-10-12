---
title: 將佈景主題重設為預設值
description: 根據自訂主題和開發商店時可能會遇到的問題，您可能無法透過Commerce管理員存取。 您可以清除並重設為佈景主題預設值，而無需存取管理員。 清除主題後，將套用預設的Luma主題。
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%
---
# 將佈景主題重設為預設值

根據自訂主題和開發商店時可能會遇到的問題，您可能無法透過Commerce管理員存取。 您可以清除並重設為佈景主題預設值，而無需存取管理員。 清除主題後，將套用預設的Luma主題。

當您開發Adobe Commerce （所有部署）和Magento Open Source元件（模組、主題和語言套件）時，快速變化的環境需要您定期清除特定目錄和快取。 否則，您的程式碼會在例外情況下執行，並且無法正常運作。 如需詳細資訊，請參閱我們的開發人員檔案中的[開發期間清除目錄](https://developer.adobe.com/commerce/php/development/components/clear-directories/)。

## 環境與技術

* Adobe Commerce內部部署
* 雲端基礎結構上的Adobe Commerce
* Magento Open Source

## 先決條件

* 資料庫工具

## 步驟

如果您需要重設存放區主題，但無法存取「管理員」面板，可以執行下列動作在資料庫中重設主題：

1. 使用資料庫工具（例如[phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)）或從命令列手動存取資料庫，以執行下列SQL查詢： `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. 清除下列目錄：
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

這樣就不會在商店檢視層級上設定主題，當您重新載入商店首頁時，將會套用預設的Luma主題。

## 其他資訊

* 在開發人員檔案中於開發期間[清除目錄](https://developer.adobe.com/commerce/php/development/components/clear-directories/)
