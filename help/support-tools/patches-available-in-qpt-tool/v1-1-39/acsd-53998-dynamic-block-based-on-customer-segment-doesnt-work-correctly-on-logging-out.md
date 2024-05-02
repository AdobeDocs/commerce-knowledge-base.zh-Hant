---
title: 「ACSD-53998：登出後根據客戶區段的動態區塊無法正常運作」
description: 套用ACSD-53998修補程式來修正Adobe Commerce問題，該問題導致基於客戶區段的動態區塊在從客戶帳戶登出後無法正常運作。
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: 5a82a6b8-e8f7-47ff-89f6-93a39b72fe38
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53998：登出後根據客戶區段的動態區塊無法正常運作

ACSD-53998修補程式修正了從客戶帳戶登出後，以客戶區段為基礎的動態區塊無法正常運作的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.39。 修補程式ID為ACSD-53998。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p2 - 2.4.4-p6、2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從客戶帳戶登出後，以客戶區段為基礎的動態區塊無法正常運作。

<u>必要條件</u>：

安裝並啟用 [!DNL Page Builder] 模組。

<u>要再現的步驟</u>：

1. 無條件建立兩個客戶區段。
1. 為每個區段建立兩個動態區塊。
1. 建立包含兩個動態區塊的區塊，做為 [!DNL Page Builder] 動態區塊。
1. 建立包含上述區塊的Widget，並讓該區塊顯示在所有頁面的頁尾區段下。
1. 清除快取。
1. 開啟首頁。
1. 以客戶身分登入。
1. 登出。

<u>預期結果</u>：

為登入客戶建立的橫幅不會顯示給訪客使用者。

<u>實際結果</u>：

即使從客戶帳戶登出，也會顯示為已登入客戶區段建立的橫幅。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
