---
title: 'MDVA-36853：無法從大型媒體集載入影像'
description: MDVA-36853修補程式修正沒有載入影像的問題，因為當您有大型媒體目錄時，頁面產生器媒體集Widget不會載入。
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853：無法從大型媒體集載入影像

MDVA-36853修補程式修正沒有載入影像的問題，因為當您有大型媒體目錄時，頁面產生器媒體集Widget不會載入。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-36853。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.4.2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 設定&#x200B;**啟用舊媒體集** = *是*，位於&#x200B;**管理員>商店>設定>進階>系統>媒體集**。
1. 導覽至&#x200B;**內容>區塊**，然後建立新的CMS區塊或編輯現有的CMS區塊。
1. 按一下&#x200B;**使用Pagebuilder編輯**&#x200B;按鈕。
1. 新增媒體元素。
1. 按一下&#x200B;**從相簿選取**&#x200B;按鈕。

<u>預期結果</u>：

媒體集Widget和媒體集影像都會如預期載入。

<u>實際結果</u>：

當您有大型`pub/media/catalog/product/cache/`目錄時，媒體集Widget和媒體集影像都不會載入。

## 套用修補程式

若要套用個別修補程式，請根據您的Adobe Commerce產品使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
