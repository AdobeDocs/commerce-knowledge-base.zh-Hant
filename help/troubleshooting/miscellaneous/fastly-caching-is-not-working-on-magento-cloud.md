---
title: Fastly快取不適用於雲端基礎結構上的Adobe Commerce
description: 本文針對Fastly快取無法在您的網站上運作的問題提供修正。 Fastly是一項CDN和快取服務，包含在Adobe Commerce的雲端基礎結構計畫和實作中。 若要驗證Fastly擴充功能是否正常運作或偵錯Fastly擴充功能，您可以使用curl命令來顯示特定回應標題。 這些回應標頭的值表示Fastly是否已啟用且正常運作。 您可以根據標頭的值和快取行為來進一步調查問題。
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Fastly快取不適用於雲端基礎結構上的Adobe Commerce

本文針對Fastly快取無法在您的網站上運作的問題提供修正。 Fastly是一項CDN和快取服務，包含在Adobe Commerce的雲端基礎結構計畫和實作中。 若要驗證Fastly擴充功能是否正常運作或偵錯Fastly擴充功能，您可以使用curl命令來顯示特定回應標題。 這些回應標頭的值表示Fastly是否已啟用且正常運作。 您可以根據標頭的值和快取行為來進一步調查問題。

此資訊可協助您驗證和測試即時網站和來源伺服器的Fastly標題。

## 受影響的版本

* 雲端基礎結構上的Adobe Commerce
* Fastly 1.2.27及更高版本

## 問題

快取可能無法用於您的即時網站、生產或測試環境。

## 原因

通常，設定、不正確的憑證或不支援的Adobe Commerce擴充功能是Fastly快取無法運作的問題。 如果您設定Fastly不正確，或使用不支援的擴充功能來移除標題，Fastly快取將無法運作。

## 使用命令進行測試並檢查回應標題

### 使用dig命令進行測試

