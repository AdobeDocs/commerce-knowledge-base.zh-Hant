---
title: 'MDVA-40550：重新索引後前端上遺失的產品'
description: MDVA-40550修補程式可解決重新索引導致部分或全部店麵類別遺失產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40550。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550：重新索引後前端上遺失的產品

MDVA-40550修補程式可解決重新索引導致部分或全部店麵類別遺失產品的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-40550。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 建立產品。
1. 將索引子切換為&#x200B;**依排程**&#x200B;更新。
   * 將產品指派至類別。
1. 啟用xdebug並在`\Magento\Indexer\Model\Indexer::reindexAll`和`\Magento\Indexer\Model\IndexMutex::execute`中建立xdebug中斷點。
1. 使用下列命令執行`catalog_category_product`的&#x200B;**完整重新索引**：

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * 等候執行在中斷點`\Magento\Indexer\Model\Indexer::reindexAll`停止。

1. 在另一個主控台中，使用下列命令並行執行&#x200B;**部分重新索引**：

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 等候執行在中斷點`\Magento\Indexer\Model\IndexMutex::execute`停止。 它會鎖定`catalog_category_product`索引子。
1. 繼續執行`catalog_category_product`的完整重新索引，並等候鎖定逾時（60秒）。

<u>預期結果</u>：

主控台中沒有錯誤訊息。

<u>實際結果</u>：

您會收到下列錯誤：

*無法取得索引的鎖定： catalog_category_product。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
