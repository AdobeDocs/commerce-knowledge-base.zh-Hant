---
title: 'ACSD-48044：套用多張禮品卡可防止下訂單'
description: 套用ACSD-48044修補程式，修正Adobe Commerce的問題，亦即套用多張禮品卡至多筆運送的單一訂單時，無法下訂單。
exl-id: fe57063c-d69c-4b80-a59c-912c2603f6af
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044：套用多張禮品卡可防止下訂單

ACSD-48044修補程式修正了將多張禮品卡套用至一張有多重送貨的訂單時，無法下單的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.25。 修補程式ID為ACSD-48044。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將多張禮品卡套用至有多張出貨的單張訂單，可防止下訂單。

<u>要再現的步驟</u>：

1. 安裝全新版本的Adobe Commerce。
1. 建立價格為$100的簡單產品，以及價格為$10的另一個簡單產品。
1. 登入 [!UICONTROL Admin panel] 並建立兩張禮品卡。

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = $25

1. 建立具有兩個地址的客戶。
1. 新增兩個產品至購物車。

   * 先新增$10的產品，然後新增$100的產品。 如果先新增$100產品，則無法重現問題。

1. 前往購物車，然後新增您建立的兩個禮品卡。
1. 按一下 **[!UICONTROL Ship to Multiple Addresses]** 在購物車頁面上。
1. 將每個產品指派至不同的地址。
1. 前往 **[!UICONTROL Shipping information]** 頁面。
1. 前往 **[!UICONTROL Billing information]** 頁面。
1. 前往 **[!UICONTROL Review Your Order]** 頁面，您可在此檢視問題。
1. 嘗試下訂單。

<u>預期結果</u>：

* 禮品卡已正確套用至總金額。
* 已下訂單。

<u>實際結果</u>：

禮卡金額混有錯誤 *「請更正禮卡代碼。」* 下訂單時。

* 第一個產品：

   * 移除禮卡(00GXM6SUGBLW) - $15.00
   * 移除禮品卡(02KB8M0H0GRD) - $0.00

* 第二個產品：

   * 移除禮卡(00GXM6SUGBLW) - $25.00
   * 移除禮品卡(02KB8M0H0GRD) - $35.00

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
