---
title: MDVA-31763：目錄價格規則會還原，直到手動重新編列索引為止
description: MDVA-31763修補程式可解決在手動重新索引之前目錄價格規則會還原的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-31763。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763：目錄價格規則會還原，直到手動重新編列索引為止

MDVA-31763修補程式可解決在手動重新索引之前目錄價格規則會還原的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-31763。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在可設定的產品上執行`catalogrule_product`部分索引器時，目錄規則會消失。

<u>要再現的步驟</u>：

1. 登入管理員後端。
1. 移至&#x200B;**商店** > **屬性** > **產品**&#x200B;並搜尋「製造商」屬性。
   * 新增幾個選項，並將[用於促銷規則條件]設定為&#x200B;*是*。
1. 移至&#x200B;**存放區** > **屬性** > **屬性集**。
   * 選取預設屬性集，並將「manufacturer」屬性加入其中。
1. 建立具有一些變數的可設定產品。
1. 設定先前建立之可設定產品的「製造商」屬性值。
1. 建立目錄規則：
   * 使用中=是
   * 網站=主要網站
   * 客戶群組=未登入
   * 條件：製造商= \&lt;可設定產品的選取值>
   * 動作：任何折扣
1. 執行完整索引。
1. 檢查PDP上的產品價格，並確定價格正確。
1. 更新已建立之可設定產品的「權重」屬性。
1. 檢查PDP上的產品價格。

<u>預期結果</u>：

在可設定產品上設定的目錄價格規則在部分重新索引期間不會移除。

<u>實際結果</u>：

在部分重新索引期間，針對可設定產品設定的目錄價格規則會消失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
