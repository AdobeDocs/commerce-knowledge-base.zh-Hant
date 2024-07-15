---
title: 'MDVA-33976修補程式：移除選項後套件無庫存'
description: MDVA-33976修補程式修正在Admin中移除套件產品的其中一個選項後，套件產品顯示為無存貨的問題。 安裝[Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp)時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-33976修補程式：移除選項後套裝無庫存

MDVA-33976修補程式修正在Admin中移除套件產品的其中一個選項後，套件產品顯示為無存貨的問題。 安裝[Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp)時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.3上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0-2.3.6-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 在Commerce管理員中開啟套件組合產品。
1. 移除其中一個套件組合產品選項。
1. 儲存變更。
1. 在店面開啟產品。

<u>預期結果</u>：

組合產品庫存狀態會根據子產品庫存狀態更新。

<u>實際結果</u>：

無論子產品的狀態為何，組合產品都會顯示為「無庫存」。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
