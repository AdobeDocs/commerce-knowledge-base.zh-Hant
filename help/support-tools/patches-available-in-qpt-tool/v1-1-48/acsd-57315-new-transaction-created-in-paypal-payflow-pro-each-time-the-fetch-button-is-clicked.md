---
title: 'ACSD-57315：新交易建立於 [!DNL PayPal Payflow Pro] 每次按一下擷取按鈕時'
description: 套用ACSD-57315修補程式，以修正在中建立新交易的Adobe Commerce問題。 [!DNL PayPal Payflow Pro] 每次在的檢視交易畫面按一下擷取按鈕時 [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315：新交易建立於 [!DNL PayPal Payflow Pro] 每次按一下擷取按鈕時

ACSD-57315修補程式修正了在中建立新交易的問題。 [!DNL PayPal Payflow Pro] 每次在的檢視交易畫面按一下擷取按鈕時 [!UICONTROL Admin]. 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.48。 修補程式ID為ACSD-57315。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

新交易建立於 [!DNL PayPal Payflow Pro] 每次在的檢視交易畫面按一下擷取按鈕時 [!UICONTROL Admin].

<u>要再現的步驟</u>：

1. 設定 [!DNL PayPal Payflow Pro].
1. 將交易方法設為 *[!UICONTROL Sale]*.
1. 下訂單，使用 *信用卡*.
1. 開啟交易來源 [!UICONTROL Admin].
1. 按一下 **[!UICONTROL Fetch]** 按鈕。
1. 檢查 [!DNL PayPal] 與下單相關的交易科目。

<u>預期結果</u>：

未建立新的付款交易。

<u>實際結果</u>：

已針對已付款的訂單建立新的付款交易。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
