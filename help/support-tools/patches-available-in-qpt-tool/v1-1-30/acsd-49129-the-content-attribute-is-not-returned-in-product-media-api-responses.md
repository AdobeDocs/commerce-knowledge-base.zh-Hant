---
title: ACSD-49129：產品媒體API回應中未傳回「Content」屬性
description: 套用ACSD-49129修補程式以修正「rest/V1/products/sku/media」產品媒體API回應中未傳回*content*屬性（*base64影像代碼*）的Adobe Commerce問題。
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129：產品媒體API回應中未傳回「Content」屬性

ACSD-49129修補程式修正了`rest/V1/products/sku/media`產品媒體API回應中未傳回&#x200B;*content*&#x200B;屬性(*[!UICONTROL base64 image code]*)的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.30時，即可使用此修補程式。 修補程式ID為ACSD-49129。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`rest/V1/products/sku/media`產品媒體API回應中未傳回&#x200B;*內容*&#x200B;屬性(*[!UICONTROL base64 image code]*)。

<u>要再現的步驟</u>：

1. 使用影像建立產品。
1. 傳送&#x200B;*GETREST API*&#x200B;要求給`rest/V1/products/<sku>/media`和`rest/V1/products/<sku>/media/<entryId>`。
1. 檢查API回應。

<u>預期結果</u>

含有資料的&#x200B;*content*&#x200B;屬性可透過REST API使用。

<u>實際結果</u>

API回應中不存在&#x200B;*content*&#x200B;屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
