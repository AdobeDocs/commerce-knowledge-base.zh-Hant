---
title: Adobe Commerce上的資料庫儲存疑難排解員
description: 本文是針對Adobe Commerce上遇到資料庫問題的客戶的疑難排解工具。 按一下每個問題以顯示疑難排解員每個步驟的答案。 根據您的症狀和組態，疑難排解人員會說明如何疑難排解資料庫的空間及組態問題。
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Adobe Commerce上的資料庫儲存疑難排解員

本文是針對Adobe Commerce上遇到資料庫問題的客戶的疑難排解工具。 按一下每個問題以顯示疑難排解員每個步驟的答案。 根據您的症狀和組態，疑難排解人員會說明如何疑難排解資料庫的空間及組態問題。

## 步驟1 — 識別有空間問題的目錄 {#step-1}

+++**您是否有 `/tmp` 空間不足造成的問題？**

這可以用一系列症狀來表示，包括 `/tmp` 裝載已滿、網站停止運作，或無法SSH連線至節點。 您可能也會遇到類似以下的錯誤 _裝置沒有剩餘空間(28)_. 針對由下列專案產生的錯誤清單： `/tmp` 填滿，檢閱 [/tmp掛載已滿](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

或者，您是否有 `/data/mysql` 空間不足造成的問題？ 這也可能是由各種症狀所指示，包括網站中斷、客戶無法將產品新增到購物車、資料庫連線失敗和galeria錯誤，例如 _SQLSTATE\[08S01\]：通訊連結失敗：1047 WSREP_. 如需MySQL磁碟空間不足所造成的錯誤清單，請參閱 [雲端基礎結構上的Adobe Commerce上的MySQL磁碟空間不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

如果您不確定是否有磁碟空間問題，以及您是否有New Relic帳戶，請前往 [New Relic基礎架構：監督主機頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). 從那裡，按一下 **儲存** 標籤，變更 **圖表顯示** 從5個結果下拉至20個，並在「已使用磁碟百分比」圖表或表格中尋找高磁碟使用率的表格。 如需詳細步驟，請參閱 [New Relic基礎建設監控>儲存標籤]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)。

如果您有上述任何症狀，請檢查索引節點的狀態，以確定這不是檔案編號問題所造成。 若要這樣做，請在CLI/終端機中執行以下命令：\
`df -ih`

IUse% > 90%嗎？

a.是 — 這是檔案過多所導致。 檢閱在中安全移除檔案的步驟 [當磁碟空間用完時，安全地刪除檔案；雲端基礎結構上的Adobe Commerce](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). 繼續前往 [步驟2](#step-2) 完成這些步驟之後。 如果您想要求更多空間， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 檢查空格。 執行 `df -h | grep mysql` 然後 `df -h | grep tmp` 在CLI/終端機中檢查磁碟空間使用狀況 `/tmp` 和 `/data/mysql` 目錄。 繼續前往 [步驟3](#step-3).

+++

## 步驟2 — 檢查磁碟空間 {#step-2}

+++**檢查磁碟空間使用狀況？**

減少檔案數後，請執行 `df -h | grep mysql` 然後 `df -h | grep tmp` 在CLI/終端機中檢查磁碟空間使用量 `/tmp` 和 `/data/mysql`. 大於70%用於 `/tmp` 或 `/data/mysql`？

a.是 — 繼續至 [步驟3](#step-3).
b.否 — 查詢可能會耗儘可用的儲存空間。 這可能會造成節點當機，造成查詢終止並移除 `tmp` 檔案。 檢查 `SHOW PROCESSLIST;` 在MySQL CLI中尋找可能導致問題的查詢。 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求更多空間。

+++

## 步驟3 — 識別高使用率的目錄 {#step-3}

+++**哪個目錄的使用率超過70%？**

哪個目錄的使用率超過70%？ `/tmp` 或 `/data/mysql`？

>[!NOTE]
>
>根據預設，資料庫tmpdir會寫入 `/tmp`. 若要檢查您的資料庫組態是否仍維持此預設值，請在MySQL CLI中執行下列命令： `SHOW VARIABLES LIKE "TMPDIR";` 如果資料庫tmpdir仍在寫入 `/tmp`，您將會看到 `/tmp` 在值欄中。

答： `/tmp`  — 繼續前往 [步驟4](#step-4). \
b. `/data/mysql`  — 繼續前往 [步驟5](#step-5).

+++

## 步驟4 — 疑難排解/tmp掛載已滿 {#step-4}

+++**疑難排解/tmp掛載已滿**

[疑難排解Adobe Commerce的/tmp掛載已滿](/help/troubleshooting/miscellaneous/tmp-mount-full.md)，向下捲動文章，然後嘗試解決方案和最佳實務。 然後執行 `df -h | grep mysql` 然後 `df -h | grep tmp` 在CLI/終端機中檢查磁碟空間使用量 `/tmp` 和 `/data/mysql` 目錄\
  &lt;使用70%？

>[!NOTE]
>
>中的解決方案 [疑難排解Adobe Commerce的/tmp掛載已滿](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 是專為未變更資料庫tmpdir （預設會寫入）之變數的商家所設計 `/tmp`. 如果您已變更tmpdir值，請依照以下說明操作： [疑難排解Adobe Commerce的/tmp掛載已滿](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 不會有所幫助。

答：是 — 您已解決問題。 \
b.否 —  [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求更多空間。

+++

## 步驟5 — 檢查預設 {#step-5}

+++**檢查預設**

您的資料庫組態可能不再為原始預設值。 在MySQL CLI中執行以尋找資料庫tmpdir設定： `SELECT @@DATADIR;`. 如果 `/data/mysql/` 已輸出，資料庫tmpdir正在寫入 `/data/mysql/`. 請依照中的步驟增加此目錄中的空間 [我們的雲端基礎結構上Adobe Commerce的MySQL磁碟空間不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). 然後執行 `df -h | grep mysql` 然後 `df -h | grep tmp` 在CLI/終端機中檢查磁碟空間使用量 `/data/mysql` 和 `/tmp`.\
  &lt;使用70%？

答：是 — 您已解決問題。 \
b.否 —  [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求更多空間。

+++

[回到步驟1](#step-1)
