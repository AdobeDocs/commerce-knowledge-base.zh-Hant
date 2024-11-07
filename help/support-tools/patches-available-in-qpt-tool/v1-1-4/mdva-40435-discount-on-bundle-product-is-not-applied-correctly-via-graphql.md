---
title: 'MDVA-40435：未透過GraphQL正確套用套件組合產品的折扣'
description: MDVA-40435修補程式可解決無法透過GraphQL正確套用套件產品折扣的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40435。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 939ba940-35b5-4ab0-81fe-38981246e389
feature: GraphQL, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-40435：未透過GraphQL正確套用套件組合產品的折扣

MDVA-40435修補程式可解決無法透過GraphQL正確套用套件產品折扣的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-40435。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未透過GraphQL正確套用套件式產品的折扣。

<u>要再現的步驟</u>：

1. 建立購物車價格規則，包含$5固定折扣的優惠券代碼。
1. 透過GraphQL建立空的購物車。
1. 透過GraphQL將套件組合產品新增到購物車。
1. 透過GraphQL對固定金額(5$)套用優惠券代碼。
1. 透過GraphQL取得購物車資訊。

<u>預期結果</u>：

「折扣」為5美元。

<u>實際結果</u>：

「折扣」為空。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
