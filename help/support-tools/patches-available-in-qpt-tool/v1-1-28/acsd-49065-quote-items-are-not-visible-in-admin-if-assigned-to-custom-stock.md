---
title: 'ACSD-49065：報價專案在管理員中不可見'
description: 套用ACSD-49065修補程式來修正Adobe Commerce問題，亦即如果報價專案僅指派給自訂庫存，則無法在管理員中看到報價專案。
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065：報價專案在管理員中不可見

ACSD-49065修補程式修正了報價專案僅指定給自訂庫存時無法在管理員中顯示的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-49065。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果報價專案僅指派給自訂庫存，則不會在管理員中顯示。

先決條件：

**[!UICONTROL B2B]** 和 **[!UICONTROL Inventory]** 必須安裝模組。

<u>要再現的步驟</u>：

1. 啟用 **[!UICONTROL Company]** 和 **[!UICONTROL B2B Quote]** 在 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. 建立次要 **[!UICONTROL Inventory Source]** 並將其指派給次要 **[!UICONTROL Inventory Stock]**.
1. 僅指派次要（非預設）以建立新產品 **[!UICONTROL Inventory Source]**.
1. 前往店面並建立新的公司帳戶。 登入身份 **[!UICONTROL Company Admin]**，然後將建立的產品新增至購物車。
1. 導覽至購物車並 *[!UICONTROL Request a Quote]*.
1. 前往管理員，並在以下網址檢視要求的報價單： **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>預期結果</u>：

專案會顯示在以新產品建立的新報價中，而不需重新儲存產品。

<u>實際結果</u>：

此 *[!UICONTROL Items Quoted]* 區段為空。 如果您重新儲存新建立的產品，專案就會出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
