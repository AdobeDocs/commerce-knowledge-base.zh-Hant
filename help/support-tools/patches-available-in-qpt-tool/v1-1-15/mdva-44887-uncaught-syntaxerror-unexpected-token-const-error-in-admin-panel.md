---
title: 「MDVA-44887：管理面板中出現「Uncaught SyntaxError： Unexpected token const」錯誤」
description: 「MDVA-44887修補程式修正管理員使用者無法點按任何功能表選項的問題。 「管理」面板中會顯示*Uncaught SyntaxError： Unexpected token const*錯誤。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-44887。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。」
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887：「管理」面板中出現「未攔截到的SyntaxError：未預期的權杖常數」錯誤

MDVA-44887修補程式修正管理員使用者無法點按任何功能表選項的問題。 此 *未攔截到的SyntaxError：未預期的語彙基元常數* 錯誤會顯示在「管理員」面板中。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.15。 修補程式ID為MDVA-44887。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者無法按一下任何功能表選項。 此 *未攔截到的SyntaxError：未預期的語彙基元常數* 錯誤會顯示在「管理員」面板中。

<u>要再現的步驟</u>：

1. 啟用JS套件組合。
1. 簡化JS檔案。
1. 登入Commerce管理面板。

<u>預期結果</u>：

管理員使用者無法按一下任何功能表選項。 瀏覽器主控台發生錯誤： *未攔截到的SyntaxError：未預期的語彙基元常數*.

<u>實際結果</u>：

管理員使用者可存取管理員面板。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
