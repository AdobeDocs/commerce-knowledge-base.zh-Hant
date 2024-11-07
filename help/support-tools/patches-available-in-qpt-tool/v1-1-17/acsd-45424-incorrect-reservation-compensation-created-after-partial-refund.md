---
title: 'ACSD-45424：部分退款後建立的預訂補償不正確'
description: ACSD-45424修補程式修正部分退款後建立錯誤預訂補償的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45424。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 0676cfda-a28e-4a66-a75b-8a3fc5e22566
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# ACSD-45424：部分退款後建立的預訂補償不正確

ACSD-45424修補程式修正部分退款後建立錯誤預訂補償的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45424。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

部份退款之後會建立不正確的預訂補償。

<u>要再現的步驟</u>：

1. 啟用店內交貨送貨方法。
1. 建立三個存貨來源，並確定各取貨地點有效（來源1、來源2、來源3）。
1. 建立新庫存並將三個來源指定給新庫存。
   * 此庫存應指派給主要網站。
1. 建立簡單產品P3，並將所有來源指派給它。
1. 新增簡易產品來源的下列數量，並啟用延期交貨：
   * 預設來源 — 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. 從前端將簡單產品新增到購物車，然後繼續前往送貨表單。
1. 選取「source1」作為出貨地點。
1. 完成順序並在資料庫中執行下列查詢：

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   您將會在`inventory_reservation`表格中取得訂購記錄。 數量為10，這是正確的。
1. 從後端開立此訂單的商業發票。
1. 現在，僅針對一種產品建立銷退折讓單。 請勿選取&#x200B;*返回庫存*&#x200B;核取方塊。
1. 從步驟8執行相同的查詢。

<u>預期結果</u>：

如果您在建立銷退折讓單期間未選取&#x200B;*退回存貨*，則`inventory_reservation`表格將不會有與銷退折讓單對應的記錄。

<u>實際結果</u>：

即使在銷退折讓單建立期間，您並未選取&#x200B;*退回存貨*，它仍會將記錄新增至`creditmemo_created`事件型別的`inventory_reservation`資料表。 此外，即使您只建立一個數量的銷退折讓單，新增至`inventory_reservation`表格的銷退折讓單記錄仍有10個數量。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
