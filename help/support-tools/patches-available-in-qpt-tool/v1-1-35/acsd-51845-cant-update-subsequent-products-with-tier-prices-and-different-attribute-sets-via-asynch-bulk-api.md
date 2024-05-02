---
title: 「ACSD-51845：無法透過非同步大量更新具有層級價格和不同屬性集的後續產品 [!DNL API]"
description: 套用ACSD-51845修補程式以修正Adobe Commerce無法透過非同步大量更新具有層級價格和其他屬性集的後續產品的問題 [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845：無法透過非同步大量更新具有層級價格與不同屬性集的後續產品 [!DNL API]

ACSD-51845修補程式修正無法透過非同步大量更新具有階層價格及不同屬性集的後續產品的問題 [!DNL REST API]. 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.35。 修補程式ID為ACSD-51845。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過非同步大量更新具有層級價格和不同屬性集的後續產品失敗 [!DNL REST API].

<u>要再現的步驟</u>：

1. 設定 [!DNL RabbitMQ].
1. 建立兩個屬性集。
1. 建立兩個 **簡單產品**，將每個產品指派至不同的屬性集。
1. 新增 **客戶群組價格** 每個產品的。
1. 以相同批次更新兩個產品 [!DNL API] 更新。
1. 確定 `bin/magento queue:consumers:start async.operations.all` 命令執行中。
1. 檢查大量 [!DNL API] 狀態。

<u>預期結果</u>：

服務執行成功。

<u>實際結果</u>：

系統會傳回錯誤訊息： *無法儲存產品。 請重試。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
