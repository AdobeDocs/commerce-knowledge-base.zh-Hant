---
title: 'ACSD-49392：部分退款後，訂單狀態變更為已關閉'
description: 套用ACSD-49392修補程式以修正Adobe Commerce問題，該問題導致捆綁產品的部分退款後，訂單狀態變更為已關閉。
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392：部分退款後，訂單狀態變更為已關閉

ACSD-49392修補程式修正套件產品部分退款後，訂單狀態變更為已關閉的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.31。 修補程式ID為ACSD-49392。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4和2.4.1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在套裝產品的部分退款後，訂單狀態會變更為已關閉。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce並建立任何隨附產品，或使用現有的隨附產品。
1. 以這個數量大於1的套件產品下訂單。
1. 前往管理員，然後從開啟在步驟2建立的訂單 **[!UICONTROL Sales]** > **[!UICONTROL Order]** 並建立發票。 觀察訂單狀態。 它將會在處理中。
1. 建立部分銷退折讓單（不要退款給捆綁銷售中的所有產品）。
1. 檢查訂單狀態。

<u>預期結果</u>

為套件產品建立部份銷退折讓單後，訂單狀態為處理中。

<u>實際結果</u>

為套件產品建立部份銷退折讓單之後，訂單狀態為完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
