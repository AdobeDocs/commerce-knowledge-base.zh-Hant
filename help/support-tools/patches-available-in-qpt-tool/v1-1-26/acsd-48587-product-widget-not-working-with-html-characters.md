---
title: 'ACSD-48587：產品Widget無法使用包含HTML字元的SKU'
description: 套用ACSD-48587修補程式，修正Adobe Commerce中在產品Widget比對規則中HTML特殊字元無法顯示相符產品的問題。
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587：產品Widget無法使用包含HTML字元的SKU

ACSD-48587修補程式修正產品Widget比對規則中HTML特殊字元無法顯示相符產品的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.26。 修補程式ID為ACSD-48587。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品Widget無法使用包含的SKU *&quot;&amp;&quot;* 符號。

<u>要再現的步驟</u>：

1. 建立產品包含 *&quot;&amp;&quot;* 在SKU中（例如s000&amp;01）。
1. 編輯CMS頁面的內容，在 *頁面產生器*.
1. 新增產品Widget。
1. 編輯Widget並設定 **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. 輸入包含的SKU *&quot;&amp;&quot;* 在產品SKU欄位中。
1. 儲存內容和CMS頁面。
1. 檢查 *CMS頁面* 的內容 *頁面產生器預覽* 和產品店面。

<u>預期結果</u>：

此產品具有 *&quot;&amp;&quot;* SKU中的頁面會顯示在「頁面產生器」預覽和店面上。

<u>實際結果</u>：

此產品具有 *&quot;&amp;&quot;* SKU中的頁面不會顯示在頁面產生器預覽中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
