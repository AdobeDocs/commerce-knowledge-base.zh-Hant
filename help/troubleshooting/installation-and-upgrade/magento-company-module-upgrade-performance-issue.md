---
title: B2B 1.5.2更新後Magento_Company模組升級中的效能問題
description: 本文針對B2B 1.5.2更新後Magento_Company模組升級中的效能問題提供Hotfix，解決company_structure表格中大型資料集的處理時間過長的問題。
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# B2B 1.5.2更新後Magento_Company模組升級中的效能問題

本文針對B2B 1.5.2更新後`Magento_Company`模組升級中的效能問題提供Hotfix，解決`company_structure`表格中大型資料集（~100,000筆以上的記錄）處理時間過長的問題。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.4.6-px + B2B 1.5.2
* Adobe Commerce （所有部署方法） 2.4.7-px + B2B 1.5.2
* Adobe Commerce （所有部署方法） 2.4.8 + B2B 1.5.2

## 問題

在更新至B2B 1.5.2之後升級`Magento_Company`模組，在處理大量記錄(~100,000+)時，會花很長的時間處理`company_structure`表格。

<u>必要條件</u>：

* 應該安裝ACSD-65540_B2B_1.5.2.patch。
* Adobe Commerce 2.4.6 - 2.4.8
* 套用ACSD-65540修補程式的B2B 1.5.0、1.5.1或B2B 1.5.2版

<u>要再現的步驟</u>：

1. 將公司指派給母公司，以建立公司階層。 如需詳細資訊，請參閱Adobe Commerce B2B指南中的[管理公司階層](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/b2b/company-management/manage-company-hierarchy)。
1. 將B2B升級至1.5.2版。

<u>預期結果</u>：

升級成功完成。

<u>實際結果</u>：

如果`company_structure`資料表中有許多記錄，則升級`Magento_Company`模組需要很長時間才能完成。

## 解決方案

若要解決此問題，請執行以下步驟：

1. 將B2B模組更新至1.5.2版：

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. 套用[ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip)。

1. 套用附加的[ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip)。
1. 套用修補程式後執行`bin/magento setup:upgrade`。

### 如何套用修補程式

解壓縮檔案，並在我們的支援知識庫中參閱[如何套用Adobe](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)提供的撰寫器修補程式，以取得指示。

### 使用雲端修補程式套用修補程式

若為Adobe Commerce on Cloud商家，請遵循下列步驟：

1. 將雲端修補程式模組的版本更新為1.1.5，以安裝以MCLOUD-13605分發的ACSD-65540_B2B_1.5.2.patch。

   >[!NOTE]
   >
   >若要檢查是否已安裝修正程式，請執行：
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. 將ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch新增至`m2-hotfixes`目錄。
1. 認可並推播變更以開始重新部署和`bin/magento setup:upgrade`。 請參閱雲端上的Adobe Commerce指南中的[套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)以取得指示。

## 相關閱讀

* [由於遺失REGEXP_LIKE函式，升級至B2B 1.5.2失敗，並出現SQL語法錯誤](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
