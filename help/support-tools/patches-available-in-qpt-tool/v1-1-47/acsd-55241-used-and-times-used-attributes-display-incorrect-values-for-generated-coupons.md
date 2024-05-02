---
title: 「ACSD-55241：**已使用**和**已使用次數**屬性針對產生的抵用券顯示不正確的值」
description: Adobe Commerce套用ACSD-55241修補程式，修正**使用**和**使用次數**屬性針對產生的抵用券顯示不正確值的問題
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241： **已使用** 和 **使用時間** 屬性針對產生的抵用券顯示不正確的值

ACSD-55241修補程式修正了 **已使用** 和 **使用時間** 屬性會顯示所產生抵用券的錯誤值。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.47。 修補程式ID為ACSD-55241。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**已使用** 和 **使用時間** 屬性會顯示所產生抵用券的錯誤值。

<u>要再現的步驟</u>：

1. 建立 **[!UICONTROL Cart Price Rules]** 從 **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** 並新增在下單時符合的任何條件(範例：小計大於 *5$*)

* 套用任何折扣。
* 選取 **[!UICONTROL Auto Coupon]**.
* 它將從產生一些優惠券代碼 **管理優惠券代碼**.
* 重新索引並清除快取。

1. 建立 **[!UICONTROL customer account]** 並登入前端。
1. 新增一個產品，其中包含超過 *2* 購物車數量並套用一張抵用券。
1. 按一下 **[!UICONTROL Check Out with Multiple Addresses]**.
1. 為每個數量選取個別的地址、下訂單，然後完成結帳程式。
1. 觀察管理員的訂單總計，並檢視套用的折扣。
1. 使用其他優惠券再次下訂單。
1. 執行 `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` 更新優惠券程式碼使用方式的命令。

<u>預期結果</u>：

正確的計數應顯示在 **使用時間** 和 **已使用** 欄與 **是** 值 **[!UICONTROL manage coupon]** 在 **[!UICONTROL cart price rule]** 在管理員中。

<u>實際結果</u>：

使用的抵用券代碼計數不會更新於 **使用時間** 格線中的欄位，以及 **已使用** 欄顯示 *否* 值（若您下單時含有多個送貨地址）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
