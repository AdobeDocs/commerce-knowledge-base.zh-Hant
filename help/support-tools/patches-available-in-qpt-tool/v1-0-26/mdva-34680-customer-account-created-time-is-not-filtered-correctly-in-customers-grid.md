---
title: 「MDVA-34680：客戶帳戶未在客戶格線中正確篩選」
description: MDVA-34680修補程式修正00:00 UTC之後建立的客戶帳戶未在客戶格線中正確篩選的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26後，即可使用此修補程式。 修補程式ID為MDVA-34680。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680：客戶網格中的客戶帳戶未正確篩選

MDVA-34680修補程式修正00:00 UTC之後建立的客戶帳戶未在客戶格線中正確篩選的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26時，即可使用此修補程式。 修補程式ID為MDVA-34680。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1和2.4.2

**與Adobe Commerce版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.6-2.3.7和2.4.1-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當客戶帳戶在00:00 UTC之後建立，並且您嘗試按該日期篩選帳戶時，它不會傳回此客戶。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **組態** > **一般**，並將時區設定為東部標準[美國/紐約]。
1. 在00:00 UTC後建立新的客戶帳戶。
1. 移至&#x200B;**客戶** > **所有客戶**，並依今天的日期篩選帳戶。

<u>預期結果</u>：

客戶帳戶篩選器會顯示今天00:00 UTC之後建立的新帳戶。

<u>實際結果</u>：

客戶帳戶篩選器沒有顯示今天建立的新帳戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
