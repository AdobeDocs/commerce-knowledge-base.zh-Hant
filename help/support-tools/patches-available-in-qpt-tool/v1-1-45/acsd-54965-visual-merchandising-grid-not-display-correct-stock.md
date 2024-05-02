---
title: 'ACSD-54965： [!UICONTROL Visual Merchandising] 格線未顯示正確的庫存'
description: 套用ACSD-54965修補程式以修正Adobe Commerce問題，其中 [!UICONTROL Visual Merchandising] 將產品指派給自訂庫存時，格線不顯示正確的庫存。
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965： [!UICONTROL Visual Merchandising] 格線未顯示正確的坯件

ACSD-54965修補程式修正了 [!UICONTROL Visual Merchandising] 將產品指派給自訂庫存時，格線不顯示正確的庫存。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.45。 修補程式ID為ACSD-54965。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 [!UICONTROL Visual Merchandising] 將產品指派給自訂庫存時，格線不顯示正確的庫存。

<u>要再現的步驟</u>：

1. 建立新的來源。
1. 建立新庫存。
1. 建立兩個產品：
   * 一個產品僅具有自訂庫存。
   * 一個產品僅具有預設庫存。
1. 將這些產品新增至類別。
1. 前往 [!UICONTROL visual Merchandising] 格線(*[!UICONTROL Products in Category]*)。

<u>實際結果</u>：

在 *[!UICONTROL All Store Views]* 範圍中，含有自訂庫存的產品不會顯示任何數量。 只有在 *[!UICONTROL Default Store View]* 選取範圍自訂庫存會顯示產品的數量。

<u>預期結果</u>：

如果範圍是，則格線顯示所有庫存資訊 *[!UICONTROL All Store Views]*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