首先，使用dig命令檢查URL的標頭。 在終端機應用程式中，輸入dig `<url>` 以驗證Fastly服務是否顯示在標題中。 如需其他深入測試，請參閱Fastly的 [變更DNS前的測試](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

例如：

* 即時網站： `dig http[s]://<your domain>`
* 分段： `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* 生產： `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### 使用curl命令測試

接下來，使用curl命令來驗證XMagento標籤是否存在以及其他標頭資訊。 「測試」和「生產」的命令格式不同。

如需這些命令的詳細資訊，請在插入時略過Fastly `-H "host:URL"`，取代為連線位置的來源（OneDrive試算表中的CNAME資訊）， `-k` 忽略SSL，並且 `-v` 提供詳細回應。 如果標題正確顯示，請檢查即時網站並再次驗證標題。

* 如果在直接繞過Fastly點選原始伺服器時發生標題問題，則您的程式碼、擴充功能或基礎結構可能會有問題。
* 如果您沒有遇到直接點選原始伺服器的錯誤，但標題缺少透過Fastly點選即時網域，則您可能會有Fastly錯誤。

首先，檢查您的 **即時網站** 以驗證回應標頭。 命令會通過Fastly擴充功能以接收回應。 如果您沒有收到正確的標頭，則應該直接測試原始伺服器。 此命令會傳回 `Fastly-Magento-VCL-Uploaded` 和 `X-Cache` 標頭。

1. 在終端機中，輸入以下命令以測試您的即時網站URL：

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   使用 `--resolve` 只有當您的即時URL未使用DNS設定，而且您沒有設定靜態路由時，才會發生這種情況。 例如：

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. 驗證回應標頭以確保Fastly正常運作。 此命令的輸出類似於curl「暫存和生產」。 例如，您應該會看到此命令傳回的唯一標頭：

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

待測試 **分段** ：

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

待測試 **生產負載平衡器** ：

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

待測試 **生產來源節點** ：

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

直接原始節點：

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

例如，如果您有公用URL www.mymagento.biz，請輸入類似下列的命令以測試生產網站：

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### 檢查回應標頭

* 檢查傳回的回應標題和值：
* Fastly-Magento-VCL-Uploaded應該存在
* 應該會傳回XMagento標籤
* Fastly-Module-Enabled應為Yes或Fastly擴充功能版本號碼
* X-Cache應為HIT或HIT， HIT
* x-cache-hits應為1,1
* Cache-Control： max-age應大於0
* Pragma應為快取

以下範例顯示Pragma、X-Module-Tags和Fastly-Module-Enabled的正確Magento。

curl指令的輸出可能會很長。 以下是僅供摘要參考的資訊：

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## 解析

### Fastly-Module-Enabled不存在

如果您在回應標題中未收到Fastly-Module-Enabled的「是」，則需要驗證Fasty模組是否已安裝及選取。

若要驗證已在測試和生產環境中啟用Fastly，請在Commerce管理員中檢查每個環境的設定：

1. 使用包含/admin的URL （或已變更的管理員URL）登入Admin Console以進行測試和生產。
1. 導覽至「商店>組態>進階>系統」。 捲動並按一下完整頁面快取。
1. 確認已選取Fastly CDN。
1. 按一下「Fastly設定」。 確保已輸入Fastly服務ID和Fastly API權杖（您的Fastly認證）。 確認您為測試環境和生產環境輸入的認證正確無誤。 按一下「測試認證」以取得協助。
1. 編輯您的composer.json，並確保Fasty模組包含在版本中。 此檔案已列出所有模組及其版本。

   * 在「必要」區段中，您應該有「fastly/magento2」： `<version number>`
   * 在「存放庫」區段中，您應該有：

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. 如果您使用「組態管理」，則應該要有組態檔。 編輯app/etc/config.app.php (2.0， 2.1)或app/etc/config.php (2.2)檔案，並確定設定 `'Fastly_Cdn' => 1` 是正確的。 設定不應為 `'Fastly_Cdn' => 0` （表示已停用）。如果您已啟用Fastly，請刪除設定檔並執行bin/magento magento-cloud：scd-dump命令以進行更新。 如需此檔案的逐步說明，請參閱 [管理系統特定設定的範例](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) 在設定指南中。

如果未安裝模組，您必須將安裝在 [整合環境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 分支並部署到中繼和生產環境。 另請參閱 [設定Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 以取得雲端基礎結構指南中的Commerce指示。

### Fastly-Magento-VCL-Uploaded不存在

在安裝與設定期間，您應該已上傳Fastly VCL。 這些是Fastly模組提供的基本VCL片段，不是您建立的自訂VCL片段。 如需指示，請參閱 [上傳Fastly VCL片段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) 雲端基礎結構指南中的Commerce 。

### X-Cache包含MISS

如果X-Cache為HIT、MISS或MISS、MISS，請再次輸入相同的curl命令，以確定最近沒有從快取中收回頁面。

如果您得到相同的結果，請使用curl命令並驗證回應標頭：

* Pragma是快取
* XMagento標籤已存在
* Cache-Control： max-age大於0

如果問題仍然存在，其他擴充功能可能會重設這些標題。 在測試中重複以下程式以停用擴充功能，找出導致問題的擴充功能。 找出導致問題的擴充功能後，您需要在「生產」中停用擴充功能。

1. 若要停用擴充功能，請依照中提供的步驟操作。 [管理擴充功能](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) 雲端基礎結構指南上的Commerce的區段。
1. 停用擴充功能後，請前往 **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. 按一下 **[!UICONTROL Flush Magento Cache]**.
1. 現在一次啟用一個擴充功能，以儲存設定並排清快取。
1. 請嘗試curl命令並驗證回應標頭。
1. 重複步驟4和5以啟用和測試curl指令。 當Fastly標題不再顯示時，您發現擴充功能造成Fastly問題。

當您隔離重設Fastly標題的擴充功能時，請聯絡擴充功能開發人員以取得其他協助。 我們無法提供協力廠商擴充功能開發人員的修正或更新以搭配Fastly快取使用。

## 如需詳細資訊，請參閱我們的開發人員檔案：

* [關於Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [設定Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [自訂Fastly VCL片段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
