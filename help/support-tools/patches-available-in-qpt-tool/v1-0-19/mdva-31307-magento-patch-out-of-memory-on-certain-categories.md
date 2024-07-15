---
title: 'MDVA-31307：某些類別的記憶體不足'
description: MDVA-31307修補程式修正「Magento\_Csp/模型/BlockCache」耗用大量記憶體並產生大量快取字串的問題，這會導致某些頁面因大量動態白名單指令碼和樣式而發生問題。 提供的修補程式會最佳化此程式。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-31307。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307：某些類別的記憶體不足

MDVA-31307修補程式修正了`Magento\_Csp/Model/BlockCache`耗用大量記憶體並產生大量快取字串的問題，這會導致某些頁面出現問題，其中有許多動態列入白名單的指令碼和樣式。 提供的修補程式會最佳化此程式。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19時，即可使用此修補程式。 修補程式ID為MDVA-31307。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**在雲端基礎結構2.4.0上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正由於快取區塊的動態CSP白名單發生問題，導致某些類別發生&#x200B;*記憶體不足*&#x200B;錯誤的問題。

<u>要再現的步驟：</u>

1. 產生小型設定檔夾具(`bin/magento setup:performance:generate-fixtures`)。
1. 在不同索引標籤中開啟所有類別頁面。

<u>實際結果：</u>

*[日期與時間] PHP嚴重錯誤：在未知的行0中，已耗用允許的記憶體大小1073741824位元組(嘗試配置90112位元組)
[日期和時間] PHP嚴重錯誤： /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php第31*&#x200B;行中允許的記憶體大小已耗盡1073741824個位元組(嘗試配置33554440個位元組)

<u>預期結果：</u>

所有頁面都已正確開啟。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
