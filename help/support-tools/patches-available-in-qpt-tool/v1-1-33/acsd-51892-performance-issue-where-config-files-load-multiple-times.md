---
title: 'ACSD-51892：設定檔案載入多次的效能問題'
description: 套用ACSD-51892修補程式，修正部署期間設定檔案載入多次的Adobe Commerce效能問題。
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892：設定檔案載入多次的效能問題

ACSD-51892修補程式修正載入 `app/etc/env.php` 和 `app/etc/config.php` 檔案於每次在單一請求中存取部署設定值時。 過度讀取檔案會給系統帶來壓力，導致整體效能降低。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.33。 修補程式ID為ACSD-51892。 請注意，Adobe Commerce 2.4.6-p2已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

設定檔案載入多次時會發生效能問題。

<u>要再現的步驟</u>：

1. 執行部署或升級至Adobe Commerce 2.4.6或更新版本。
1. 檢查檔案系統記錄檔以存取 `app/etc/env.php` 和 `app/etc/config.php` 檔案執行期間。

<u>預期結果</u>：

部署在正常時間範圍內成功。

<u>實際結果</u>：

* 伺服器正疲於回應您輸入的任何命令。 這會導致 *錯誤503第一個位元組逾時* 存取網站時。
* 記錄檔中有多個專案可存取 `app/etc/env.php` 和 `app/etc/config.php` 檔案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
