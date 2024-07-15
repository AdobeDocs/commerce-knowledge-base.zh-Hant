---
title: 'MDVA-19640：進階報告未顯示任何資料'
description: MDVA-19640修補程式修正進階報告未顯示任何資料的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-19640。 請注意，目前沒有計畫在未來版本中修正此問題。
exl-id: 6df70f10-5d34-4540-b2ae-3a0be32f2bfd
feature: Commerce Intelligence
role: Admin
source-git-commit: 2914a110444898f78d2ed43ea96a9c5f6e70229f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-19640：進階報告未顯示任何資料

MDVA-19640修補程式修正進階報告未顯示任何資料的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-19640。 請注意，目前沒有計畫在未來版本中修正此問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.0

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.1 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 在Admin中，移至&#x200B;**報表** > **Business Intelligence**&#x200B;並選取&#x200B;**進階報表**。
1. 檢視&#x200B;**進階報告**&#x200B;頁面。

<u>預期結果</u>：

進階報表如預期包含資訊。

<u>實際結果</u>：

進階報表不會顯示任何資料。

<u>安裝修補程式後需要的其他步驟</u>：

必須套用下列SQL查詢來更新cron_schedule表格中的記錄：
`UPDATE core_config_data SET path = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics") WHERE path LIKE "crontab/default/jobs/analytics%";`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
