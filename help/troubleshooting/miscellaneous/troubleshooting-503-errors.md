---
title: 疑難排解503錯誤，因必須變更預設清漆設定
description: 本文提供解決方案，用於疑難排解503錯誤，該錯誤是由某些清漆快取預設值不足以供您的存放區使用所導致。
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 疑難排解503錯誤，因必須變更預設清漆設定

本文提供解決方案，用於疑難排解503錯誤，該錯誤是由某些清漆快取預設值不足以供您的存放區使用所導致。

## 問題

如果Adobe Commerce使用的快取標籤長度超過Varnish預設的8192位元組，您會在瀏覽器中看到HTTP 503 （後端擷取失敗）錯誤。 錯誤可能會顯示類似下列的內容： *&quot;錯誤503後端擷取失敗。 後端擷取失敗&quot;*

## 解決方案

若要解決此問題，請增加Varnish組態檔中`http_resp_hdr_len`引數的預設值。 `http_resp_hdr_len`引數指定最大標頭長度&#x200B;*在*&#x200B;之內，總預設回應大小為32768個位元組。

>[!NOTE]
>
>如果`http_resp_hdr_len`值超過32K，您也必須使用`http_resp_size`引數增加預設回應大小。

1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟您的「消失」設定檔：
   * CentOS 6： `/etc/sysconfig/varnish`
   * CentOS 7： `/etc/varnish/varnish.params`
   * Debian： `/etc/default/varnish`
   * Ubuntu： `/etc/default/varnish`
1. 搜尋`http_resp_hdr_len`引數。
1. 如果引數不存在，請在`thread_pool_max`之後新增。
1. 將`http_resp_hdr_len`設為等於最大類別的產品計數乘以21的值。 （每個產品標籤的長度約為21個字元。）    例如，如果最大類別有3,000種產品，則將該值設為65536個位元組應該有效。    例如：    ```conf    -p http_resp_hdr_len=65536 \    ```
1. 將`http_resp_size`設定為符合增加之回應標頭長度的值。    例如，使用增加的標頭長度和預設回應大小的總和是良好的起點(例如，65536 + 32768 = 98304)： `-p http_resp_size=98304`。 程式碼片段如下：

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## 健康情況檢查逾時 {#health-check-timeouts}

如果您在Varnish設定為快取應用程式時停用快取，並且當Adobe Commerce處於開發人員模式時，則可能無法登入管理員。

發生此狀況是因為預設健康狀態檢查的`timeout`值為2秒。 健康情況檢查可能需要超過2秒的時間來收集和合併每個健康情況檢查要求的資訊。 如果10次健康情況檢查中有6次發生這種情況，則會將Adobe Commerce伺服器視為不健康。 當伺服器狀況不良時，清漆會提供過時內容。

由於管理員是透過Varnish存取，因此您無法登入管理員以啟用快取(除非Adobe Commerce再次恢復正常)。 不過，您可以使用下列命令來啟用快取：

```bash
$ bin/magento cache:enable
```

如需使用命令列的詳細資訊，請參閱[開始使用命令列組態](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli)。
