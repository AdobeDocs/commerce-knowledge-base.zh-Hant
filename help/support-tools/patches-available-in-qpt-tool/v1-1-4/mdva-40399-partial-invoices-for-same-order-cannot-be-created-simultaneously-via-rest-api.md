---
title: 「MDVA-40399：無法透過API同時建立相同訂單的部分發票」
description: MDVA-40399修補程式修正了無法透過Rest API同時建立相同訂單之部分發票的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40399。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399：無法透過API同時建立相同訂單的部分商業發票

MDVA-40399修補程式修正了無法透過Rest API同時建立相同訂單之部分發票的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40399。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

不能使用Rest API同時建立相同訂單的部分商業發票。

<u>必要條件</u>：

至少有兩個變數的可設定產品。

<u>要再現的步驟</u>：

1. 將可設定產品的兩個變體新增到購物車。
1. 下訂單。
1. 透過Rest API同時為訂單建立兩張商業發票。

<u>預期結果</u>：

* 兩個商業發票都必須成功建立。
* 應該針對`sales_order_item`資料表中的兩個商業發票更新`qty_invoiced`。
* 這兩種產品都應該有已開立商業發票的數量。

<u>實際結果</u>：

* 兩個商業發票都已成功建立。
* `qty_invoiced`未針對`sales_order_item`資料表中的其中一個商業發票進行更新。
* 在管理員的&#x200B;**訂單檢視**&#x200B;頁面中，只針對一個產品顯示發票數量。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修補程式區段。
