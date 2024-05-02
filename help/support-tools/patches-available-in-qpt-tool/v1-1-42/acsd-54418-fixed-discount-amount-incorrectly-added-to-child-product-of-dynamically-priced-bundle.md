---
title: 'ACSD-54418：固定折扣金額錯誤地新增到動態定價套件的子產品中'
description: 套用ACSD-54418修補程式，修正動態定價套裝的每個子產品不正確套用固定折扣金額的Adobe Commerce問題。
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418：動態定價套裝的子產品不正確地新增了固定折扣金額。

ACSD-54418修補程式修正動態定價套件組合的每個子產品不正確套用固定折扣金額的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.42。 修補程式ID為ACSD-54418。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

固定折扣金額錯誤地套用至動態定價套件的每個子產品。

<u>要再現的步驟</u>：

1. 建立 **[!UICONTROL bundle product]** 搭配動態定價與 *2* 套件組合選項。
1. 建立 **[!UICONTROL cart price rule]** 特定優惠券代碼，僅適用於捆綁產品 **[!UICONTROL SKU]** 且具有固定折扣。
1. 將隨附產品新增到購物車。
1. 套用 **[!UICONTROL coupon code]**.
1. 檢查套用至購物車的折扣。

<u>預期結果</u>：

此折扣只會套用至整個套裝產品一次。

<u>實際結果</u>：

折扣會套用至每個套件組合子產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
