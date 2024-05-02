---
title: 「ACSD-49286：出現多個產品Widget時，產品會新增到購物車兩次」
description: 套用ACSD-49286修補程式來修正Adobe Commerce問題，此問題導致當頁面上出現多個產品Widget時，產品會新增至購物車兩次。
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286：出現多個產品Widget時，產品會新增到購物車兩次

ACSD-49286修補程式修正了當頁面上出現多個產品Widget時，產品會新增至購物車兩次的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-49286。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當頁面上出現多個產品Widget時，產品會新增至購物車兩次。

<u>要再現的步驟</u>：

1. 登入管理員並前往 **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. 在內容區段中，按一下 **[!UICONTROL Edit]** 使用 [!DNL Page Builder].
1. 新增兩個列元素至 **[!UICONTROL Content]**.
1. 將產品新增至兩個列元素。
1. 在第一列中，將產品外觀設定為 [!UICONTROL Product Grid] 並選取要顯示的任何類別。
1. 在第二列，將產品外觀設定為 [!UICONTROL Product Carousel] 並選取要顯示的任何其他類別。
1. 前往店面 **[!UICONTROL Home Page]**，並從Product Grid新增一項產品。
1. 從新增其他產品 [!UICONTROL Product Carousel].

<u>預期結果</u>：

將產品新增到購物車後，產品數量不應加倍 [!UICONTROL Product Grid].

<u>實際結果</u>：

將產品新增到購物車後，產品數量會增加一倍 [!UICONTROL Product Grid].

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。 

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
