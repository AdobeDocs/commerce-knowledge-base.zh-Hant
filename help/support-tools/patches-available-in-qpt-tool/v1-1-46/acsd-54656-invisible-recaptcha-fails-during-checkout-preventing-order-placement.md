---
title: 隱形 [!DNL reCAPTCHA] 結帳時失敗，無法下訂單
description: 套用ACSD-54656修補程式來修正隱藏的Adobe Commerce問題 [!DNL reCAPTCHA] 結帳期間無法正常運作，導致訂單無法下達。
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656：隱藏 [!DNL reCAPTCHA] 結帳期間無法正常運作，導致訂單無法下達。

ACSD-54656修補程式修正隱藏專案的問題 [!DNL reCAPTCHA] 結帳期間無法正常運作，導致訂單無法下達。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.46。 修補程式ID為ACSD-54656。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

隱形 [!DNL reCAPTCHA] 結帳期間無法正常運作，導致訂單無法下達。

<u>要再現的步驟</u>：

1. 啟用任何型別 [!DNL reCAPTCHA] 上的禮品卡 [!UICONTROL Checkout] 頁面。
1. 新增產品至購物車並前往 **[!UICONTROL Checkout]** 頁面。
1. 展開禮卡表單，並填寫有效的禮卡優惠券。
1. 按一下 **[!UICONTROL See balance and apply]** 按鈕。

<u>預期結果</u>：

已成功套用禮品卡。

<u>實際結果</u>：

錯誤訊息顯示： *[!DNL reCAPTCHA]驗證失敗，請重試*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
