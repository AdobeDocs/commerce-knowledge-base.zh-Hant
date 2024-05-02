---
title: 「ACSD-57337：具有存取限制的管理員使用者可以在*公司*格線中檢視所有公司」
description: 套用ACSD-57337修補程式以修正Adobe Commerce問題，其中具有特定網站存取限制的管理員使用者可檢視*公司*格線中所有網站的公司。
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337：具有存取限制的管理員使用者可以在 *公司* 格線

ACSD-57337修補程式修正具有特定網站存取限制的管理員使用者可檢視中所有網站的公司的問題。 *公司* 格線。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.48。 修補程式ID為ACSD-57337。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有特定網站存取限制的管理員使用者可以在 *公司* 格線。

<u>要再現的步驟</u>：

1. 建立其他網站、商店和商店評論。
1. 建立指派給不同網站的幾個公司。
1. 建立管理員使用者角色，並將角色範圍設定為已建立的網站。
1. 建立管理員，並將其指派給已建立的角色。
1. 使用新管理員登入。
1. 開啟 **[!UICONTROL Customers]** > **[!UICONTROL Companies]** 並觀察公司清單。

<u>預期結果</u>：

指派給其他網站的公司會顯示在 *公司* 格線。

<u>實際結果</u>：

所有公司皆會顯示在 *公司* 格線。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。