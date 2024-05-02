---
title: 「ACSD-47669：匯入具有可自訂選項的產品時出現內部伺服器錯誤」
description: 套用ACSD-47669修補程式，修正在匯入具有可自訂選項的產品期間發生內部伺服器錯誤的Adobe Commerce問題。
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669：匯入具有可自訂選項的產品時出現內部伺服器錯誤

ACSD-47669修補程式修正了在使用可自訂選項匯入產品期間發生內部伺服器錯誤的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.38。 修補程式ID為ACSD-47669。 請注意，Adobe Commerce 2.4.6已修正此問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯入具有可自訂選項的產品時發生內部伺服器錯誤。

<u>要再現的步驟</u>：

1. 建立其他商店檢視。 確定您有2個商店檢視，例如en、UK。
1. 建立兩個簡單的產品，例如prod1和prod2。
1. 準備一個csv檔案，該檔案會針對每個商店檢視中的產品以及新增自訂選項 **所有商店檢視** 範圍。 匯入此csv檔案。
1. 準備另一個包含兩個記錄的csv檔案。 第一筆記錄應更新專屬於英國存放區檢視範圍的&#39;prod1&#39;自訂選項，第二筆記錄應更新專屬於英國存放區的&#39;prod2&#39;自訂選項 **所有商店檢視** 範圍。 匯入第二個csv檔案。

<u>預期結果</u>：

您應該能夠自訂選項，不會發生任何錯誤。

<u>實際結果</u>：

發生完整性限制違規錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
