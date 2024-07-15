---
title: 'MDVA-33559修補程式：PayflowPro付款已拒絕錯誤'
description: MDVA-33559修補程式可解決PayPal PayflowPro付款遭拒絕的問題。
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559修補程式： PayflowPro付款已拒絕錯誤

MDVA-33559修補程式可解決PayPal PayflowPro付款遭拒絕的問題。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.5-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此問題與名稱中使用的&amp;符號及等號(=)特殊字元有關。

<u>要再現的步驟</u>：

1. 新增簡單產品至購物車。
1. 前往結帳。
1. 設定送貨地址。 (送貨地址範例： **名字** = ** *約翰的* ** **姓氏** = ** *蘋果和橘子， Inc* ** **街道地址** = *1234 E無名稱的St* **國家** = *美國* **州/省** = *安州* **城市{2 1} = *Anytown*** Zip **= *12345***&#x200B;電話&#x200B;**= *1234567890*)**
1. 將付款設定為&#x200B;**PayPal PayflowPro**，並嘗試完成結帳。

<u>預期結果</u>：

如預期，交易會導致付款成功或錯誤訊息。

<u>實際結果</u>：

交易遭到拒絕，客戶收到一封電子郵件，顯示「交易已被拒絕」。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
