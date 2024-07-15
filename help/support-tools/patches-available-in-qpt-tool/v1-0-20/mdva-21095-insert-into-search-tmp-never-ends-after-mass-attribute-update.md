---
title: 'MDVA-21095： INSERT INTO "search_tmp..."在大量屬性更新之後不會結束'
description: MDVA-21095修補程式修正了查詢「INSERT INTO」「search\_tmp...」在大量屬性更新後從未結束的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-21095。 請注意，目前沒有計畫在未來版本中修正此問題。
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095： INSERT INTO &quot;search_tmp...&quot;在大量屬性更新之後不會結束

MDVA-21095修補程式修正了查詢`INSERT INTO` &quot;search\_tmp...&quot;在大量屬性更新後從未結束的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-21095。 請注意，目前沒有計畫在未來版本中修正此問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`INSERT INTO` &quot;search\_tmp...&quot;在大量屬性更新之後永遠不會結束。

<u>要再現的步驟</u>：

執行含有~30,000個專案的整批屬性值更新。

<u>預期結果</u>：

重新索引程式會正常完成，如預期。

<u>實際結果</u>：

重新索引程式已完成，但許多查詢`INSERT INTO` &quot;search\_tmp...&quot;會啟動，直到伺服器達到`pm.max_children`引數值且PHP-fpm終止，而且即使MySQL重新啟動並處理程式終止後，這些查詢也會持續發生。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
