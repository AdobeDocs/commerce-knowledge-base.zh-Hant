---
title: 'MDVA-29148：儲存時ArrayBackend未指派預設值'
description: MDVA-29148修補程式解決了「\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend」在儲存時未指派預設值的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148：儲存時ArrayBackend未指派預設值

MDVA-29148修補程式可解決 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 不會在儲存時指派預設值。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.3-p1。

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） >=2.3.0 &lt;2.4.2。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過匯入指令碼或REST API建立產品時，使用 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 沒有為具有預設值的後端模型和指定預設值。

<u>要再現的步驟</u>：

1. 建立新的全域屬性，使用 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` 後端模型和非空白的預設值。
1. 使用REST API建立新產品。
1. 從REST API擷取該新產品，並確認產品的自訂屬性中未出現該屬性。

<u>預期結果</u>：

自訂屬性預設值已儲存至產品屬性。

<u>實際結果</u>：

自訂屬性預設值未儲存至產品屬性。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
