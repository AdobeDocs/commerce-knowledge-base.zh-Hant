---
title: 'MDVA-25631：無法儲存並重新整理客戶區段'
description: MDVA-25631修補程式解決使用者無法儲存和重新整理包含大量客戶的客戶區段的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-25631。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 4250824b-e347-4ca4-8eaf-4de4d091bfc4
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# MDVA-25631：無法儲存和重新整理客戶區段

MDVA-25631修補程式解決使用者無法儲存和重新整理包含大量客戶的客戶區段的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-25631。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法儲存和重新整理包含大量客戶的客戶區段。

<u>必要條件</u>：

產生大量客戶（超過300萬）。

<u>要再現的步驟</u>：

1. 建立客戶區段並嘗試儲存。

<u>預期結果</u>：

已儲存客戶區段且未發生任何錯誤。

<u>實際結果</u>：

您收到&#x200B;*500*&#x200B;錯誤，因為已用盡允許的記憶體大小。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
