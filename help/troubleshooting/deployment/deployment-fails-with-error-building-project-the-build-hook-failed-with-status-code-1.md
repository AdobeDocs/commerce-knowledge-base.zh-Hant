---
title: 「部署失敗並出現「建置專案錯誤：建置掛接失敗，狀態代碼為1」」
description: 「本文討論Adobe Commerce雲端基礎結構問題的原因和解決方案，該問題的部署流程的建置階段失敗，錯誤訊息摘要為：*「錯誤建置專案：建置掛接失敗，狀態碼為1」*。」
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# 部署失敗並顯示「建置專案時發生錯誤：建置掛接失敗，狀態碼為1」

本文會討論Adobe Commerce雲端基礎結構問題的原因和解決方案，其中部署流程的建置階段失敗，錯誤訊息摘要為： *「建置專案時發生錯誤：建置掛接失敗，狀態碼為1」*.

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

<u>要再現的步驟</u>：

手動觸發部署，或透過執行環境的合併、推播或同步化來觸發。

<u>預期結果</u>：

已成功完成部署。

<u>實際結果</u>：

1. 建置階段會失敗，且整個部署流程會卡住。
1. 在部署錯誤記錄檔中，錯誤訊息的結尾是： *「建置專案時發生錯誤：建置掛接失敗，狀態碼為1。 已中止的建置」。*

## 原因

環境建置失敗的原因有很多。 通常，在部署記錄中，您會看到一則長錯誤訊息，其中第一部分將更具體說明原因，而結論將為 *「建置專案時發生錯誤：建置掛接失敗，狀態碼為1。 已中止的建置」。*

進一步瞭解第一個問題特定部分，將有助於您識別問題。 以下是最常見的部分，下一節會提供解決方案：

* 沒有可用的儲存空間。
* ECE-Tools設定不正確。
* 您嘗試套用的修補程式與您的Adobe Commerce版本不相容，或與套用的其他修補程式或您的自訂內容發生衝突。
* 自訂模組程式碼的問題導致無法成功建置。

## 解決方案

* 檢查以確保有足夠的儲存空間。 有關如何檢查可用空間的資訊，請參閱 [使用CLI檢查雲端環境的磁碟空間](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) 文章。 您可以考慮清除記錄目錄和/或增加磁碟空間。
* 請確定ECE-Tools已正確設定。
* 檢查問題是否由修補程式造成。 解決衝突或連絡人 [Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). 如需詳細資訊，請參閱下文。
* 檢查問題是否起因於自訂擴充功能。 解決衝突或聯絡擴充功能開發人員以取得解決方案。

以下段落提供一些更多詳細資訊。

### 清理記錄檔及/或增加空間

要考慮進行清理的目錄：

* `var/log`
* `var/report`
* `var/debug/`
* `var`

如果您使用Adobe Commerce雲端基礎結構入門計畫架構，如需有關如何增加磁碟空間的詳細資訊，請參閱 [增加雲端整合環境的磁碟空間](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). 相同的指示可用於在雲端基礎結構上增加Adobe Commerce的空間Pro規劃架構整合環境。 對於Pro Production/Staging，您需要將票證歸檔至 [Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，並要求增加磁碟空間。 但受到Platform監視。 但是，通常您不必在Pro架構的測試/生產上處理這個問題，因為Adobe Commerce會監視這些引數，並警示您和/或根據合約採取動作。

### 請確定ECE-tools設定正確

1. 確定已在中正確定義組建鉤點 `magento.app.yaml` 檔案。 如果您使用Adobe Commerce 2.2.X，建置勾點應依下列方式定義：

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   使用 [升級至ece-tools](https://devdocs.magento.com/guides/v2.3/cloud/project/ece-tools-upgrade-project.html) 文章以供參考。

1. 請確定ECE-tools套件存在於 `composer.lock` 檔案，方法是執行下列命令：    <pre><code class="language-bash">grep `<code class="language-yaml">&quot;name&quot;： &quot;magento/ece-tools&quot;</code>&#39; composer.lock</code></pre>    若已指定，回應會類似於以下範例：    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

請參閱 [升級至ece-tools](https://devdocs.magento.com/guides/v2.3/cloud/project/ece-tools-upgrade-project.html) 文章以供參考。

### 此修補程式是否造成問題？

如果套用的修補程式導致環境無法成功建置，您會在部署記錄檔中看到類似下列的內容：

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

這些錯誤訊息表示您嘗試套用的修補程式是針對其他Adobe Commerce版本建立的，或與您的自訂專案或先前套用的修補程式衝突。 嘗試解決衝突或連絡 [Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### 擴充功能是否造成問題？

如果自訂擴充功能導致環境無法成功建置，您會在部署記錄中看到自訂模組名稱，以及此模組造成的特定衝突。 解決衝突或聯絡擴充功能開發人員以取得解決方案。

### 確定已套用變更

提交並推送您的變更。 這將會自動觸發部署。
