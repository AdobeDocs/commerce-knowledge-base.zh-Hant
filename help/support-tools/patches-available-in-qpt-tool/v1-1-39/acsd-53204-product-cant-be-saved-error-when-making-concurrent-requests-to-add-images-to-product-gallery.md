---
title: 'ACSD-53204： *無法儲存產品*同時要求將影像新增到相簿時發生錯誤'
description: 套用ACSD-53204修補程式以修正Adobe Commerce問題，其中使用rest/V1/products/&lt；sku&gt；/media端點同時請求將影像新增至產品相簿時會擲回無法儲存產品錯誤。
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204： &quot;*無法儲存產品*「同時請求將影像新增至相簿時發生錯誤

ACSD-53204修補程式修正了「*無法儲存產品*&#x200B;同時要求使用將影像新增至產品相簿時擲回「錯誤」 `rest/V1/products/<sku>/media` 端點。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.39。 修補程式ID為ACSD-53204。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

&quot;*無法儲存產品*&#x200B;同時要求使用將影像新增至產品相簿時擲回「錯誤」 `rest/V1/products/<sku>/media` 端點。

<u>要再現的步驟</u>：

1. 登入「管理面板」。
1. 使用SKU p1建立產品。
1. 同時向發出多個請求 `rest/V1/products/<sku>/media` 端點可同時上傳多個影像。

<u>預期結果</u>：

影像儲存時不會發生錯誤。

<u>實際結果</u>：

&quot;*無法儲存產品*「錯誤會不時傳回。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
