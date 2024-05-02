---
title: 'ACSD-48634： [!DNL JS] 發生以下情況時發生 [!DNL Google Analytics Content Experiments] 已啟用'
description: 套用ACSD-48634修補程式以修正 [!DNL JS] 上的錯誤 [!DNL staging] 更新頁面時間 [!DNL Google Analytics Content Experiments] 已啟用。
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634： [!DNL JS] 發生以下情況時發生 [!DNL Google Analytics Content Experiments] 已啟用

ACSD-48634修補程式修正 [!DNL JS] 上的錯誤 [!DNL staging] 更新頁面時間 [!DNL Google Analytics Content Experiments] 已啟用。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.27。 修補程式ID為ACSD-48634。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL JS] 錯誤發生於 [!DNL staging] 更新頁面時間 [!DNL Google Analytics Content Experiments] 已啟用。

<u>要再現的步驟</u>：

1. 在 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**，建立其他網站、商店和 **[!UICONTROL Store View]**. 確定 **[!UICONTROL Store View]** 是 *[!UICONTROL Enabled]*.
1. 設定 **[!DNL Configure Google Analytics]** 前往 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**：
   * 的 **[!DNL Main]** 和其他網站 [!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**： *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* 用於其他欄位，但請勿變更它們。
   * 的 **[!DNL Default Config]** [!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**： *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
1. 停用 **[!DNL Configure Google Analytics]** 於 **[!DNL Default Config]** [!DNL scope] 透過變更 **[!UICONTROL Enable]** 從 *[!UICONTROL Yes]* 至 *[!UICONTROL No]*. 請勿變更其他任何專案！
1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. 建立及編輯任何 **[!UICONTROL category]** 並為其新增排程更新：
   * 任何名稱、未來的開始日期、未來的結束日期，以及中的任何變更 **[!UICONTROL category]** ([!UICONTROL For Example]： *[!UICONTROL disable category]*)。
1. 儲存更新並檢查 [!DNL browser developer console] 錯誤。

<u>預期結果</u>：

否 [!DNL JS] 錯誤和變更 [!DNL staging] 更新已成功儲存。

<u>實際結果</u>：

[!DNL JS] 主控台中顯示錯誤，表單格式錯誤，以及 [!DNL spinner] 儲存後永遠不會停用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
