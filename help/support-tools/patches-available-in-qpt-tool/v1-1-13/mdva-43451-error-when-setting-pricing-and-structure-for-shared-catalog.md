---
title: 'MDVA-43451：設定共用型錄的定價和結構時發生錯誤'
description: MDVA-43451修補程式可解決使用者無法設定共用目錄之定價與結構的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-43451。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451：設定共用型錄的訂價與結構時發生錯誤

MDVA-43451修補程式可解決使用者無法設定共用目錄之定價與結構的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-43451。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法設定共用目錄的定價和結構。 顯示下列訊息： *找不到要求的存放區。 請驗證存放區，然後再試一次。*

<u>要再現的步驟</u>：

1. 建立自訂網站。 網站的ID應為0、1、2。
1. 在上述網站下建立一個商店。 存放區的ID應為0、1、2。
1. 為上述存放區建立三個存放區檢視。 存放區檢視的ID應為0、1、2、3、4。
1. 刪除ID為2的存放區檢視。 現在，商店表格看起來應該類似於下表。

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. 建立新的共用目錄。
1. 設定「價格與結構」時，請選取在步驟2中建立的商店。
1. 儲存共用目錄。

<u>預期結果</u>：

共用目錄會順利儲存。

<u>實際結果</u>：

您無法儲存共用目錄。 會顯示下列錯誤：
*找不到要求的存放區。 請驗證存放區，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
