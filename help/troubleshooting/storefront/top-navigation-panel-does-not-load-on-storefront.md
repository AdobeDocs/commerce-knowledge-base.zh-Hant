---
title: 頂層導覽面板未載入店面
description: 本文提供Varnish Edge Side Include (ESI)問題的設定解決方案，其中如果使用Varnish進行快取，則某些頁面的內容（通常是頂端導覽面板）不會顯示在店面上。
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 頂層導覽面板未載入店面

本文提供Varnish Edge Side Include (ESI)問題的設定解決方案，其中如果使用Varnish進行快取，則某些頁面的內容（通常是頂端導覽面板）不會顯示在店面上。

## 受影響的產品和版本

* Adobe Commerce 2.X.X
* 所有光澤處理版本

## 問題

<u>必要條件</u>：

為您的Adobe Commerce商店安裝及設定清漆。

<u>要再現的步驟</u>：

1. 前往店面。
1. 瀏覽商店頁面。

<u>預期結果</u>：

所有內容和所有頁面區塊皆已成功載入。

<u>實際結果</u>：

請注意，部分內容區塊（例如具有類別的頂端導覽面板）未載入。 改為顯示空白。

## 原因

此問題的可能原因如下：

* ESI包含標籤是以HTTPS存取通訊協定產生，而Varnish只能搭配HTTP使用。
* 清漆不會處理JSON內的ESI。
* 回應標頭對於Varnish太大；它無法處理它們。

## 解決方案

若要解決問題，您需要執行額外的Varnish設定，並重新啟動Varnish。

1. 作為使用者，具有 `root` 許可權，在文字編輯器中開啟您的「消失」設定檔。 請參閱 [修改Varnish系統設定](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) 開發人員檔案中，取得此檔案可能位於不同作業系統哪個位置的資訊。
1. 在 `DAEMON_OPTS variable`，新增 `-p feature=+esi_ignore_https`， `-p  feature=+esi_ignore_other_elements`， `-p  feature=+esi_disable_xml_check`. 如下所示：

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. 儲存變更並退出文字編輯器。
1. 在VCL組態檔案中，增加下列引數的值以增加回應標頭： `http_resp_hdr_len`， `http_resp_size`， `workspace_backend`. 請確定最後兩個具有類似的值。
1. 當您變更此專案時，您需要執行 `service varnish restart` 以使變更生效。

## 相關閱讀

* [設定Varnish與您的網頁伺服器](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) （位於我們的開發人員檔案中）。
* [塗漆檔案](https://varnish-cache.org/docs/5.1/reference/index.html)
