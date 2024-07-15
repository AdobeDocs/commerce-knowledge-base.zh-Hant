---
title: 「MDVA-34192修補程式：無法以特定格式修改客戶日期」
description: MDVA-34192修補程式修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192修補程式：無法以特定格式修改客戶日期

MDVA-34192修補程式修正無法使用dd/mm/yyyy格式修改/指定客戶出生日期的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.5-p1上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：** 2.3.4-2.3.6

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此修補程式可解決數個問題。 以下是其中一個專案的說明和重現步驟。

當我們使用自訂日期屬性進行篩選且管理員使用者地區設定為en\_GB時，產品格線篩選器無法正常運作。

<u>要再現的步驟：</u>：

1. 建立&#x200B;**介面地區設定**&#x200B;設定為&#x200B;*英文（英國）*&#x200B;的管理員使用者。
1. 使用下列設定建立日期屬性：
   * **存放區擁有者的目錄輸入型別**： *日期*
   * **用於篩選器選項**： *是*
   * **新增至資料行選項**： *是*
1. 將屬性指派給屬性集。
1. 前往產品編輯頁面，使用日期選擇器選取新屬性的日期並儲存。
1. 嘗試使用新的日期屬性來篩選產品格線。

<u>預期結果：</u>：

當管理員使用者地區設定為en\_GB時，產品篩選器可正確用於自訂日期屬性。

<u>實際結果：</u>：

當管理員使用者地區設定為en\_GB時，自訂日期屬性的產品篩選器無法正常運作。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
