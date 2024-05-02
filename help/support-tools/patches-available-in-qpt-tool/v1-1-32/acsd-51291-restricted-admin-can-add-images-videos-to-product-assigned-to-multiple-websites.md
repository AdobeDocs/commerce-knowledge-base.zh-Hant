---
title: 「ACSD-51291：受限制的管理員可將影像/影片新增至指派給多個網站的產品」
description: 套用ACSD-51291修補程式以修正Adobe Commerce問題，其中存取一個網站的受限管理員可將影像/影片新增至指派給多個網站的產品。
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291：受限制的管理員可將影像/影片新增至指派給多個網站的產品

ACSD-51291修補程式修正了具有單一網站存取權的受限管理員可將影像/影片新增至指派給多個網站的產品的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.32。 修補程式ID為ACSD-51291。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p3、2.4.5 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

擁有單一網站存取權的受限管理員可將影像/影片新增至指派給多個網站的產品。

<u>要再現的步驟</u>

1. 以管理員身分登入。
1. 建立第二個網站、商店和商店檢視。
1. 使用僅供第二個網站、商店和商店檢視使用的資源，建立第二個管理員角色。
1. 建立第二個管理員，並將其指派給新的受限制管理員角色。
1. 建立新產品，並將其指派給預設網站和新網站。
1. 從主要管理員設定檔登出。
1. 以新的受限制管理員身分登入。
1. 編輯已指派給兩個網站的已建立產品。
1. 開啟 **[!UICONTROL Images and Videos]** 標籤。

<u>預期結果</u>：

* 系統會顯示下列訊息：

  *受限管理員僅可在管理員擁有指派產品的所有網站的許可權時，才能對影像或影片執行動作。*

* 此 **[!UICONTROL Add Video]** 按鈕未啟用。

<u>實際結果</u>：

受限管理員可以新增影像和影片，即使產品已指派給無法存取的網站。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
