---
title: ACSD-51845：無法透過非同步大量 [!DNL API]更新具有階層價格與不同屬性集的後續產品
description: 套用ACSD-51845修補程式以修正Adobe Commerce問題，此問題導致您無法透過非同步大量 [!DNL REST API]以階層價格及不同屬性集更新後續產品。
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845：無法透過非同步大量[!DNL API]更新具有層級價格與不同屬性集的後續產品

ACSD-51845修補程式修正無法透過非同步大量[!DNL REST API]以階層價格及不同屬性集更新後續產品的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51845。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過非同步大量[!DNL REST API]，以層級價格及不同屬性集更新後續產品失敗。

<u>要再現的步驟</u>：

1. 設定[!DNL RabbitMQ]。
1. 建立兩個屬性集。
1. 建立兩個&#x200B;**簡單產品**，將每個產品指派給不同的屬性集。
1. 為每個產品新增&#x200B;**客戶群組價格**。
1. 在同一個批次[!DNL API]更新中更新兩個產品。
1. 確定`bin/magento queue:consumers:start async.operations.all`命令正在執行。
1. 檢查大量[!DNL API]狀態。

<u>預期結果</u>：

服務執行成功。

<u>實際結果</u>：

系統傳回錯誤訊息： *無法儲存產品。 請再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
