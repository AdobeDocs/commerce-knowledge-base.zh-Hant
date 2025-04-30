---
title: 由於遺失REGEXP_LIKE函式，升級至B2B 1.5.2會因SQL語法錯誤而失敗
description: 本文提供嘗試更新company_structure表格時，由於遺失REGEXP_LIKE函式而發生SQL語法錯誤問題的Hotfix。
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: 04e17dfdf143e233eb2767064c1328990c899eda
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 由於遺失REGEXP_LIKE函式，升級至B2B 1.5.2會因SQL語法錯誤而失敗

>[!INFO]
>
>如果您在更新至B2B 1.5.2後升級`Magento_Company`模組時遇到效能問題，請套用附加的[ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip)。
>
>如需詳細資訊，請參閱Adobe Commerce知識庫中，B2B 1.5.2更新後Magento_Company模組升級中的[效能問題](/help/troubleshooting/installation-and-upgrade/magento-company-module-upgrade-performance-issue.md)。

本文提供嘗試更新`company_structure`資料表時，由於遺失`REGEXP_LIKE`函式而發生SQL語法錯誤的Hotfix。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.4.6-px + B2B 1.5.2 （使用[!DNL MariaDB] 10.6）
* Adobe Commerce （所有部署方法） 2.4.7-px + B2B 1.5.2 （使用[!DNL MariaDB] 10.6）

## 問題

嘗試更新`company_structure`資料表時，因為遺失`REGEXP_LIKE`函式，所以升級至B2B 1.5.2版會失敗，並出現SQL語法錯誤。

<u>必要條件</u>：

* MariaDB 10.6
* Adobe Commerce 2.4.6x或2.4.7x
* B2B 1.5.0或1.5.1版

<u>要再現的步驟</u>：

1. 將公司指派給母公司，以建立公司階層。 如需詳細資訊，請參閱Adobe Commerce B2B指南中的[管理公司階層](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy)。
1. 將B2B升級至1.5.2版。

<u>預期結果</u>：

升級成功完成。

<u>實際結果</u>：

`bin/magento setup:upgrade`因下列錯誤而失敗：

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## 解決方案

若要解決此問題，請執行以下步驟：

1. 將B2B模組更新至1.5.2版：

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. 套用附加的[ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip)修補程式。 請參考支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得指示。
1. 執行`bin/magento setup:upgrade`。

### 使用雲端修補程式套用修補程式

針對雲端基礎結構上的Adobe Commerce，請遵循下列步驟：

1. 將`cloud-patches`模組的版本更新為1.1.5：

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. 提交並推送變更以啟動重新部署。 請參閱雲端上的Adobe Commerce指南中的[套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)以取得指示。
