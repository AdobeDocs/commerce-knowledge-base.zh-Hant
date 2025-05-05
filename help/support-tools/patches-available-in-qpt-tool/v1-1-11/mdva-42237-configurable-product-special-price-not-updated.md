---
title: 'MDVA-42237：未更新可設定的產品特別價格'
description: MDVA-42237修補程式修正了可設定產品的特殊價格在變更其次產品價格後未更新的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11後，即可使用此修補程式。 修補程式ID為MDVA-42237。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 3e890448-8368-4eb2-ab64-c04cdacf20bb
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42237：未更新可設定的產品特殊價格

MDVA-42237修補程式修正了可設定產品的特殊價格在變更其次產品價格後未更新的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11時，即可使用此修補程式。 修補程式ID為MDVA-42237。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

可設定產品的特殊價格在變更其子產品價格後不會更新。

<u>要再現的步驟</u>：

1. 移至&#x200B;**管理員** > **系統** > **索引管理**，然後為所有索引將&#x200B;**索引模式**&#x200B;設定為&#x200B;**依排程更新**。
1. 使用單一簡單產品建立可設定的產品，並設定子產品的特殊價格。
1. 檢查店面是否反映特殊價格。
1. 使用GraphQL移除特殊價格，並重新檢查店面的產品價格。

<u>預期結果</u>：

店面不再顯示特別價格。

<u>實際結果</u>：

店面未更新價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
