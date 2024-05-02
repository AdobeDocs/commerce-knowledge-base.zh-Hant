---
title: 「ACSD-56886：可設定的產品在子產品停用時無庫存」
description: 套用ACSD-56886修補程式來修正Adobe Commerce問題，此問題導致可設定產品在產品停用時失去庫存子項。
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886：當子產品停用時，可設定的產品會無庫存

ACSD-56886修補程式修正了子產品停用時，可設定產品無存貨的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.45。 修補程式ID為ACSD-56886。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當子項產品停用時，可設定的產品會變成無庫存。

<u>要再現的步驟</u>：

1. 以管理員身分登入。
1. 設定中的所有索引子 **[!UICONTROL Update By Schedule]** 模式。
1. 建立下列可設定的產品：

   * 名稱= *測試可設定1*
   * 屬性= *顏色*
   * 值= *紅色* 和 *黑色*
   * 的價格 **紅色**  子產品= *$100*；
   * 「黑色」子產品的價格= *200美元*.

1. 為可設定產品建立以下排程更新：

   * 開始日期= *3* 分鐘後。
   * 結束日期= *5* 開始日期後分鐘。
   * 產品名稱= *已編輯可設定的測試1*.
   * 停用 **紅色** 中的子產品 **可設定** 區段。

1. 等待開始日期。
1. 在店面開啟可設定的產品詳細資訊。

<u>預期結果</u>：

可設定的產品顯示為 **有貨** 使用 **低至200** 標籤。

<u>實際結果</u>：

可設定的產品顯示為 **無庫存**.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
