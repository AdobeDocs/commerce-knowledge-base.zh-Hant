---
title: 「ACSD-51114：啟用非同步索引時，隨機產品從大型目錄中消失」
description: 套用ACSD-51114修補程式來修正Adobe Commerce問題：啟用非同步索引時，大型目錄中的隨機產品會消失。
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114：啟用非同步索引時，隨機產品從大型目錄中消失

>[!NOTE]
>
>此修補程式已棄用。

ACSD-51114修補程式修正啟用非同步索引時，隨機產品從大型目錄中消失的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.30。 修補程式ID為ACSD-51114。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並在[[!DNL Quality Patches Tool]：搜尋修正程式頁面]。使用修正程式ID作為搜尋關鍵字來尋找修正程式。

## 問題

啟用非同步索引時，隨機產品從大型目錄中消失。

<u>要再現的步驟</u>：

1. 建立一組10種產品。
1. 將所有索引子設定為 **[!UICONTROL Update on Save]** 模式。
1. 建立類別並指派所有產品至該類別。
1. 停用所有產品。
1. 開啟類別，並確認沒有產品。
1. 將所有索引子設定為 **[!UICONTROL Update on Schedule]** 模式。
1. 設定 `DEFAULT_BATCH_SIZE` 至2英吋  `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. 啟用產品，順序如下：1、9、2、5、10、3。
1. 執行cron命令。
1. 再次開啟類別。

<u>預期結果</u>：

所有啟用的產品都會顯示。

<u>實際結果</u>：

所有啟用的產品都不會顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
