---
title: 「E：驗證路由時發生錯誤。在中繼或生產部署期間出現yaml錯誤」
description: 「本文為Adobe Commerce提供雲端基礎結構問題的解決方案，當嘗試將專案部署到中繼或生產環境時，您會收到*"E：驗證路由時發生錯誤.yaml"*錯誤訊息。」
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E：驗證路由時發生錯誤。中繼或生產部署期間發生yaml錯誤

本文提供Adobe Commerce在雲端基礎結構問題上的解決方案，其中您會在嘗試將專案部署到中繼或生產環境時收到&#x200B;*&quot;E：驗證routes.yaml&quot;時發生錯誤*&#x200B;錯誤訊息。

## 受影響的版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

<u>要再現的步驟</u>：

將程式碼推送至測試或生產環境以觸發部署。

<u>預期行為</u>：

部署成功。

<u>實際行為</u>：

會封鎖部署，並在記錄中顯示下列錯誤訊息：

<pre>部署應用程式驗證設定E：驗證routes.yaml時發生錯誤。
已為您的叢集設定下列網域，但並未在routes.yaml檔案中定義路由：

- store1.example.com
- store2.example.com
- test-store.example.com

使用您目前的routes.yaml設定，
  系統不會提供這些網域！

若要繼續，請參閱此處以取得疑難排解的指示：
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## 原因

如果`routes.yaml`檔案中遺漏已新增至專案的任何其他網域的路由設定，則會發生此錯誤。

在自助路由設定的Adobe Commerce自助啟用升級中，我們新增了預先部署檢查，以確保您專案中的所有網域已在`routes.yaml`檔案中設定路由。 如果有任何網域缺少路由設定，則會封鎖部署。

## 解決方案

若要解決封鎖的部署，請使用下列其中一種方法，更新`routes.yaml`檔案以設定錯誤訊息中所列網域的路由：

* 在升級過程中套用Adobe Commerce提供的修補程式。
* 手動將遺失的路由組態新增至`routes.yaml`檔案。

### 方法1：套用Adobe Commerce提供的修補程式

1. 尋找標題為「*為&lt;project\_ID>啟用自助服務功能」的最新Adobe Commerce支援票證。*
1. 依照票證中的指示套用修補程式，以更新雲端環境的路由設定。
1. 提с交並推送變更以重新部署您的專案。

### 方法2：手動新增遺失的路由設定

1. 若要使用相同的路由設定為您專案中的所有網域提供服務，請更新`routes.yaml`檔案，新增預設網域和您專案上所有其他網域的路由範本，如下列範例所示：

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. 提с交並推送您的變更，以重新部署您的專案。

如需更新路由設定的詳細指示，請參閱我們的開發人員檔案中的[Adobe Commerce雲端>設定路由](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html)。

>[!NOTE]
>
>如果您的專案設定指定了不再使用的網域，請儘早完成以下步驟以從專案中移除它們： 1. 提交支援票證，其中包含要從專案環境中移除的網域清單。 2.支援團隊移除網域後，請更新`routes.yaml`檔案以移除對過時網域的任何參照。
