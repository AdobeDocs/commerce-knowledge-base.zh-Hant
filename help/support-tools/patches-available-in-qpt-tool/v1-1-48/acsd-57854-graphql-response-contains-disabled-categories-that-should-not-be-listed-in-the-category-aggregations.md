---
title: 「ACSD-57854： *GraphQL*回應包含停用的類別，這些類別不應列在類別彙總中」
description: 套用ACSD-57854修補程式以修正Adobe Commerce問題，其中的*GraphQL*回應包含不應列在類別彙總中的停用類別。
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854： *GraphQL* 回應包含停用的類別，這些類別不應列在類別彙總中

ACSD-57854修補程式修正了 *GraphQL* 回應包含停用的類別，這些類別不應列在類別彙總中。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.48。 修補程式ID為ACSD-57854。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

*GraphQL* 回應包含停用的類別，這些類別不應列在類別彙總中。

<u>要再現的步驟</u>：

1. 建立兩個類別。
1. 建立產品(測試Adobe產品)並將產品指派給這兩個類別。
1. 停用已建立的其中一個類別。
1. 使用產品 *GraphQL* 以搜尋產品。
1. 檢查產品類別清單 *GraphQL* 回應。

<u>預期結果</u>：

停用的類別不會列在 *GraphQL* 回應。

<u>實際結果</u>：

停用的類別會列在類別彙總中 *GraphQL* 回應。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
