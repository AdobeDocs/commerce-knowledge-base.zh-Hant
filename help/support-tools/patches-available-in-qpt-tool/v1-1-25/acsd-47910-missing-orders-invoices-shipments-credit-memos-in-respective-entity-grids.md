---
title: 'ACSD-47910：個別實體網格中遺漏的訂單、商業發票、出貨、銷退折讓單'
description: 套用ACSD-47910修補程式，修正個別實體網格中遺失訂單、商業發票、出貨及銷退折讓單的Adobe Commerce問題。
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910：個別實體網格中遺漏的訂單、商業發票、出貨及銷退折讓單

ACSD-47910修補程式修正個別實體網格中遺失訂單、商業發票、出貨及銷退折讓單的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.25。 修補程式ID為ACSD-47910。 尚未提供將修正此問題的版本。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

個別實體網格中遺漏訂單、商業發票、出貨及銷退折讓單。

<u>要再現的步驟</u>：

1. 啟用 **[!UICONTROL Asynchronous indexing]** 在 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. 下兩張訂單。
1. 執行cron將這些訂單同步至網格。
1. 開啟其中一個訂單，使其準備好開立商業發票。 尚未提交商業發票。
1. 建立可放在前端的新訂單。 請勿點選「下訂單」按鈕。
1. 新增 `sleep(30)` 在 `foreach` 在 `NotSyncedDataProvider::L43`.
1. 執行 `bin/magento cron:run`.
1. 現在下新訂單。
1. 為上一張訂單開立商業發票。
1. 再次執行cron，預期新訂單將同步。
1. 前往「管理員」中的訂單格線。

<u>預期結果</u>：

新訂單應會出現在訂單格線上。

<u>實際結果</u>：

先前的訂單更新已同步至格線(**[!UICONTROL status: Processing]**)。 新順序絕不會出現在格線上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
