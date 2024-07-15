---
title: 'MDVA-32694修補程式：將產品新增至報價的問題'
description: MDVA-32694修補程式可解決無法在管理員中將有效產品新增至非預設網站上所建立可協商報價的問題。
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694修補程式：將產品新增至報價的問題

MDVA-32694修補程式可解決無法在管理員中將有效產品新增至非預設網站上所建立可協商報價的問題。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構2.3.2上的Adobe Commerce搭配B2B 1.2版

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.3.5-p2、2.4.0、2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

使用B2B安裝全新的Adobe Commerce執行個體。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店>設定>一般> B2B功能**&#x200B;並啟用&#x200B;**公司**&#x200B;和&#x200B;**B2B報價**。
1. 使用&#x200B;**商店**&#x200B;和&#x200B;**商店評論**&#x200B;再建立2個網站（您總共應該有3個網站： *基本*、*網站2*、*網站3*）。
1. 建立簡單產品並僅將其指派給&#x200B;*網站3*。
1. 移至&#x200B;**商店>所有商店**，並將&#x200B;*網站3*&#x200B;設定為&#x200B;**預設值**。
1. 移至前端，並在&#x200B;*網站3*&#x200B;上建立新公司。
1. 將先前建立的產品加入購物車，並建立新的可協商的報價。
1. 移至&#x200B;**商店>所有商店**，並將「*基底*」網站設回&#x200B;**預設值**。
1. 移至&#x200B;**SALES > Quotes > Open建立較早的報價單**，並嘗試加入相同的產品。

<u>預期結果</u>：

管理員使用者可以如預期將相同的產品新增至報價單。

<u>實際結果</u>：

Admin使用者無法將相同的產品加入報價中，此錯誤訊息隨即出現：

```php
This product is assigned to another website.
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
