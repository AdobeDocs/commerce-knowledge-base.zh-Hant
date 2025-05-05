---
title: 'MDVA-39229：更新目錄規則中繼更新開始時間時發生錯誤'
description: MDVA-39229修補程式修正了使用者在更新目錄規則測試更新開始時間後收到錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-39229。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229：更新目錄規則中繼更新開始時間時發生錯誤

MDVA-39229修補程式修正了使用者在更新目錄規則測試更新開始時間後收到錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-39229。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.3.4-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

更新目錄規則測試更新的開始時間後，使用者收到錯誤。

<u>要再現的步驟</u>：

1. 建立型錄價格規則。
1. 建立並執行任何測試更新。
1. 執行查詢，並確認已建立Staging旗標。


   `select * from flag;`


1. 建立新的測試更新，以便在五分鐘後開始。
1. 開啟&#x200B;**內容** > **暫存** > **儀表板** > **新更新**，將開始時間延遲一分鐘。
1. 等候六分鐘。
1. 執行cron。

<u>預期結果</u>：

更新開始時間已變更，且已套用更新。 已從`staging_update`資料表中刪除舊更新。

<u>實際結果</u>：

使用者收到以下錯誤：

*report.ERROR： Cron工作staging_synchronize_entities_period有錯誤：無法刪除作用中的更新。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修補程式區段。
