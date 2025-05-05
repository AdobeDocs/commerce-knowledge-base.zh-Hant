---
title: MDVA-40101：下單後商品仍為迷你購物車PayPal Express結帳
description: MDVA-40101修補程式修正使用PayPal Express結帳成功下單後，無法從迷你購物車移除專案的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40101。 請注意，問題已在Adobe Commerce 2.4.0中修正。
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101：下單後商品仍為迷你購物車PayPal Express結帳

MDVA-40101修補程式修正使用PayPal Express結帳成功下單後，無法從迷你購物車移除專案的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40101。 請注意，問題已在Adobe Commerce 2.4.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.3.7

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使使用PayPal Express結帳成功下訂單，商品仍會保留在迷你購物車中。

<u>要再現的步驟</u>：

在瀏覽器中，以無痕模式使用PayPal Express Checkout下訂單。

<u>預期結果</u>：

成功完成訂單後，迷你購物車應該空白。

<u>實際結果</u>：

* 成功頁面會顯示一個空白的迷你購物車。
* 所有其他頁面會顯示包含已購買專案的迷你購物車。
* 按一下購物車連結會將您重新導向至空的購物車頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修補程式區段。
