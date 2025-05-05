---
title: 「MDVA-43718：存取共用目錄時出現『消費者無權存取資源』錯誤」
description: MDVA-43718修補程式解決錯誤*取用者無權存取%resources的問題。*從自訂整合存取共用目錄時顯示。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-43718。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718：存取共用目錄時出現「消費者無權存取資源」錯誤

MDVA-43718修補程式解決錯誤&#x200B;*取用者無權存取%resources的問題。從自訂整合存取共用目錄時出現*。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15時，即可使用此修補程式。 修補程式ID為MDVA-43718。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從自訂整合存取共用目錄時出現下列錯誤： *消費者無權存取%resources*。

<u>要再現的步驟</u>：

1. 從「管理員> **系統** > **整合** > **新增整合**」建立新的整合。
1. 新增以下資源的存取權並啟用整合：

   * Magento_SharedCatalog：：list
   * Magento_SharedCatalog：：manage
   * Magento_目錄：：目錄

1. 使用整合存取： `rest/default/V1/sharedCatalog/1`

<u>預期結果</u>：

系統會傳回共用目錄的詳細資料。

<u>實際結果</u>：

系統傳回下列錯誤：

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
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
