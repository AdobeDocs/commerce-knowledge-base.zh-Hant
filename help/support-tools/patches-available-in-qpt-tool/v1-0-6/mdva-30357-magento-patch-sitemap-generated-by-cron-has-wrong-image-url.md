---
title: 'MDVA-30357：cron產生的Sitemap有錯誤的影像URL'
description: MDVA-30357修補程式修正了Commerce管理員中cron產生的Sitemap所建立的錯誤影像URL問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357：cron產生的Sitemap有錯誤的影像URL

MDVA-30357修補程式修正了Commerce管理員中cron產生的Sitemap所建立的錯誤影像URL問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.2至2.4.0

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Adobe Commerce中cron產生的Sitemap包含錯誤的影像URL路徑。

<u>要再現的步驟</u>：

1. 在「Commerce管理員」中，建立新網站、商店或商店檢視。
1. 請為每個商店至少新增一個產品，並為每個產品至少新增一個影像。
1. 在&#x200B;**管理員** > **存放區** > **組態** > **目錄** > **XML Sitemap** > **產生設定**&#x200B;中啟用依排程&#x200B;**產生** Sitemap。
1. 在&#x200B;**管理員** > **行銷** > **網站地圖**&#x200B;中，使用網站地圖名稱（例如&quot;*網站地圖.xml*&quot;）手動產生兩個商店的網站地圖。
   * 將檔案重新命名為&quot;*manual\_sitemap.xml*&quot;或複製檔案內容至任何文字編輯器。
1. 由cron工作`sitemap_generate`產生相同的Sitemap。
1. 比較手動產生的Sitemap &quot;*manual\_sitemap.xml*&quot;與cron &quot;*Sitemap.xml*&quot;產生的Sitemap。

<u>預期結果</u>：

快取的Sitemap影像路徑URL正確。

<u>實際結果</u>：

cron產生的網站地圖包含錯誤的影像路徑URL。 如果您嘗試從&quot;*sitemap.xml*&quot;開啟影像，則會顯示預設的預留位置。 手動產生的Sitemap URL不受此問題影響。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。

若要深入瞭解Sitemap，請參閱開發人員檔案中的下列文章：

* [新增Sitemap和搜尋引擎自動機制](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [設定並執行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [在瀏覽器中執行cron.php的安全](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
