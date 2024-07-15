---
title: 「MDVA-22026：無法從外部URL匯入產品影像」
description: MDVA-22026修補程式修正無法從外部URL匯入產品影像的問題。
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# mdva-22026：無法從外部URL匯入產品影像

MDVA-22026修補程式修正無法從外部URL匯入產品影像的問題。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-22026。 請注意，Adobe Commerce 2.3.4版已修正問題。

## 受影響的產品和版本

**在雲端基礎結構2.3.2-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.3.2-2.3.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 在Admin中，移至&#x200B;**系統** > **匯入**。
1. 設定&#x200B;**實體型別** = *產品*。
1. 設定&#x200B;**匯入行為** = *新增/更新*。
1. 設定&#x200B;**允許的錯誤計數** = *10000*。
1. 選取要匯入的檔案。
1. 按一下&#x200B;**檢查資料**&#x200B;按鈕（應該會驗證檔案）。
1. 按一下&#x200B;**匯入**&#x200B;按鈕。

<u>預期結果</u>：

如預期從CSV檔案成功匯入產品，包括來自外部URL的影像。

<u>實際結果</u>：

從CSV檔案匯入產品（包括來自外部URL的影像）失敗並收到類似錯誤：

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## 套用修補程式

若要套用個別的修補程式，請根據您的部署方法，使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html)。
* 雲端基礎結構上的Adobe Commerce： [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool檢查Adobe Commerce問題的修補程式](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
