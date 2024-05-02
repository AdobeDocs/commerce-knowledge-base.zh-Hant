---
title: 'ACSD-51431：索引子狀態為*[!UICONTROL Working]*即使變更記錄檔中沒有專案'
description: 套用ACSD-51431修補程式以修正索引器狀態為*的Adobe Commerce問題[!UICONTROL Working]*即使變更記錄檔中沒有專案。
feature: Logs, Price Indexer
role: Admin
exl-id: 85977b78-7f6b-47c7-b33e-16668bdf98fe
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-51431：索引器狀態為 *[!UICONTROL Working]* 即使變更記錄檔中沒有專案

ACSD-51431修補程式修正了索引器狀態為「 」的效能問題 *[!UICONTROL Working]* 即使變更記錄檔中沒有專案。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.33。 修補程式ID為ACSD-51431。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

索引子狀態為 *[!UICONTROL Working]* 即使變更記錄檔中沒有專案。

<u>要再現的步驟</u>：

1. 設定 **[!UICONTROL indexers]** 至 [!UICONTROL Update on Schedule].
1. 設定cron工作每分鐘執行一次。
1. 同時儲存對不同產品的變更。
1. 執行 `bin/magento indexer:status` 幾分鐘內。

<u>預期結果</u>：

會處理變更，且索引子位於 *[!UICONTROL Ready]* 狀態。 此 *[!UICONTROL Schedule]* 狀態為 *[!UICONTROL idle (0 in the backlog)]*.

<u>實際結果</u>：

會處理變更，且索引子位於 *[!UICONTROL Ready]* 狀態。 然而， *[!UICONTROL Schedule]* 狀態顯示 *[!UICONTROL working (0 in the backlog)]*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
