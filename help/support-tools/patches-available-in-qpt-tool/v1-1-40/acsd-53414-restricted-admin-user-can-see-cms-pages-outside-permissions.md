---
title: 「ACSD-53414：受限制的管理員使用者可以檢視其許可權範圍以外的CMS頁面」
description: 套用ACSD-53414修補程式以修正Adobe Commerce問題，該問題導致受限制的管理員使用者無法檢視其許可權範圍以外的CMS頁面。
feature: CMS
role: Admin, Developer
exl-id: f8540d52-a3bb-49bb-8868-7b1db03e571b
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53414：受限制的管理員使用者可檢視其許可權範圍以外的CMS頁面

ACSD-53414修補程式修正受限管理員使用者可在其許可權範圍外檢視CMS頁面的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.40。 修補程式ID為ACSD-53414。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限制的管理員使用者看見CMS頁面超出其許可權範圍。

<u>要再現的步驟</u>：

1. 建立新網站(sub_website)、商店(sub_store)和商店(sub_storeview)。
1. 建立sub_expert角色，允許sub_website和sub_store的範圍。 僅指派下列許可權： [!UICONTROL Dashboard] 和 [!UICONTROL Pages].
1. 建立新的管理員使用者並將其指派給sub_expert角色。
1. 將下列CSM頁面指派給sub_storeview與預設的storeview。

   * [!UICONTROL 404 Not Found] >子商店
   * [!UICONTROL 503 Service Unavailable] >預設預覽

1. 使用步驟3中建立的管理員使用者登入管理員。
1. 檢查CMS頁面格線。

<u>預期結果</u>：

*[!UICONTROL 503 Service Unavailable]* 網頁管理員看不到該頁面。

<u>實際結果</u>：

*[!UICONTROL 503 Service Unavailable]* 對網頁管理員可見。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
