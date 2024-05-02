---
title: 「ACSD-49737：信用卡付款失敗後，優惠券錯誤地標籤為已使用」
description: 套用ACSD-49737修補程式，以修正Adobe Commerce在支付信用卡失敗後，優惠券錯誤地標示為使用的問題。
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737：優惠券錯誤標示為 *已使用* 在信用卡付款失敗之後

ACSD-49737修補程式修正了抵用券錯誤標示為的問題 *已使用* 在信用卡付款失敗之後。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.30。 修補程式ID為ACSD-49737。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

優惠券錯誤地標籤為 *已使用* 在信用卡付款失敗之後。

<u>必要條件</u>：

1. 設定 **[!UICONTROL Braintree sandbox payment]** 方法。
1. 確定 [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) 取用者已設定並執行。

<u>要再現的步驟</u>：

1. 建立 **[!UICONTROL Cart Price Rule]** ，並使用自動產生的抵用券代碼。
1. 以客戶身分登入。
1. 將產品新增至購物車。
1. 套用自動產生的抵用券代碼。
1. 嘗試以失敗的付款下訂單。
1. 檢查中的優惠券使用方式 **[!UICONTROL Cart Price Rule]** 在 **[!UICONTROL Manage Coupon Codes]** 標籤。

<u>預期結果</u>：

抵用券不應標示為 *已使用* 如果付款失敗。

<u>實際結果</u>：

* 優惠券代碼顯示 — 已使用： *是*，使用時間： *1*
* 優惠券代碼僅供一次性使用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 安裝修補程式後所需的其他步驟

（本節為選用；套用修補程式修正問題後，可能需要執行一些步驟。） 

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
