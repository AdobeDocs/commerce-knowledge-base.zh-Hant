---
title: Adobe Commerce上的資料庫儲存疑難排解員
description: 本文是針對Adobe Commerce上遇到資料庫問題的客戶的疑難排解工具。 按一下每個問題以顯示疑難排解員每個步驟的答案。 根據您的症狀和組態，疑難排解人員會說明如何疑難排解資料庫的空間及組態問題。
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Adobe Commerce上的資料庫儲存疑難排解員

本文是針對Adobe Commerce上遇到資料庫問題的客戶的疑難排解工具。 按一下每個問題以顯示疑難排解員每個步驟的答案。 根據您的症狀和組態，疑難排解人員會說明如何疑難排解資料庫的空間及組態問題。

## 步驟1 — 識別有空間問題的目錄 {#step-1}

+++**您是否有因空間不足所導致的`/tmp`問題？**

這可以用一系列症狀來表示，包括`/tmp`掛載已滿、網站停止運作，或無法透過SSH連線至節點。 您也可能遇到錯誤，例如&#x200B;_裝置上已無空間(28)_。 如需因`/tmp`已滿而產生的錯誤清單，請檢閱[/tmp裝載已滿](/help/troubleshooting/miscellaneous/tmp-mount-full.md)。

或您是否有因空間不足而導致的`/data/mysql`問題？ 這也可能是由各種症狀所指示，包括網站中斷、客戶無法將產品新增到購物車、連線到資料庫失敗以及Galeria錯誤，例如&#x200B;_SQLSTATE\[08S01\]：通訊連結失敗： 1047 WSREP_。 如需[!DNL MySQL]磁碟空間不足所造成的錯誤清單，請參閱Adobe Commerce上雲端基礎結構[&#128279;](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)上的[!DNL MySQL] 磁碟空間不足。

如果您不確定是否有磁碟空間問題，且您有New Relic帳戶，請移至[New Relic基礎架構監視主機頁面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)。 從那裡，按一下&#x200B;**儲存空間**&#x200B;索引標籤，將&#x200B;**圖表顯示**&#x200B;下拉式清單從5個結果變更為20個結果，並在[已使用磁碟百分比]圖表或表格中尋找高磁碟使用率的表格。 如需詳細步驟，請參閱[New Relic基礎架構監控>儲存標籤]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)。

如果您有上述任何症狀，請檢查索引節點的狀態，以確定這不是檔案編號問題所造成。 若要這樣做，請在CLI/終端機中執行以下命令：\
`df -ih`

IUse% > 90%嗎？

a.是 — 這是檔案過多所導致。 檢閱在[當磁碟空間不足時安全地刪除檔案的步驟，雲端基礎結構上的Adobe Commerce](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26889)。 完成這些步驟後，請繼續進行[步驟2](#step-2)。 如果您想要要求更多空間，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 檢查空格。 在CLI/終端機中執行`df -h | grep mysql`，然後執行`df -h | grep tmp`，以檢查`/tmp`和`/data/mysql`目錄中的磁碟空間使用量。 繼續進行[步驟3](#step-3)。

+++

## 步驟2 — 檢查磁碟空間 {#step-2}

+++**檢查磁碟空間使用量？**

一旦您減少了檔案數目，請在CLI/終端機中執行`df -h | grep mysql`然後執行`df -h | grep tmp`，以檢查`/tmp`和`/data/mysql`中的磁碟空間使用量。 `/tmp`或`/data/mysql`的使用率是否超過70%？

a.是 — 繼續進行[步驟3](#step-3)。
b.否 — 查詢可能會耗儘可用的儲存空間。 這可能會造成節點當機，導致查詢停止並移除`tmp`個檔案。 檢查[!DNL MySQL] CLI中`SHOW PROCESSLIST;`的輸出是否有可能是問題原因的查詢。 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求更多空間。

+++

## 步驟3 — 識別高使用率的目錄 {#step-3}

+++**哪個目錄的使用率超過70%？**

哪個目錄的使用率超過70%？ `/tmp`或`/data/mysql`？

>[!NOTE]
>
>根據預設，資料庫tmpdir會寫入`/tmp`。 若要檢查您的資料庫組態是否仍維持此預設值，請在[!DNL MySQL] CLI中執行下列命令： `SHOW VARIABLES LIKE "TMPDIR";`如果資料庫tmpdir仍在寫入`/tmp`，您將會在[值]欄中看到`/tmp`。

a. `/tmp` — 繼續進行[步驟4](#step-4)。 \
b. `/data/mysql` — 繼續進行[步驟5](#step-5)。

+++

## 步驟4 — 疑難排解/tmp掛載已滿 {#step-4}

+++**疑難排解/tmp掛載已滿**

[針對Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)進行/tmp掛載完整疑難排解，向下捲動文章，然後嘗試解決方案和最佳實務。 接著在CLI/終端機中執行`df -h | grep mysql`再執行`df -h | grep tmp`，以檢查`/tmp`和`/data/mysql`目錄中的磁碟空間使用量\
  &lt;使用70%？

>[!NOTE]
>
>[疑難排解/tmp mount full for Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)中的解決方案是專為未變更資料庫tmpdir變數的商戶所設計，預設會寫入`/tmp`。 如果您已變更tmpdir值，[疑難排解/tmp mount full for Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)中的指示將沒有幫助。

答：是 — 您已解決問題。 \
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求更多空間。

+++

## 步驟5 — 檢查預設 {#step-5}

+++**檢查預設值**

您的資料庫組態可能不再為原始預設值。 在[!DNL MySQL] CLI `SELECT @@DATADIR;`中執行以尋找資料庫tmpdir設定。 如果輸出`/data/mysql/`，資料庫tmpdir現在正在寫入`/data/mysql/`。 請嘗試依照雲端基礎結構上Adobe Commerce上[[!DNL MySQL] 磁碟空間不足的步驟，增加此目錄中的空間](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)。 接著在CLI/終端機中執行`df -h | grep mysql`再執行`df -h | grep tmp`，以檢查`/data/mysql`和`/tmp`中的磁碟空間使用量。\
  &lt;使用70%？

答：是 — 您已解決問題。 \
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求更多空間。

+++

[回到步驟1](#step-1)

## 相關閱讀

* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
