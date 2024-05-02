---
title: 'ACSD-54106：修正產品類別中的土耳其文重音字元排序'
description: 套用ACSD-54106修補程式，修正Adobe Commerce中土耳其文重音字元依名稱排序的類別產品順序不正確的問題。
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106：修正產品類別中的土耳其文重音字元排序

ACSD-54106修補程式修正土耳其文重音字元依名稱排序的類別產品順序不正確的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.39。 修補程式ID為ACSD-54106。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

按名稱排序類別中的產品時，土耳其重音字元排序不正確。

<u>要再現的步驟</u>：

1. 登入管理面板。
1. 建立以下命名的簡單產品，並將其指派給任何類別：

* 名稱A
* 名稱C
* 名稱D
* 名稱
* 名稱M
* Ö姓名
* 名稱U
* 名稱Y
* 名稱Z

1. 導覽至店面並存取包含產品的類別。
1. 修改排序順序以 *[!UICONTROL By Name]*.

<u>預期結果</u>：

產品會依照下列順序正確排序：

* 名稱A
* 名稱C
* 名稱D
* 名稱
* 名稱M
* Ö姓名
* 名稱U
* 名稱Y
* 名稱Z

<u>實際結果</u>：

產品未正確依下列順序排序：

* 名稱A
* 名稱D
* 名稱M
* 名稱Y
* 名稱Z
* 名稱C
* Ö姓名
* 名稱U
* 名稱

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
