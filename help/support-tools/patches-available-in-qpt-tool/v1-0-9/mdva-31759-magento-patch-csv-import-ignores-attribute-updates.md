---
title: 「MDVA-31759修補程式：CSV匯入會忽略屬性更新」
description: MDVA-31759修補程式修正CSV匯入作業會忽略其他具有*Dropdown*和*Text Area*型別的屬性問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759修補程式： CSV匯入會忽略屬性更新

MDVA-31759修補程式修正CSV匯入會忽略具有&#x200B;*下拉式清單*&#x200B;和&#x200B;*文字區域*&#x200B;型別之其他屬性的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

CSV匯入會忽略其他具有&#x200B;*下拉式清單*&#x200B;和&#x200B;*文字區域*&#x200B;型別的屬性。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 使用下列設定建立產品屬性：
   * **預設標籤**： *G003*
   * **存放區擁有者的目錄輸入型別**： *文字區域*&#x200B;或&#x200B;*下拉式清單*
   * **屬性代碼**： *G003*
   * **領域**： *全域*
1. 將以上屬性新增至預設屬性集。
1. 建立具有預設屬性集的產品，並指定新屬性的值。
1. 將產品匯出為CSV。
1. 更新&#x200B;**additional\_attributes**&#x200B;欄中的屬性值。
1. 匯入更新的CSV。

<u>預期結果</u>：

G003屬性值會更新。

<u>實際結果</u>：

G003屬性值未更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
