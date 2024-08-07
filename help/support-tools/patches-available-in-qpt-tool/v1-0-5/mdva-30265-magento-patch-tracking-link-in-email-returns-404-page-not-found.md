---
title: 'MDVA-30265：電子郵件中的追蹤連結傳回404找不到頁面'
description: MDVA-30265修補程式可解決客戶在訂單確認電子郵件中點按出貨追蹤連結時，發生「404找不到頁面」錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265：電子郵件中的追蹤連結傳回404找不到頁面

MDVA-30265修補程式可解決客戶在訂單確認電子郵件中點按出貨追蹤連結時，發生「404找不到頁面」錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3至2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

為下訂單建立出貨後，會傳送電子郵件給客戶，其中包含追蹤資訊及追蹤訂單的連結。 但是，當客戶按一下電子郵件中的出貨追蹤連結時，這會傳回「404找不到頁面」錯誤。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce 2.4。如需相關步驟，請參閱我們的開發人員檔案中的[使用撰寫器安裝Adobe Commerce](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html)。
1. 下訂單。
1. 移至[管理]面板> **銷售** > **訂單**。 尋找您剛建立的訂單並開啟。
1. 建立出貨並新增追蹤編號（承運商=自訂值）。 如需相關步驟，請參閱使用手冊中的[Order Management >建立出貨](https://docs.magento.com/user-guide/sales/shipments-create.html)。
1. 您會收到電子郵件。 按一下追蹤連結以檢查其是否正常運作。
1. 建立發票。 如需相關步驟，請參閱使用手冊中的[Order Management >建立發票](https://docs.magento.com/user-guide/sales/invoice-create.html)。 再按一下上方追蹤連結上的。

<u>預期結果</u>：

即使是在建立商業發票之後，追蹤連結應該也會運作。

<u>實際結果</u>：

建立發票後，追蹤連結無法運作，並傳回「404找不到頁面」錯誤頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
