---
title: 匯出的產品.csv檔案不會出現
description: 本文修正您在Commerce管理員中嘗試將產品匯出至.csv檔案，但檔案未顯示的問題。
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: 465eb89cf5c5169b0b459ab7e6bdcbd418781093
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# 匯出的產品.csv檔案不會出現

本文修正您在Commerce管理員中嘗試將產品匯出至.csv檔案，但檔案未顯示的問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 問題

<u>要再現的步驟</u>

先決條件：此 **將秘密金鑰新增至URL** 選項已設為 *是*. 此選項是在Commerce管理員的底下設定。 **商店** > **設定** > **進階** > **管理員** > **安全性**.

1. 在「管理員」中，導覽至 **系統** > **資料傳輸** > **匯出**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. 選取
   * **實體型別**： *產品*
   * **匯出檔案格式**： *CSV*
   * **欄位附件**：保留為未勾選。
1. 按一下 **繼續**.
1. 系統會顯示下列訊息： *「訊息已新增至佇列，請等候儘快取得檔案」*.

<u>預期結果</u>

含有匯出產品的.csv檔案會在幾分鐘後顯示在格線中。

<u>實際結果</u>

含有已匯出產品的.csv檔案在10分鐘或更長時間後不會顯示在格線中。

## 原因

Adobe Commerce應用程式元件2.3.2版中的匯出功能已知問題。

## 解決方案

此問題有兩種可能的解決方案：

* 停用「將秘密金鑰新增至URL」選項。
* 執行 `bin/magento queue:consumers:start exportProcessor` 命令以手動執行，並選擇性地將其設定為由cron執行。

請參閱以下段落中兩個選項的詳細資料。

### 停用「將秘密金鑰新增至URL」選項

1. 在「管理員」中，導覽至 **商店** > **設定** > **進階** > **管理員** > **安全性**.
1. 設定 **將秘密金鑰新增至URL** 選項至 *不適用。*
1. 按一下 **儲存設定**.
1. 清除下的快取 **系統** > **工具** > **快取管理** 或透過執行    ```bash    bin/magento cache:clean``` 或Admin中的。

### 手動執行匯出命令，並選擇性地將其新增為cron作業

若要取得匯出檔案，請執行 `bin/magento queue:consumers:start exportProcessor` 命令。 執行此動作後，檔案應該會顯示在格線中。


若要選擇性地將流程新增為cron作業，您必須新增 `CRON_CONSUMERS` 變數至 `.magento.env.yaml` 檔案。

#### 將程式新增為cron工作（選用）

1. 確認您的cron已設定完畢。 另請參閱 [設定cron工作](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) 以取得詳細資訊。
1. 執行以下命令，傳回訊息佇列取用者的清單：     `./bin/magento queue:consumers:list`
1. 將下列專案新增至 `.magento.env.yaml` 根應用程式目錄中的檔案，並包含您要新增的取用者。 例如，以下是匯出處理所需的消費者：

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   然後推送此更新檔案並重新部署您的環境。 另請參閱 [新增自訂cron工作至您的專案](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) （位於我們的開發人員檔案中）。

>[!NOTE]
>
>如果您找不到 `.magento.env.yaml` 檔案時，如果您認為該檔案已刪除，則必須建立新的 `.magento.env.yaml`. 一開始可能是空的，您可以視需要在其中新增資訊。 請參考下列文章： [設定用於部署的環境變數](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) 和 [環境變數](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) （位於我們的開發人員檔案中）。

>[!NOTE]
>
>在雲端基礎結構Pro專案的Adobe Commerce上， [auto-crons功能](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) 您必須在雲端基礎結構上的Adobe Commerce上啟用，才能使用將自訂cron工作新增到測試和生產環境 `.magento.app.yaml`. 如果未啟用此功能， [建立支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，為您新增工作。
