---
title: 「ACSD-45241：虛擬產品的庫存數量計算錯誤」
description: ACSD-45241修補程式修正建立銷退折讓單後，虛擬產品的庫存數量計算錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45241。 請注意，問題已在Adobe Commerce 2.4.4中修正。
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241：虛擬產品的庫存數量計算錯誤

ACSD-45241修補程式修正建立銷退折讓單後，虛擬產品的庫存數量計算錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45241。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立銷退折讓單後，虛擬產品的存貨數量計算錯誤。

<u>要再現的步驟</u>：

1. 在Commerce管理員中以虛擬產品作為子產品建立可設定產品。
1. 請確認在步驟一中建立的兩個產品均有庫存。
1. 將步驟1中建立的虛擬產品數量標示為100，同時保留可銷售數量100。
1. 將產品新增至購物車。
1. 使用在步驟一中建立的虛擬產品下訂單。
1. 將訂單狀態維持為「擱置中」。 無需處理付款。
1. 已在`inventory_reservation`中建立`order_created`筆記錄。 虛擬產品數量顯示100，可銷售數量為99。
1. 開啟訂單，並移至&#x200B;**發票** > **提交發票**。
1. 已在`inventory_reservation`中建立`invoice_created`筆記錄。 虛擬產品數量現在是99，而可銷售數量也是99。
1. 建立銷退折讓單，但不選取&#x200B;**退回存貨**。

<u>預期結果</u>：

`inventory_reservation`中未建立任何新記錄，且虛擬產品的庫存數量未變更。

<u>實際結果</u>：

已在`inventory_reservation`中建立`creditmemo_created`記錄，而虛擬產品庫存數量已調整為98，可銷售數量為99。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
