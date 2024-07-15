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

MDVA-33970修補程式可解決銷退折讓單中顯示美元($)符號而非當地貨幣的問題。 **網站**&#x200B;範圍用於&#x200B;**價格**&#x200B;屬性時，就會發生這種情況。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.4-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.4 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

在此範例中，會使用這些設定：

* 2網站存在 — 每個網站都有&#x200B;**商店**&#x200B;和&#x200B;**商店檢視**。
* **預設設定**&#x200B;使用新加坡元作為&#x200B;**貨幣** （**商店>設定>一般>貨幣設定**）：
   * **基本貨幣** = *新加坡元*
   * **預設顯示貨幣** = *新加坡元*
   * **允許的貨幣** = *新加坡元*
* **網站1**&#x200B;有&#x200B;**預設設定**。
* **網站2**&#x200B;使用馬來西亞林吉特做為&#x200B;**貨幣**：
   * **基本貨幣** = *馬來西亞令吉*
   * **預設顯示貨幣** = *馬來西亞令吉*
   * **允許的貨幣** = *馬來西亞令吉*
* 移至&#x200B;**商店>貨幣符號**，並設定：
   * **MYR （馬來西亞令吉）** = *RM*
   * **SGD （新加坡元）** = *SGD* （**使用標準** = *已核取*）
* 有些&#x200B;**產品**&#x200B;存在。

<u>要再現的步驟</u>：

1. 從&#x200B;**網站2**&#x200B;發出&#x200B;**訂單** （您可以將其設定為預設以避免其他設定）。
1. 登入&#x200B;**管理員**。
1. 開啟新建立的訂單。
1. 檢查&#x200B;**貨幣符號** = *RM*。
1. 建立&#x200B;**發票**。
1. 檢查發票中的&#x200B;**貨幣符號** = *RM*。
1. 建立&#x200B;**銷退折讓單**。
1. 檢查&#x200B;**銷退折讓單**&#x200B;中的&#x200B;**貨幣符號** ** ** = *RM*。
1. 開啟&#x200B;**訂單**&#x200B;中的&#x200B;**銷退折讓單**&#x200B;標籤。
1. 檢查格線中的&#x200B;**貨幣符號**。
1. 開啟&#x200B;**銷售>銷退折讓單**。
1. 檢查格線中的&#x200B;**貨幣符號**。

<u>預期結果</u>：

如預期使用正確的當地語系化貨幣符號。

<u>實際結果</u>：

即使未在「管理」設定中設定，系統仍會使用美元($)符號。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
