---
title: '''ACSD-49877：視訊自動播放不適用於行動裝置 [!DNL Safari]『'
description: 套用ACSD-49877修補程式，修正Adobe Commerce視訊自動播放選項在行動裝置上無法運作的問題 [!DNL Safari] 直接連結至遠端視訊檔案時。
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877：視訊自動播放在行動裝置上無法運作 [!DNL Safari]

ACSD-49877修正行動裝置上的自動播放選項的問題 [!DNL Safari] 當視訊直接連結到遠端視訊檔案時，無法運作。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.30。 修補程式ID為ACSD-49877。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 [！magento/quality-patches] 封裝至最新版本，並在[[!DNL Quality Patches Tool]：搜尋修補程式]。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

視訊自動播放不適用於行動裝置 [!DNL Safari] 直接連結至遠端視訊檔案，而非串流服務時。

<u>必要條件</u>：
[!DNL Page Builder] 模組已安裝。

<u>要再現的步驟</u>：

1. 建立新的CMS頁面，並編輯 **[!UICONTROL Content Value]** 替換為 [!DNL Page Builder].
1. 新增 *標籤* 元素到內容中，並新增 *視訊元素* 內部 *標籤*.
1. 現在按一下齒輪按鈕以編輯 *視訊元素*.
1. 將mp4視訊檔案的連結新增至 [!UICONTROL Video URL] 欄位。
1. 標籤 **[!UICONTROL Autoplay]** 欄位為 *是*.
1. 按一下 **[!UICONTROL Save]**.
1. 開啟最近建立的頁面 [!DNL Safari] 使用iPhone。

<u>預期結果</u>

自動播放選項適用於 [!DNL Safari] 使用iPhone。

<u>實際結果</u>

自動播放選項無法運作 [!DNL Safari] 使用iPhone。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
