---
title: 匯入不會更新套件組合選項順序
description: 針對從.csv檔案匯入產品後，套件組合產品選項會以匯入檔案所列不同的順序出現的問題，本文提供解決方案。
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 匯入不會更新套件組合選項順序

針對從.csv檔案匯入產品後，套件組合產品選項會以匯入檔案所列不同的順序出現的問題，本文提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce內部部署2.2.x、2.3.x
* Magento Open Source

## 問題

<u>必要條件</u>：

您有一個包含套件組合產品的有效.csv檔案。

<u>要再現的步驟</u>：

1. 使用[匯入功能](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/import/data-import)匯入檔案。
1. 開啟套件組合產品頁面。

<u>預期結果</u>：

選項順序與.csv檔案中的選項順序相同。

<u>實際結果</u>：

選項順序與.csv檔案中的選項順序不同。

## 原因

選項位置未明確宣告。

## 解決方案

1. 針對.csv檔案中`bundle_values`欄的`position`引數中的每個選項，明確宣告位置。 如需詳細指示，請參閱使用手冊中的[編輯產品資料](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data)。
1. 重複匯入操作。

如需匯入的一般資訊，請參閱使用手冊中的[匯入組合產品](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products)。
