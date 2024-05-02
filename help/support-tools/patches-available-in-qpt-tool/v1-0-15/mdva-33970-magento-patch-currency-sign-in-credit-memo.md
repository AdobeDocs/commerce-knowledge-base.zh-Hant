---
title: 'MDVA-33970修補程式：銷退折讓單中的貨幣登入'
description: MDVA-33970修補程式可解決銷退折讓單中顯示美元($)符號而非當地貨幣的問題。 當**Website**範圍用於**Price**屬性時，就會發生這種情況。
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970修補程式：銷退折讓單中的貨幣登入

MDVA-33970修補程式可解決銷退折讓單中顯示美元($)符號而非當地貨幣的問題。 這種情況發生於 **網站** 範圍用於 **價格** 屬性。

此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.15。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.4 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

在此範例中，會使用這些設定：

* 2個網站存在 — 每個都有 **儲存** 和 **存放區檢視**.
* 此 **預設設定** 新加坡元為 **貨幣** (**儲存>組態>一般>貨幣設定**)：
   * **基本貨幣** = *新加坡元*
   * **預設顯示貨幣** = *新加坡元*
   * **允許的貨幣** = *新加坡元*
* **網站1** 具有 **預設設定**.
* **網站2** 有馬來西亞林吉特 **貨幣**：
   * **基本貨幣** = *馬來西亞林吉特*
   * **預設顯示貨幣** = *馬來西亞林吉特*
   * **允許的貨幣** = *馬來西亞林吉特*
* 前往 **儲存>貨幣符號**，並設定：
   * **馬來西亞林吉特（馬來西亞林吉特）** = *RM*
   * **新加坡元（新加坡元）** = *SGD* (**使用標準** = *已核取*)
* 部分 **產品** 「 」已存在。

<u>要再現的步驟</u>：

1. 建立 **訂購** 從 **網站2** （您可以將其設定為預設以避免其他設定）。
1. 登入 **管理員**.
1. 開啟新建立的訂單。
1. 檢查 **貨幣符號** = *RM*.
1. 建立 **發票**.
1. 檢查 **貨幣符號** = *RM* 在商業發票中。
1. 建立 **銷退折讓單**.
1. 檢查 **貨幣符號**  ** ** = *RM* 在 **銷退折讓單**.
1. 開啟 **銷退折讓單** 定位於 **訂購**.
1. 檢查 **貨幣符號** 在格線中。
1. 開啟 **銷售>銷退折讓單**.
1. 檢查 **貨幣符號** 在格線中。

<u>預期結果</u>：

如預期使用正確的當地語系化貨幣符號。

<u>實際結果</u>：

即使未在「管理」設定中設定，系統仍會使用美元($)符號。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
