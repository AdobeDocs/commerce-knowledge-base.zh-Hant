---
title: ACSD-57003：訂單狀態變更為*Complete*而非*Processing*
description: 套用ACSD-57003修補程式以修正訂單狀態變更為*Complete*而非變更為*Processing*的Adobe Commerce問題。
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003：訂單狀態變更為&#x200B;*完成*，而非變更為&#x200B;*處理*

ACSD-57003修補程式修正了訂單狀態變更為&#x200B;*完成*&#x200B;而非變更為&#x200B;*處理*&#x200B;的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.46時，即可使用此修補程式。 修補程式ID為ACSD-57003。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂單部份退款且部份出貨時，訂單狀態變更為&#x200B;*完成*，而非變更為&#x200B;*處理*。

<u>要再現的步驟</u>：

1. 使用兩個可設定的產品建立訂單。
1. 為所有專案開立商業發票。
1. 只出貨第一個料號。
1. 只退款/建立出貨料號（*第一個料號*）的銷退折讓單。
1. 檢查訂單狀態。

<u>預期結果</u>：

訂單狀態應該是&#x200B;_處理_&#x200B;狀態。

<u>實際結果</u>：

建立部份出貨專案的銷退折讓單後，訂單狀態變更為&#x200B;*完成*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
