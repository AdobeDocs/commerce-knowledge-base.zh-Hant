---
title: 'MDVA-29787：未顯示相關產品'
description: MDVA-29787修補程式可解決Adobe Commerce商店前端未顯示**相關產品**的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6後，即可使用此修補程式。 修補程式ID為MDVA-29787。
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787：未顯示相關產品

MDVA-29787修補程式解決了Adobe Commerce商店前端未顯示&#x200B;**相關產品**&#x200B;的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6時，即可使用此修補程式。 修補程式ID為MDVA-29787。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.3。

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.0。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當「*」是*&#x200B;之一，且在Commerce管理員中將&#x200B;**產品用於顯示**&#x200B;時，**相關產品**&#x200B;的目標規則無法運作。

>[!NOTE]
>
>注意：此修正程式不會修正現有的目標規則。 您必須重新建立現有的目標規則。

<u>要再現的步驟</u>：

1. 建立&#x200B;**新屬性** （範例： Test\_Attr）。
   * 設定存放區擁有者的&#x200B;**目錄輸入型別** = *文字。*
   * 在&#x200B;**店面屬性**&#x200B;中，設定&#x200B;**促銷規則條件** = *是*。
1. 建立&#x200B;**新屬性集** （範例： Test\_Set）。
1. 將&#x200B;**新屬性**&#x200B;新增至&#x200B;**新屬性集** （範例：將「Test\_Attr」屬性新增至「Test\_Set」屬性集）。
1. 建立三個產品。 例如，其設定如下：
   * 產品1，Test\_Attr = MAGT2NA\_Test3
   * 產品2，Test\_Attr = 24-MB02
   * 產品3，Test\_Attr = 701644329389M
1. 建立目標&#x200B;**規則** (**行銷**   > **相關產品規則**，然後按一下&#x200B;**新增規則**&#x200B;按鈕。) 包含設定：
   * **套用至** = *相關產品*
   * **產品符合**
   * 將您在&#x200B;****&#x200B;步驟1中建立的新屬性&#x200B;**設定為Product1的屬性（範例： Test\_Attr = MAGT2NA\_Test3）。**
   * **要顯示的產品** =其他兩個產品的屬性(例如：24-MB02和701644329389M屬性)。
1. 儲存&#x200B;**規則**。
1. 視需要執行重新索引。
1. 清除快取。
1. 在前端開啟Product1。

<u>預期結果</u>：

出現相關產品。

<u>實際結果</u>：

缺少相關產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
