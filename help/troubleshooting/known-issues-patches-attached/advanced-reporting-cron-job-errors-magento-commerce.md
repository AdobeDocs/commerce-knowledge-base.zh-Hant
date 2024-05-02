---
title: 進階報告cron工作錯誤Adobe Commerce
description: 本文提供Adobe Commerce中進階報告cron作業問題的修補程式，若客戶嘗試存取進階報告，可能會導致404錯誤。
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 進階報告cron工作錯誤Adobe Commerce

本文提供Adobe Commerce中進階報告cron作業問題的修補程式，若客戶嘗試存取進階報告，可能會導致404錯誤。

## 受影響的產品和版本

Adobe Commerce （所有部署選項） 2.3.x

## 問題

客戶嘗試存取進階報告時收到404錯誤，且關聯的記錄中有錯誤 `analytics_collect_data job` .

## 相容的Magento版本：

修補程式與下列Adobe Commerce版本相容（但可能無法解決問題）：

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)：Adobe Commerce （所有部署選項） 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)：Adobe Commerce （所有部署選項） 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)：Adobe Commerce （所有部署選項） 2.3.0

## **解決方案**

若要修正此問題，請套用本文附加的相關修補程式。 若要下載，請按一下下列連結：

* 下載 [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* 下載 [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* 下載 [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

若要檢查要使用的修正程式：

<ol><li>使用下列命令檢閱記錄檔：<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>根據您看到的錯誤，使用下表中的資訊選取修正程式。<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>錯誤</p>
</td>
<td class="wysiwyg-text-align-center">修補</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL：執行cron作業時發生錯誤{"exception"："[object] (RuntimeException(code： 0)：在/srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php：327執行cron作業時發生錯誤，TypeError(code： 0)： substr_count()預期引數1為字串，在/srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php：106)"}指定為空[]</pre>或<pre>report.ERROR： Cron作業analytics_collect_data有錯誤： substr_count()預期引數1為字串，但指定null。 統計資料： {"sum"：0，"count"：1，"realmem"：0，"emalloc"：0，"realmem_start"：224919552，"emalloc_start"：216398384}
  [] []</pre>
<p> </p>
</td>
<td>套用<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>，請清除快取並等待24小時，讓工作再次執行，然後再試一次。</td>
</tr>
<tr>
<td>
<p><em>無法開啟檔案/tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/.../tmp/.../</em></p>
</td>
<td>套用<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>，請清除快取並等待24小時，讓工作再次執行，然後再試一次。</td>
</tr>
<tr>
<td><em>密碼無效</em></td>
<td>套用<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>，請清除快取並等待24小時，讓工作再次執行，然後再試一次。</td>
</tr>
</tbody>
</table>
</li></ol>

## 如何套用修補程式

解壓縮檔案並遵循中的指示 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## 相關閱讀

[無法刪除檔案。 警告！unlink：管理員沒有這類檔案或目錄錯誤](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
