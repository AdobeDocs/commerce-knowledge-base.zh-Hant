---
title: 「ACSD-49389：準備好取件時，API就會傳送取件電子郵件」
description: 套用ACSD-49389修補程式以修正Adobe Commerce問題，亦即訂單無法收取時，API會傳送已準備好收取的電子郵件。
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389：準備好接收由API傳送的電子郵件，但還沒有準備好接收時

ACSD-49389修補程式修正了訂單無法收取時，API會傳送準備收取電子郵件的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49389。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [QPT登陸頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當訂單未準備好取貨時，API會傳送準備取貨的電子郵件。

<u>要再現的步驟</u>：

1. 啟用 *[!UICONTROL In-Store Delivery]* 方法。
1. 建立已啟用取貨地點的庫存來源。
1. 使用主要網站及上述建立的來源建立新庫存。
1. 建立指派相同來源的產品。
1. 設定庫存數量= 1。
1. 使用檢視在步驟4中建立的產品 *[!UICONTROL In-Store Delivery]* 方法。
1. 建立訂單的商業發票。
1. 將產品的數量設為 *0* 並且沒有庫存。
1. 發佈下列API請求：

```
{
    "orderIds": [
        1
    ]
}
```

<u>預期結果</u>：

未傳送準備取車電子郵件。

<u>實際結果</u>：

API傳回 *訂單未準備好取貨*，但已準備好收取電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
