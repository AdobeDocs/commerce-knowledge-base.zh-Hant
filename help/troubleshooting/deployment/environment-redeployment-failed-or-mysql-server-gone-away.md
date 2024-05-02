---
title: 環境重新部署失敗或MySQL伺服器消失
description: 本文提供Adobe Commerce （所有部署方法）問題的解決方案，這類問題會導致MySQL配置的空間中斷而導致部署停滯或資料庫連線錯誤。
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 環境重新部署失敗或MySQL伺服器消失

本文提供Adobe Commerce （所有部署方法）問題的解決方案，這類問題會導致MySQL配置的空間中斷而導致部署停滯或資料庫連線錯誤。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce （所有版本）

## 問題

* 部署程式失敗，在部署記錄（命令列和UI記錄）中出現以下錯誤：  ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce以503錯誤回應，而以下錯誤訊息會顯示於應用程式記錄中：    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    連線到MySQL伺服器時，會出現下列錯誤：    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## 原因

問題最可能的原因是MySQL資料庫配置的空間太低。 若要確定情況確實如此，請依照進一步說明檢查MySQL的可用空間。

### 檢查是否有足夠的空間可供MySQL使用

針對雲端基礎結構上的所有Adobe Commerce入門計畫架構環境，以及 [整合環境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 雲端基礎結構專業版的Adobe Commerce計畫架構， [SSH連線至環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) 並執行命令：

```bash
magento-cloud db:size
```

對於Pro架構的測試或生產環境， [SSH連線至環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)，然後執行 `df -h`   `| grep mysql` 命令。 結果將類似於以下內容：

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## 解決方案

### 若要解決此問題，您需要為MySQL分配更多空間。

對於所有入門架構和Pro架構整合環境，這可以在 `.magento/services.yaml` 檔案，透過增加 `mysql: disk:` 引數。 例如：

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

請參閱 [設定MySQL服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html) 文章以供參考。

若要對Pro架構的測試或生產環境進行這些變更，您必須建立 [支援票證](https://support.magento.com). 但是，通常您不必在Pro架構的測試/生產上處理這個問題，因為Adobe Commerce會監視這些引數，並警示您和/或根據合約採取動作。

### 套用變更

一旦您變更 `.magento/services.yaml` 檔案，您必須提交並推送變更以套用。 推送將會觸發部署程式。
