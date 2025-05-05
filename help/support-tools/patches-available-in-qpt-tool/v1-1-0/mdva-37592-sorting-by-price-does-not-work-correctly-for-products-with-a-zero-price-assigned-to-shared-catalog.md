---
title: 'MDVA-37592：依價格排序不適用於價格為零的產品'
description: MDVA-37592 Adobe Commerce修補程式解決指派給共用目錄之價格為零的產品無法正確依價格排序的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-37592。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592：依價格排序不適用於價格為零的產品

MDVA-37592 Adobe Commerce修補程式解決指派給共用目錄之價格為零的產品無法正確依價格排序的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0時，即可使用此修補程式。 修補程式ID為MDVA-37592。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端架構上的Adobe Commerce 2.4.0-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署型別） 2.3.6-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

依價格排序無法正確用於指派給共用目錄價格為零的產品。

<u>必要條件</u>：

已安裝B2B。

<u>要再現的步驟</u>：

1. 啟用共用目錄。
1. 使用下列價格建立四種產品，並將它們指派至類別 — $50、$60、$70和$80。
1. 使用上述產品建立共用目錄。
1. 將價格為$70的產品自訂價格設為零。
1. 現在建立公司使用者，並將其指派至剛建立的共用目錄。
1. 使用公司帳戶登入，並瀏覽至指派產品的類別。
1. 嘗試依價格排序。

<u>預期結果</u>：

價格為零的產品會正確排序。

<u>實際結果</u>：

價格為零的產品無法正確排序。 而是根據原始價格排序。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 我們的雲端架構上的Adobe Commerce：開發人員檔案中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修補程式區段。
