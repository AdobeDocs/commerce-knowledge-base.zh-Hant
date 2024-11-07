---
title: 頂層導覽面板未載入店面
description: 本文提供配置解決方案，解決Edge Side Include (ESI)問題，其中如果使用Varnish進行快取，則店面不會顯示某些頁面的內容（通常是頂端導覽面板）。
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 頂層導覽面板未載入店面

本文提供配置解決方案，解決Edge Side Include (ESI)問題，其中如果使用Varnish進行快取，則店面不會顯示某些頁面的內容（通常是頂端導覽面板）。

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

1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟您的「消失」設定檔。 請參閱開發人員檔案中的[修改Varnish系統組態](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server)，以取得不同作業系統之檔案可能所在位置的資訊。
1. 在`DAEMON_OPTS variable`中，新增`-p feature=+esi_ignore_https`、`-p  feature=+esi_ignore_other_elements`、`-p  feature=+esi_disable_xml_check`。 如下所示：

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. 儲存變更並退出文字編輯器。
1. 在VCL組態檔中，增加下列引數的值以增加回應標頭： `http_resp_hdr_len`、`http_resp_size`、`workspace_backend`。 請確定最後兩個具有類似的值。
1. 當您變更此專案時，必須執行`service varnish restart`才能讓變更生效。

## 相關閱讀

* 在開發人員檔案中[設定Varnish與您的網頁伺服器](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server)。
* [塗漆檔案](https://varnish-cache.org/docs/5.1/reference/index.html)
