---
title: 'ACSD-51230：已刪除禮卡帳戶'
description: 套用ACSD-51230修補程式，修正處理訂單中簡單產品的部分退款時，會刪除禮品卡帳戶的Adobe Commerce問題。
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230：已刪除禮品卡帳戶

ACSD-51230修補程式修正了處理訂單中簡單產品的部分退款時，禮品卡帳戶遭到刪除的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.32。 修補程式ID為ACSD-51230。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

處理訂單中簡單產品的部分退款時，會刪除禮品卡帳戶。

<u>要再現的步驟</u>：

1. 建立訂單，使用 *禮品卡* 和 *簡單產品* (例如， *新增：SKU：GI000XX000XXX，SKU：PC046CP042076*) - （任何付款和送貨方式均有效）。
1. 為訂單開立商業發票。
1. 前往 **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. 已建立禮品卡的帳戶。
1. 現在移至 **[!UICONTROL Order]**，並建立 **[!UICONTROL Credit Memo]**.
1. 變更的數量 *禮品卡* 設為0並加以更新。 這將會為以下專案建立部分退款： *簡單產品*.
1. 按一下 **[!UICONTROL Refund]**.
1. 現在重新整理 **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. 新建立的帳戶已刪除。

<u>預期結果</u>

禮品卡帳戶可供使用，因為未針對禮品卡建立退款。

<u>實際結果</u>

禮卡帳戶已刪除，且禮卡不會退款。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
