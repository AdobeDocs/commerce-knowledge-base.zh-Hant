---
title: 'MDVA-29400：透過PayPal Express結帳所下的重複訂單'
description: MDVA-29400修補程式可解決客戶透過PayPal Express結帳下單時，建立重複訂單的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-29400。 請注意，問題已在Adobe Commerce 2.4.1中修正。
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400：透過PayPal Express結帳所下的重複訂單

MDVA-29400修補程式可解決客戶透過PayPal Express結帳下單時，建立重複訂單的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-29400。 請注意，問題已在Adobe Commerce 2.4.1中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.3.7-p1、2.4.0 - 2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者使用PayPal Express結帳下訂單時，會建立重複的訂單。

<u>必要條件</u>：

已啟用並設定PayPal Express簽出。

<u>要再現的步驟</u>：

1. 新增產品至購物車。
1. 移至「結帳」頁面，並使用PayPal Express作為付款方式。
1. 它會重新導向至paypal/express/review/頁面。
1. 下單。 您將會被重新導向到成功頁面。
1. 返回PayPal/express/review/頁面。
1. 按一下&#x200B;**下訂單**&#x200B;按鈕。

<u>預期結果</u>：

只會建立一個訂單。

<u>實際結果</u>：

您收到下列錯誤：*PayPal Express簽出Token不存在*，但已成功下第二張訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
