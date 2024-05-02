---
title: 'ACSD-51645：如果擴充功能Magento_OfflineShipping已停用，儲存新的購物車價格規則'
description: 套用ACSD-51645修補程式以修正Adobe Commerce問題，此問題會在停用擴充功能Magento_OfflineShipping的情況下，儲存新的購物車價格規則時發生錯誤。
exl-id: 301086bb-7aab-4e74-93e6-9080eebcb026
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51645：如果停用擴充功能Magento_OfflineShipping，儲存新的購物車價格規則

如果停用擴充功能Magento_OfflineShipping，ACSD-51645修補程式會修正儲存新購物車價格規則時發生錯誤的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.33。 修補程式ID為ACSD-51645。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果擴充功能，儲存新的購物車價格規則時發生錯誤 `Magento_OfflineShipping` 已停用。

<u>要再現的步驟</u>：

1. 停用 `Magento_OfflineShipping` 模組。
1. 登入 **管理員**.
1. 前往 **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. 建立新的 **[!UICONTROL Cart Price Rule]**.
1. 填寫必填欄位。
1. 儲存 **[!UICONTROL Cart Price Rule]**.

<u>預期結果</u>：

已成功儲存購物車價格規則。

<u>實際結果</u>：

發生下列錯誤：
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
