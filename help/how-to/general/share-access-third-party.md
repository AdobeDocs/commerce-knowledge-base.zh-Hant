---
title: 雲端基礎結構上Adobe Commerce的第三方測試秘訣
description: 本文提供選項，讓您在雲端基礎結構上的Adobe Commerce擴充功能發生問題時，可與協力廠商共用存取權以進行測試/驗證。
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# 雲端基礎結構上Adobe Commerce的第三方測試秘訣

本文提供選項，讓您在雲端基礎結構上的Adobe Commerce擴充功能發生問題時，可與協力廠商共用存取權以進行測試/驗證。
在決定向第三方提供存取許可權的方式時，您應遵循適當的內部資料安全性程式和要求。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.3.0 - 2.3.7-p1、2.4.0 - 2.4.3

## 使用哪些環境進行測試

根據您的內部安全性標準，您可以選擇在本機環境中使用協力廠商疑難排解。 如果問題無法在本機重現，您可以提供雲端環境的存取權。 如果您選擇這麼做，請務必遵循您的內部安全標準。 如果提供對任何雲端環境的存取權，請確定您的第三方清楚知道可以進行的工作，以及僅復寫或允許程式碼變更等作業需要什麼核准。 這對於生產環境尤其重要。

## 為協力廠商提供存取權和資料

* 提供您的協力廠商雲端環境的存取權。 相關文章：

   * [Adobe Commerce說明中心使用手冊>共用存取權：授予其他使用者存取您帳戶的許可權](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) （在我們的支援知識庫中）。
   * 在我們的使用手冊中[共用您的Commerce帳戶](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/commerce-account/commerce-account-share)。

* 建立資料庫傾印（或給予第三方廠商執行此作業的存取權）。 這可以使用CLI或在Commerce Admin中完成。 此DB傾印會模糊化客戶資料，因此他們只得到程式碼和產品SKU等，沒有專有/客戶資料。 若需參考資訊，請在我們的支援知識庫中使用[共用您的Commerce帳戶] (/help/how-to/general/create-database-dump-on-cloud.md)。
* 測試完成後，請務必撤銷雲端環境的共用存取權，如支援知識庫中的[Adobe Commerce說明中心使用手冊>撤銷（刪除共用存取權）](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access)所述。

## 測試最佳實務

標準實務是在本機環境中進行疑難排解。 如果問題無法在本機重現，請前往測試。 協力廠商可能需要檢查生產環境。 請確定您的第三方知道他們僅會嘗試在生產與中繼上重現問題，不會進行任何程式碼變更，如果他們需要變更程式碼，則必須先取得您的許可權。

## 相關閱讀

* [在我們的支援知識庫中，在Adobe Commerce中使用協力廠商擴充功能的最佳作法](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento)。
