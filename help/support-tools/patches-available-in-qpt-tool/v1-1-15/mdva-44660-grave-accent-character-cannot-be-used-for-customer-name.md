---
title: 「MDVA-44660：重音符號字元[']不能用於客戶名稱」
description: MDVA-44660修補程式修正重音符號字元(')無法用於客戶名稱的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-44660。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 696f2690-2af5-4770-a4a8-c88c423c6c16
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-44660：重音符號字元(&amp;amp；grave；)無法用於客戶名稱

MDVA-44660修補程式修正重音符號字元[\&#39;]無法用於客戶名稱的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-44660。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

重音符號字元[\&#39;]不能用於客戶的名字和姓氏。

<u>要再現的步驟</u>：

使用Admin帳戶建立新客戶，或在店面註冊時使用名字或姓氏中的抑音字元，例如「L&#39;Epicerie」。

<u>預期結果</u>：

可以建立名稱中包含重音符號的新客戶。

<u>實際結果</u>：

*名字無效！*&#x200B;或&#x200B;*姓氏無效*&#x200B;錯誤已顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
