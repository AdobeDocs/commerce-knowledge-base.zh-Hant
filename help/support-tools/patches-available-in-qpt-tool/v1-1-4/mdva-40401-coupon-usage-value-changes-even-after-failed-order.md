---
title: 'MDVA-40401：訂單失敗後優惠券使用值變更'
description: MDVA-40401修補程式修正了即使在訂單失敗後優惠券使用量值也會變更的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40401。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401：訂單失敗後優惠券使用量值變更

MDVA-40401修補程式修正了即使在訂單失敗後優惠券使用量值也會變更的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40401。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者以失敗順序使用抵用券後，就無法重新套用抵用券。

<u>要再現的步驟</u>：

1. 使用自動產生的抵用券建立購物車規則。
1. 新增產品至購物車並套用優惠券。
1. 移至&#x200B;**簽出**。
1. 下訂單前，讓新增的產品「無庫存」。
1. 您應該會收到&#x200B;*缺貨*&#x200B;錯誤。
1. 執行cron。
1. 前往購物車並移除該產品。
1. 新增其他產品並套用優惠券。

<u>預期結果</u>：

由於未下前一筆訂單，因此應成功套用優惠券代碼。

<u>實際結果</u>：

您收到&#x200B;*優惠券代碼無效*&#x200B;錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
