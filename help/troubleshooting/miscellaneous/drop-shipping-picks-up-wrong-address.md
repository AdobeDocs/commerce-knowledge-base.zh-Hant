---
title: 直接運送擷取錯誤的地址
description: 送貨解決方案未擷取產品來源的地址。
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# 直接運送擷取錯誤的地址

## 問題

送貨解決方案未擷取產品來源的地址。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本），已安裝Magento詳細目錄
* Adobe Commerce內部部署2.3.0和更新版本，並安裝Magento詳細目錄
* Magento Open Source2.3.0和更新版本，並安裝Magento詳細目錄

### 原因

「Magento詳細目錄」目前不支援在結帳期間根據來源地址計算製造商直接出貨率。 而是在所有情況下都使用來自設定的預設商店位址。

## 相關閱讀

* [Magento詳細目錄常見問題集](https://github.com/magento/inventory/wiki/MSI-FAQs) 在GitHub中。
