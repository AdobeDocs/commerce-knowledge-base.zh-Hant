---
title: 404執行型錄價格規則排程更新後，商店前端發生錯誤
description: 本文提供修補程式和必要步驟，以修正目錄價格規則更新建立且稍後編輯其開始時間後，與在所有商店正面頁面上取得404錯誤相關的已知Adobe Commerce 2.2.1問題。 若要修正問題，您必須套用修補程式。
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404執行型錄價格規則排程更新後，商店前端發生錯誤

本文提供修補程式和必要步驟，以修正目錄價格規則更新建立且稍後編輯其開始時間後，與在所有商店正面頁面上取得404錯誤相關的已知Adobe Commerce 2.2.1問題。 若要修正問題，您必須套用修補程式。

## 問題

店面頁面無法使用，返回404錯誤。 若此更新的開始日期是在初始建立後進行編輯，則問題會在使用中型錄價格規則更新到期後出現。

<u>要再現的步驟</u>：

1. 在「Commerce管理員」中，建立「 」下的新「目錄價格規則」 **行銷** > **促銷活動** > **目錄價格規則**.
1. 在 **目錄價格規則** 格點，按一下 **編輯，** 排程新的更新並設定 **狀態** 至 *作用中。*
1. 瀏覽至 **內容** > **內容分段** > **控制面板。**
1. 選取最近建立的更新並變更其開始時間。
1. 儲存變更。

<u>預期結果</u> ：

當「更新」開始日期生效時，型錄價格規則即會成功套用。

<u>實際結果</u> ：

當更新開始日期生效時，店面上的所有目錄和產品將變為無法使用，並傳回404錯誤。

## 解決方案

若要還原目錄頁面，並完全使用目錄價格規則更新功能，您必須安裝修正程式、手動刪除規則並刪除管理員中的規則，以及修正資料庫中的無效連結。 您也需要重新建立型錄價格規則。

以下是所需步驟的詳細說明：

1. [套用修補程式](#patch).
1. 在「Commerce管理員」中，刪除與問題（其開始時間已更新）相關的目錄價格規則。 若要這麼做，請開啟底下的規則頁面 **行銷** > **促銷活動** > **目錄價格規則**，然後按一下 **刪除規則**.
1. 存取資料庫手動從刪除相關記錄 `catalogrule` 表格。
1. 修正資料庫中的無效連結。 請參閱 [相關段落](#fix_links) 以取得詳細資訊。
1. 在「Commerce管理員」中的 **行銷**，前往 **促銷活動** > **目錄價格規則**，並使用所需的設定建立新規則。
1. 清除下的瀏覽器快取 **系統** > **快取管理**.
1. 請確定cron作業已正確設定，並且可以成功執行。

## 修補 {#patch}

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce 2.2.1

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.2.0 - 2.2.4
* Adobe Commerce內部部署2.2.0和2.2.2 - 2.2.4

## 如何套用修補程式

如需指示，請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中。

## 修正資料庫中暫存的無效連結 {#fix_links}

>[!WARNING]
>
>我們強烈建議在任何資料庫操作前先建立資料庫備份。 我們也建議先在開發環境中測試查詢。

執行以下步驟來修正含有無效連結的列 `staging_update` 表格。

1. 檢查無效的連結 `staging_update` 表格存在於 `flag` 表格。 這些是記錄 `flag_code=staging`.
1. 從識別無效的版本 `flag` 使用下列查詢的表格：

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. 從 `staging_update` 表格中，選取小於目前（無效）版本的現有版本，然後取得傳回兩個數字的版本值。 您採取此方式（而非前一個版本）可避免前一個版本是 `staging_update` 可以套用的表格，我們仍需要重新套用它。

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   您收到的回應版本是您的有效版本 `id`.

1. 對於包含無效連結的列 `flag` 表格，設定 `flag_data` 值至包含有效版本ID的資料。 這有助於儲存重新索引步驟的效能，並允許避免重新索引所有實體。

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>範例：</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## 附加的檔案
