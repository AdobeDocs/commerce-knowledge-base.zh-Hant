---
title: 由於內容暫存問題，所有頁面均出現錯誤404
description: 本文針對Adobe Commerce內部部署和Adobe Commerce雲端基礎結構問題提供修正，存取任何店面頁面或Commerce管理員時，會出現404錯誤。
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# 由於內容暫存問題，所有頁面均出現錯誤404

本文針對Adobe Commerce內部部署和Adobe Commerce雲端基礎結構問題提供修正，存取任何店面頁面或Commerce管理員時，會出現404錯誤。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

>[!NOTE]
>
>本文不適用於您嘗試收到404錯誤的情況 [預覽測試更新](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). 如果您遇到此問題，請開啟 [支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

存取任何店面頁面或管理員在使用對店面內容資產執行含有已排程更新的作業後，會導致404錯誤（「糟糕，我們的不良……」頁面） [內容分段](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) （使用排程的存放區內容資產更新） [Magento\_Staging模組](https://developer.adobe.com/commerce/php/module-reference/))。 例如，您可能會刪除有排程更新的產品，或移除排程更新的結束日期。

存放區內容資產包括：

* 產品
* 類別
* 目錄價格規則
* 購物車價格規則
* CMS頁面
* CMS區塊
* Widget

部分情況將在下面的「原因」一節中討論。

## 原因

此 `flag` 資料庫(DB)中的表格包含無效的連結，指向 `staging_update` 表格。

此問題與內容測試有關。 以下是兩種特定情況；請注意，可能有更多情況會觸發此問題。

**案例1：** 刪除符合以下條件的商店內容資產：

* 已排程內容暫存的更新
* 更新有結束日期（即更新的資產恢復為先前版本的到期日）
* 更新的結束日期是過去的日期

同時，如果刪除的資產沒有排程更新的結束日期，則可能不會發生問題。

**案例2：** 正在移除排程更新的結束日期/時間。

### 識別您的問題是否相關

若要識別您遇到的問題是否為本文所述的問題，請執行以下資料庫查詢：

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

如果查詢傳回表格，其中 `update_exists` 值為「0」，則為的無效連結 `staging_update` 表格存在於您的資料庫中，以及 [解決方案區段](#solution) 有助於解決問題。 以下是查詢結果的範例，包含 `update_exists` 等於「0」的值：

![update_exists_0.png](assets/update_exists_0.png)

如果查詢傳回表格，其中 `update_exists` 值為「1」或空白結果，表示您的問題與中繼更新無關。 以下是查詢結果的範例，包含 `update_exists` 等於「1」的值：

![updates_exist_1.png](assets/updates_exist_1.png)

在此案例中，您可能會參考 [Site Down疑難排解員](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) 以取得疑難排解建議。

## 解決方案

1. 執行以下查詢以刪除指向的無效連結 `staging_update` 表格：

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. 等待cron工作執行（若設定正確，最多五分鐘後執行），或若未設定cron，則手動執行。

在修正無效連結後，應立即解決問題。 如果問題仍然存在， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
