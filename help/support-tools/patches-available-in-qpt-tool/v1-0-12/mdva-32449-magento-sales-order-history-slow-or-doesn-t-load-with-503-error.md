---
title: 「MDVA-32449：銷售訂單歷史記錄緩慢或未載入，並出現503錯誤」
description: MDVA-32449修補程式可解決Adobe Commerce上銷售訂單歷史記錄載入緩慢或無法載入及顯示503錯誤的問題。 當13000+個客戶指派至B2B公司時，就會發生此問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12後，即可使用此修補程式。 請注意，此問題已在Adobe Commerce 2.4.1中修正。
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449：銷售訂單歷史記錄緩慢或未載入，並出現503錯誤

MDVA-32449修補程式可解決Adobe Commerce上銷售訂單歷史記錄載入緩慢或無法載入及顯示503錯誤的問題。 當13000+個客戶指派至B2B公司時，就會發生此問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12時，即可使用此修補程式。 請注意，此問題已在Adobe Commerce 2.4.1中修正。

## 受影響的產品和版本

當13000+個客戶指派至B2B公司時，就會發生此問題。

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.3.5-p2、2.4.0、2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正訂單歷史記錄載入速度非常緩慢或完全沒有載入的問題。

<u>必要條件</u>：

指派給B2B公司的13000+個客戶

<u>要再現的步驟</u>：

1. 以公司管理員身分登入店面。
1. 移至銷售訂單歷史記錄頁面。

<u>預期結果</u>：

銷售訂單歷史記錄頁面會正常載入。

<u>實際結果</u>：

頁面載入速度非常慢，或頁面無法載入且會顯示逾時錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
