---
title: '''ACSD-47336： [!UICONTROL Something went wrong] 在Adobe Commerce Admin中關閉通知時發生錯誤'
description: 套用ACSD-47336修補程式來修正使用者看到的Adobe Commerce問題 [!UICONTROL Something went wrong] 在中停用通知時發生錯誤 [!DNL Commerce] 管理員。
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336： _[!UICONTROL Something went wrong]_在Adobe Commerce管理中關閉通知時發生錯誤

ACSD-47336修補程式修正使用者看到 _[!UICONTROL Something went wrong]_在中停用通知時發生錯誤 [!DNL Commerce] 管理員。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.24。 修補程式ID為ACSD-47336。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法）： 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法）： 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者看到 _[!UICONTROL Something went wrong]_在中停用通知時發生錯誤 [!DNL Commerce] 管理員。

<u>要再現的步驟</u>：

1. 執行大量作業（例如，從產品格線大量更新產品屬性）。
1. 完成作業(例如，執行 `bin/magento queue:consumer:start product_action_attribute.update`)。
1. 重新整理 [!DNL Commerce] 管理頁面，展開管理通知區段，然後按一下 **[!UICONTROL Dismiss All Completed Tasks]** 連結。

<u>預期結果</u>：

此 _[!UICONTROL Something went wrong]_清除完成的任務時，不應顯示錯誤。

<u>實際結果</u>：

此 _[!UICONTROL Something went wrong]_顯示錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
