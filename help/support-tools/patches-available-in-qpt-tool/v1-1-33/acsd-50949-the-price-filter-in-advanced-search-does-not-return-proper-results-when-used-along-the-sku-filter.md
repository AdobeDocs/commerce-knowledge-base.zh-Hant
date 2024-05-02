---
title: 'ACSD-50949：與SKU篩選器搭配使用時，進階搜尋中的價格篩選器沒有傳回正確結果'
description: 套用ACSD-50949修補程式來修正Adobe Commerce問題，該問題導致在搭配SKU篩選器使用時，進階搜尋中的價格篩選器無法傳回正確結果。
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949：與SKU篩選器搭配使用時，進階搜尋中的價格篩選器沒有傳回正確結果

ACSD-50949修補程式修正了進階搜尋中的價格篩選器在搭配SKU篩選器使用時未傳回正確結果的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.33。 修補程式ID為ACSD-50949。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 問題

與SKU篩選器搭配使用時，進階搜尋中的價格篩選器沒有傳回正確結果。

<u>要再現的步驟</u>：

1. 建立多個產品，例如：

   | SKU | 名稱 | 價格 | 數量 |
   |-----|-----------|-------|----------|
   | MJ1 | 產品1 | $10 | 10 |
   | MJ2 | 產品2 | 15美元 | 10 |
   | MJ3 | 產品3 | 21美元 | 10 |
   | MJ4 | 產品4 | 32美元 | 10 |
   | MJ5 | 產品5 | 33美元 | 10 |
   | MJ6 | 產品6 | 34美元 | 10 |
   | MJ7 | 產品7 | 44美元 | 10 |

1. 開啟 **[!UICONTROL Advanced Search]** 並依SKU搜尋： &quot;MJ&quot;。
1. 按一下 **[!UICONTROL Modify your search]** 連結。
1. 將價格範圍新增到條件來源 *1* 至 *21*，然後按一下 **[!UICONTROL Search]** 按鈕。

<u>預期結果</u>：

系統只會傳回價格在定義範圍內的產品。

<u>實際結果</u>：

價格高於以下值的產品： *21美元* 會傳回。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
