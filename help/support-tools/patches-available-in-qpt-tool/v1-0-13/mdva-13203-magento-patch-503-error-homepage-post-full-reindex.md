---
title: 'MDVA-13203修補程式：發佈完整重新索引後出現503錯誤首頁'
description: 「MDVA-13203 Adobe Commerce修補程式修正您的網站顯示維護頁面，且「system.log」中出現*CRITICAL： SQLSTATE\[23000\]：完整性條件約束違規*錯誤的問題。」 修補程式ID為MDVA-13203。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13時，即可使用此修補程式。
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-13203修補程式：503錯誤首頁發佈完整重新索引

MDVA-13203 Adobe Commerce修補程式修正您的網站顯示維護頁面，且`system.log`中有&#x200B;*CRITICAL： SQLSTATE\[23000\]：完整性條件約束違規*&#x200B;錯誤的問題。 修補程式ID為MDVA-13203。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13時，即可使用此修補程式。

## 受影響的產品和版本

**在雲端基礎結構2.2.4上為Adobe Commerce版本** Adobe Commerce建立修補程式。

**與Adobe Commerce版本相容：** Adobe Commerce （所有部署方法） 2.3.0-2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟：</u>

1. 前往受影響的URL。
1. 您會看到維護頁面。
1. 透過SSH檢查網站是否未處於維護狀態：
   <pre> bin/magento維護：狀態
    狀態：維護模式未啟用
    劐免IP位址清單：無</pre>
1. 檢視`system.log`：

<pre>grep critical -i var/log/system.log |尾

[2018-09-04 17:05:18] report.CRITICAL： SQLSTATE[23000]：完整性條件約束違規： 1062索引鍵'PRIMARY'的重複專案'4613'，查詢為： INSERT INTO 'search_tmp_5b8ebb4e994da5_88027289' ('entity_id'，'score')值(？， ？)，.. (？， ？)， (？， ？) [] []
[2018-09-04 17:05:21] report.CRITICAL： SQLSTATE[23000]：完整性條件約束違規： 1062索引鍵'PRIMARY'的重複專案'4613'，查詢為： INSERT INTO 'search_tmp_5b8ebb51579943_52333638' ('entity_id'，'score')值(？， ？)，..，(？) [] []
[2018-09-04 17:05:47] report.CRITICAL： SQLSTATE[23000]：完整性條件約束違規： 1062索引鍵「PRIMARY」的重複專案「1350」，查詢為： INSERT INTO 'search_tmp_5b8ebb6b7028f4_68065024' ('entity_id'，'score')值(？、？)、(？、？)、(？、？)、(？)、(？)、(？ ？？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？) [] []
[2018-09-04 17:05:47] report.CRITICAL： SQLSTATE[23000]：完整性條件約束違規： 1062索引鍵「PRIMARY」的重複專案「1350」，查詢為： INSERT INTO 'search_tmp_5b8ebb6b7885a9_23360993' ('entity_id'，'score')值(？、？)、(？、？)、(？、？)、(？)、(？)、(？ ？？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？)， (？， ？) [] []

日期

2018年9月4日星期二17:06:11 UTC</pre>

<u>預期結果：</u>您應該會看到網站。

<u>實際結果：</u>因為資料庫一致性問題，所以會顯示維護頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
