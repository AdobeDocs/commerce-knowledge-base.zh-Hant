---
title: MDVA-42046：指派給產品屬性的值不正確
description: MDVA-42046修補程式修正了更新具有日期輸入欄位的產品時，為產品屬性指派的值不正確的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-42046。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046：指派給產品屬性的值不正確

MDVA-42046修補程式修正了更新具有日期輸入欄位的產品時，為產品屬性指派的值不正確的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-42046。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.3.5-p2和2.4.0 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

儲存具有`news_from_date`和/或`news_to_date`欄位的產品後，這些欄位的值會重設為預設值。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 匯出在步驟一中建立的產品。
1. 在匯出的CSV檔案中，在`news_from_date`和`news_to_date`欄位中放入一些值。 例如：2021-05-15和2021-06-18。
1. 使用修改過的CSV檔案匯入產品。
1. 在產品格線中新增其他欄「將產品設為新的開始日期」和「將產品設為新的結束日期」。
1. 開啟產品的編輯頁面，若未進行任何變更，請按一下[儲存]。**&#x200B;**
1. 返回產品格線並檢查產品的資料。

<u>預期結果</u>：

「將產品設為新的開始日期」和「將產品設為新的結束日期」都與儲存前相同。

<u>實際結果</u>：

* 「將產品設為新的起始日期」和「將產品設為新的終止日期」欄中的值已變更。

* 「將產品設為新的開始日期」欄會顯示目前的日期，「將產品設為新的結束日期」欄是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
