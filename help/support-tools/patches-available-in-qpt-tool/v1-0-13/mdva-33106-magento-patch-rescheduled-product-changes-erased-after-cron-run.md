---
title: 'MDVA-33106修補程式：重新排程的產品變更在cron執行後清除'
description: MDVA-33106修補程式修正了重新排程的產品變更在cron之後被清除的問題
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-33106修補程式：重新排程的產品變更在cron執行後清除

MDVA-33106修補程式修正了重新排程的產品變更在cron之後被清除的問題

```bash
bin/magento cron:run
```

命令執行。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 在Commerce Admin中，前往&#x200B;**目錄** > **產品**，然後按一下「編輯」。 請注意&#x200B;**價格**&#x200B;值，例如&#x200B;*9.99*。
1. 按一下&#x200B;**排程新更新**&#x200B;並填寫詳細資料：
   * 更新名稱並不重要。
   * 設定未來的日期，+1年作為開始日期和結束日期。
   * 將價格設定為&#x200B;*1.99*。
   * 儲存變更。
1. 前往「內容」暫存控制面板，選取格線檢視以檢視上方是否排程相符。
1. 選取排程更新旁的編輯動作。 資料仍應符合以上。
1. 將排程日期變更為更近的日期。 從現在開始，請改成+ 1週或+ 1個月，而非+1年。
1. 儲存變更，並檢查日期是否已在測試儀表板上更新。
1. 等待cron工作執行。
1. 在排程變更中再次按一下編輯並檢查價格。

<u>預期結果</u>：

價格是1.99。

<u>實際結果</u>：

價格為9.99。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
