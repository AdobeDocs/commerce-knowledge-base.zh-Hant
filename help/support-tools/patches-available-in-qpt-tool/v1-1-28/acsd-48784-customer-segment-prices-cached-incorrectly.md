---
title: 「ACSD-48784：客戶群組之間的客戶區段價格快取不正確」
description: 套用ACSD-48784修補程式，修正客戶群組之間不正確快取客戶區段價格的Adobe Commerce問題。
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784：客戶群組之間的客戶區段價格快取不正確

ACSD-48784修補程式修正客戶群組之間不正確快取客戶區段價格的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-48784。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶群組之間的客戶區段價格快取不正確。

<u>必要條件</u>：

設定 [!DNL Varnish] 或 [!DNL Fastly].

<u>要再現的步驟</u>：

1. 在您的存放區中啟用完整頁面快取。
1. 以具有特殊客戶群組定價的使用者身分登入網站。
1. 移至具有特殊客戶群組定價之產品的產品頁面。 觀察 *特別價格*.
1. 在獨立的瀏覽器中，以訪客使用者身分開啟相同的產品頁面，而不需登入。 觀察正常價格。
1. 存取Adobe Commerce管理介面並清除Adobe Commerce和 [!DNL Fastly] 此存放區的快取。
1. 在登入的瀏覽器中，移除 `X-Magento-Vary` Cookie。
1. 在登入的瀏覽器中，重新載入相同的產品頁面多次，直到快取完全清除為止。
1. 在非登入瀏覽器中重新載入產品頁面，現在即可檢視客戶群組定價。

<u>預期結果</u>：

產品頁面會顯示特定客戶群組的正確價格。

<u>實際結果</u>：

* 訪客使用者可看見特別登入使用者價格。
* 迷你購物車會在產品加入後顯示正確的價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
