---
title: 'MDVA-38852：目錄詳細目錄鎖定會降低效能的表格'
description: MDVA-38852修補程式可解決目錄庫存鎖定表格以進行更新的問題，此問題會在同時下幾個訂單時大幅降低效能。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-38852。 請注意，問題已在Adobe Commerce 2.3.6中修正。
exl-id: 6ecee9c8-1f39-47de-8fbc-55e30cc936af
feature: Catalog Management, Inventory, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-38852：目錄詳細目錄會鎖定降低效能的表格

MDVA-38852修補程式可解決目錄庫存鎖定表格以進行更新的問題，此問題會在同時下幾個訂單時大幅降低效能。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-38852。 請注意，問題已在Adobe Commerce 2.3.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

目錄存貨會鎖定更新的表格，在同時下幾個訂單時，會大幅降低效能。

<u>要再現的步驟</u>：

1. 新增產品至購物車。
1. 繼續結帳，並嘗試下訂單。

<u>預期結果</u>：

* 沒有死結。
* 同時下幾個訂單時，效能不會降低。

<u>實際結果</u>：

* 同時有多個使用者時，下訂單的速度會非常慢。
* 發生死結錯誤，如下所示：

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
