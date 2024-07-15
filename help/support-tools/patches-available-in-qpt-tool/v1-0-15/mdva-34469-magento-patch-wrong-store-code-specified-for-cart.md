---
title: 'MDVA-34469：為購物車指定的存放區代碼錯誤'
description: 「MDVA-34469修補程式解決使用者在切換商店檢視後將產品加入購物車時，收到錯誤訊息：*為購物車指定的商店代碼錯誤*的問題。」 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15時，即可使用此修補程式。 修補程式ID為MDVA-34469。 請注意，Adobe Commerce 2.4.2已修正此問題。'
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469：為購物車指定的存放區代碼錯誤

MDVA-34469修補程式解決使用者在切換商店檢視後將產品加入購物車時，收到錯誤訊息的問題： *為購物車*&#x200B;指定的商店代碼錯誤。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15時，即可使用此修補程式。 修補程式ID為MDVA-34469。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.4.1 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者在嘗試切換商店檢視時，看到購物車查詢錯誤，*「為購物車指定的商店代碼錯誤」*。

<u>必要條件</u>：

* Adobe Commerce 2.4.0。
* 設定了具有單一商店和兩個商店檢視的單一網站。
* 已建立客戶帳戶。

<u>要再現的步驟</u>：

1. Adobe Commerce後端設定為有兩個存放區檢視（使用存放區代碼：預設、秒）。
1. 使用者使用預設商店代碼建立購物車。
1. 使用者嘗試使用`Store`請求標頭中的第二個商店代碼來擷取此購物車。

<u>預期結果</u>：

顯示購物車是因為切換商店（在`Store`請求標題中傳送新代碼）會將購物車與請求的商店建立關聯。

<u>實際結果</u>：

購物車查詢傳回錯誤，且購物車未顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
