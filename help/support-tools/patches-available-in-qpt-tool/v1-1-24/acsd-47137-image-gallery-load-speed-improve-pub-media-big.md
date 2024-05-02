---
title: '''ACSD-47137：改善影像集載入速度''pub/media''資料夾太大'''
description: 當「pub/media」資料夾非常大時，套用ACSD-47137修補程式可改善影像庫的載入速度。
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137：改善影像中心載入速度，當 `pub/media` 資料夾大

ACSD-47137修補程式可改善影像庫的載入速度， `pub/media` 資料夾非常大。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.24。 修補程式ID為ACSD-47137。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

影像庫的載入速度很慢，當 `pub/media` 資料夾非常大。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce管理員> **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** 至 _否_.
1. 清除設定快取。
1. 登出並再次以管理員使用者身分登入。
1. 在管理員側邊欄上，前往 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** 並選取根類別。
1. 展開 **[!UICONTROL Content]** 區段並按一下 **[!UICONTROL Select from Gallery]**.

載入頁面時，Adobe Commerce會傳送 `media_gallery/directories/gettree` 要求載入媒體資料夾樹狀結構。

<u>預期結果</u>：

此 `media_gallery/directories/gettree` 請求應僅從必要的目錄載入內容，而不是從以下目錄循環整個路徑清單 `pub/media/` 資料夾。

<u>實際結果</u>：

此 `media_gallery/directories/gettree` 請求需要很長時間載入，當 `pub/media/` 資料夾中有許多內容。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
