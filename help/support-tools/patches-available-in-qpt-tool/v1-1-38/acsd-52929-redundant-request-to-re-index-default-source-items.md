---
title: 'ACSD-52929：重新索引預設來源專案的備援請求'
description: 套用ACSD-52929修補程式來修正Adobe Commerce問題，其中當庫存索引器設定為非同步模式時，有重新索引預設來源專案的多餘請求。
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929：重新索引預設來源專案的備援請求

ACSD-52929修補程式修正了在非同步模式中設定清查索引器時，重新索引預設來源專案的請求冗餘的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.38。 修補程式ID為ACSD-52929。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當庫存索引器設定為非同步模式時，重新索引預設來源專案的要求有備援。

<u>要再現的步驟</u>：

1. 設定 [!DNL RabbitMQ].
1. 透過移至以下位置啟用非同步重新索引策略： **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** 並設定 **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. 建立自訂詳細目錄來源。
1. 登入 [!DNL RabbitMQ] 儀表板並前往佇列標籤。
1. 檢查 `inventory.indexer.sourceItem` 佇列並確保它沒有訊息。
1. 從後端開啟簡單產品並新增 *[!UICONTROL stock only]* 至自訂來源並儲存產品。
1. 載入 `inventory.indexer.sourceItem` 佇列在 [!DNL RabbitMQ] 控制面板，然後檢查訊息。

<u>預期結果</u>：

自訂來源的佇列中只有一個訊息。

<u>實際結果</u>：

佇列中會顯示兩個訊息：一個代表預設來源，另一個代表自訂來源。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
