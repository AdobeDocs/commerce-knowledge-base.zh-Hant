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

# ACSD-47137：當`pub/media`資料夾很大時，提高影像庫載入速度

當`pub/media`資料夾非常大時，ACSD-47137修補程式可改善影像庫的載入速度。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-47137。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當`pub/media`資料夾非常大時，影像庫的載入速度會很慢。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]**&#x200B;至&#x200B;_否_。
1. 清除設定快取。
1. 登出並再次以管理員使用者身分登入。
1. 在管理員側邊欄上，前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;並選取根類別。
1. 展開&#x200B;**[!UICONTROL Content]**&#x200B;區段並按一下&#x200B;**[!UICONTROL Select from Gallery]**。

載入頁面時，Adobe Commerce傳送`media_gallery/directories/gettree`個要求以載入媒體資料夾樹狀結構。

<u>預期結果</u>：

`media_gallery/directories/gettree`要求應該只從必要的目錄載入內容，而不是從`pub/media/`資料夾循環整個路徑清單。

<u>實際結果</u>：

當`pub/media/`資料夾含有大量內容時，`media_gallery/directories/gettree`要求需要很長時間才能載入。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
