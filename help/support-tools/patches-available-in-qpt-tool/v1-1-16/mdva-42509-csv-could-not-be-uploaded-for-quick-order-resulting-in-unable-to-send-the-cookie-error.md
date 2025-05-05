---
title: 「MDVA-42509：無法為快速訂單上傳CSV，導致「無法傳送Cookie」錯誤」
description: MDVA-42509修補程式解決無法針對快速訂購上傳CSV而導致*無法傳送Cookie*錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16後，即可使用此修補程式。 修補程式ID為MDVA-42509。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 7aa0e710-9a28-4531-b9cb-c82f654487f4
feature: B2B, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-42509：無法為快速訂單上傳CSV，導致「無法傳送Cookie」錯誤

MDVA-42509修補程式解決無法為快速訂購上傳CSV而導致&#x200B;*無法傳送Cookie*&#x200B;錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16時，即可使用此修補程式。 修補程式ID為MDVA-42509。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用CSV建立大量產品的快速訂單會顯示Cookie錯誤： *無法傳送Cookie*

<u>要再現的步驟</u>：

1. 透過瀏覽至&#x200B;**商店** > **設定** > **組態** > **一般** > **B2B功能**&#x200B;來啟用快速訂購。
1. 建立客戶帳戶，並前往頂端連結的&#x200B;**快速訂購**。
1. 嘗試使用具有超過100個SKU的CSV建立快速訂單。

<u>預期結果</u>：

您可以建立具有大量SKU的快速訂單。

<u>實際結果</u>：

系統會顯示與Cookie大小相關的錯誤訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
