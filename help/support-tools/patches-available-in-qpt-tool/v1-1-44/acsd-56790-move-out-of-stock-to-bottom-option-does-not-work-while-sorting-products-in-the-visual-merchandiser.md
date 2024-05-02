---
title: '''ACSD-56790： **[!UICONTROL move out of stock to bottom]在排序產品時，**選項無法運作  [!DNL Visual Merchandiser]『'
description: 套用ACSD-56790修補程式，修正Adobe Commerce在視覺化商品銷售中排序產品時，從庫存移至底部選項無法運作的問題。
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790： **[!UICONTROL move out of stock to bottom]** 在排序產品時，選項無法運作 [!DNL Visual Merchandiser]

ACSD-56790修補程式修正了在中排序產品時，從庫存移至底部選項無法運作的問題。 [!DNL Visual Merchandiser]. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.44。 修補程式ID為ACSD-56790。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 **[!UICONTROL move out of stock to bottom]** 在排序產品時，選項無法運作 [!DNL Visual Merchandiser]

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 和建立下列屬性。
1. 建立新網站： **非主要**.
1. 建立 **非主要存放區** 這個新網站。
1. 建立兩個存放區：

   * 第一個 **主要網站商店**.
   * 中的第二個 **非主要存放區**.

1. 建立兩個來源：
   * 字母。
   * 數字。

1. 建立兩個庫存：
   * 第一個主要 — 銷售管道：主要網站 — 指派的來源：信件。
   * 第二個非主要 — 銷售管道：非主要 — 指定來源：數字。

1. 在兩個網站上建立三個簡單的產品，全部在預設類別中，全部指派給兩個來源：

   * 產品A — 數量 *10* 在字母中，數量 *0* 在數字中。
   * 產品1 — 數量 *0* 在字母中，數量 *10* 在數字中。
   * ProductA1 — 數量 *10* 在字母中，數量 *10* 在數字中。

1. 前往 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** 並選取  **[!UICONTROL Default category]**.
1. 將範圍更改為 **第一**.
1. 展開「類別」區段中的「產品」 。
1. 挑選排序順序為： **[!UICONTROL move out of stock to bottom]**

<u>預期結果</u>：

產品清單，具有 **無庫存** 產品會移至底部。

<u>實際結果</u>：

產品無法載入。 頁面會重新導向至管理控制面板，並顯示錯誤訊息： `Invalid security or form key. Please refresh the page`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
