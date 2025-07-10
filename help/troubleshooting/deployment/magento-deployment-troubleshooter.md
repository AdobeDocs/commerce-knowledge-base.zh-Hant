---
title: Adobe Commerce部署疑難排解員
description: Adobe Commerce上的停滯部署和失敗部署可以使用Deployment Troubleshooter工具來解決。 按一下每個問題以顯示疑難排解員每個步驟的答案。
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: d2c37f4465d5ba4f4b4878eae292fa805d1dc45b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Adobe Commerce部署疑難排解員

Adobe Commerce上的停滯部署和失敗部署可以使用Deployment Troubleshooter工具來解決。 按一下每個問題以顯示疑難排解員每個步驟的答案。

## 步驟1 — 確認服務執行中 {#step-1}

+++**雲端基礎結構服務上的Adobe Commerce是否正常運作？**

停滯部署 — 雲端基礎結構服務上的Adobe Commerce是否正常運作？ 檢查[Adobe Commerce Cloud](https://status.adobe.com/products/3350/)。

a.是 — 繼續進行[步驟2](#step-2)。\
b.否 — 維護或全球中斷。 檢查估計持續時間和更新。

+++

## 步驟2 — 檢查其他環境中的部署 {#step-2}

+++**其他環境中是否有部署會封鎖現有環境中的部署？**

若要取得進行中活動的清單，請使用magento-cloud CLI執行以下命令（如果您只新增到一個雲端專案）。 **注意**：請檢查您是否使用最新版的magento-cloud CLI。 如需相關步驟，請參閱Commerce on Cloud Infrastructure指南中的[更新CLI](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview)。

```bash
magento-cloud --state=in_progress
```

若要取得進行中活動的清單，請使用magento-cloud CLI執行以下命令（如果您已新增至多個專案）：

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

若要尋找現有部署活動的相關資訊(請參閱[如果雲端UI有「記錄片段」錯誤，請檢查部署記錄](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
如需詳細資訊)，您可以執行此命令來取得該活動的執行記錄檔：

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a.是 — 疑難排解現有環境中封鎖部署的其他環境。 繼續進行[步驟3](#step-3)。

b.否 — 疑難排解目前的環境。 繼續進行[步驟3](#step-3)。

+++


## 步驟3 — 驗證所有節點上的SSH {#step-3}

+++所有節點&#x200B;**SSH成功？**

a.是 — 繼續進行[步驟4](#step-4)。\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟4 — 確認所有服務都在執行中 {#step-4}

+++**所有服務都在執行中？**

a.是 — 繼續進行[步驟5](#step-5)。\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟5 — 驗證Bitbucket執行中 {#step-5}

+++**使用Bitbucket？**

a.是 — 檢查[status.bitbucket.com](https://bitbucket.status.atlassian.com/)。\
b.否 — 檢查[建置和部署記錄](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/test/log-locations)中的部署記錄錯誤。 繼續進行[步驟6](#step-6)。

+++

## 步驟6 — 檢查錯誤代碼 {#step-6}

+++**回報的錯誤碼？**

a.是 — 繼續進行[步驟7](#step-7)。\
b.否 — 繼續進行[步驟8](#step-8)。

+++

## 步驟7 - 403禁止的錯誤 {#step-7}

+++**403禁止存取？**

a.是 — 繼續進行[步驟16](#step-16)。
b.否 — 繼續進行[步驟9](#step-9)。

+++

## 步驟8 — 驗證cron工作是否執行 {#step-8}

+++**目前是否在執行cron工作？**&#x200B;在分支上透過ssh登入並執行`ps aufxx |grep cron`。

a.是 — 透過ssh在受影響的分支（例如主要）上登入。 終止和解鎖cron工作。 這將終止cron作業並重設狀態。 執行`php vendor/bin/ece-tools cron:kill`，然後執行`php vendor/bin/ece-tools cron:unlock`。 如果您正在將一個環境合併到另一個環境的過程中，請檢查這兩個環境是否正在執行cron。\
b.否 — 繼續執行[步驟17](#step-17)。

+++

## 步驟9 — 可部署至遠端叢集的應用程式錯誤 {#step-9}

+++**無法將應用程式上傳到遠端叢集錯誤？**

a.是 — 繼續進行[步驟10](#step-10)。\
b.否 — 繼續執行[步驟11](#step-11)。

+++

## 步驟10 — 檢查足夠的儲存空間 {#step-10}

+++**可用儲存空間還好嗎？**

* [檢查整合/入門環境](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-integration-environment)
* [檢查Pro測試/生產環境](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-dedicated-clusters)

a.是 — 繼續[步驟11](#step-11)。\
b.否 — 檢閱[管理磁碟空間](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space)。

+++

## 步驟11 — 驗證磁碟空間 {#step-11}

+++無法寫入&#x200B;**_檔案警告&#x200B;_？**

a.是

* 對於整合/入門環境：

   * 請[在.magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=zh-Hant#application-disk-space)中增加磁碟值，然後重新部署。 如果這個方法無法運作，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
   * 或者，檢閱`var/log`資料夾並刪除任何超過1MB的記錄檔。 執行此命令以檢查檔案大小：

     ```bash
     ls -la var/log
     ```

* 對於Pro測試/生產環境：

   1. 提交支援票證以新增儲存空間。

b.否 — 繼續進行[步驟12](#step-12)。

+++

## 步驟12 — 環境重新部署失敗錯誤 {#step-12}

+++**環境重新部署失敗錯誤？**

a.是 — 繼續[步驟13](#step-13)。\
b.否 — 繼續進行[步驟8](#step-8)。

+++

## 步驟13 — 檢查Elasticsearch升級是否失敗 {#step-13}

+++**正在升級或部署的Elasticsearch？**

a.是 — Elasticsearch升級步驟失敗。 請參閱[Elasticsearch軟體相容性](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html)。 如果Elasticsearch升級仍無法運作，[請提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。 **注意**：在雲端基礎結構上的Adobe Commerce上，請注意，若未提前48個營業時間通知我們的基礎結構團隊，服務升級就無法推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時，[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。\
b.否 — 繼續執行[步驟14](#step-14)。

+++

## 步驟14 — 檢查空間限制 {#step-14}

+++**檔案系統用完inode或空間？**

a.是 — 請參閱[管理磁碟空間](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=zh-Hant#application-disk-space)。\
b.否 — 繼續執行[步驟15](#step-15)。

+++

## 步驟15 - Elasticsearch版本錯誤 {#step-15}

+++**有關Elasticseach版本的錯誤？**

a.是 — 繼續進行[步驟16](#step-16)。\
b.否 — 繼續執行[步驟21](#step-21)。

+++

## 步驟16 — 驗證撰寫器設定 {#step-16}

+++**Composer設定是否正確？**

a.是 — 繼續進行[步驟10](#step-10)。\
b.否 — 檢閱[Composer疑難排解員網頁](https://getcomposer.org/doc/articles/troubleshooting.md)。

+++

## 步驟17 — 檢查長時間執行的程式 {#step-17}

+++**個長時間執行的處理序？**

a.是 — 識別長時間執行的處理作業，然後終止處理作業：
1. 在終端機中執行以下命令： `ps aufx`。
1. 找出長期執行程式的PID。
1. 使用`kill -9 <PID>`終止處理序。

監控部署是否重新發生。

b.否 — 繼續執行[步驟18](#step-18)。

+++

## 步驟18 — 檢查後掛接失敗 {#step-18}

+++**後掛接失敗/擱置？**

a.是 — 資料庫： [可用磁碟空間](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=zh-Hant#allocate-disk-space)，損毀，不完整/損毀的資料表。\
b.否 — 繼續執行[步驟19](#step-19)。

+++

## 步驟19 — 檢查協力廠商擴充功能是否封鎖部署 {#step-19}

+++**使用協力廠商擴充功能？**

a.是 — 嘗試[停用協力廠商擴充功能](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure-store/extensions)並執行部署（檢視問題是否起因），尤其是當任何錯誤中有擴充功能名稱時。\
b.否 — 繼續執行[步驟20](#step-20)。

+++

## 步驟20 — 檢查緩慢查詢 {#step-20}

+++**長時間執行查詢？**

[檢查慢速查詢記錄檔和MySQL顯示處理清單](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md)。

a.是 — 刪除任何長時間執行的查詢。 檢閱[MySQL Kill語法。](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步驟21 — 降級Elasticsearch版本 {#step-21}

+++**正在降級Elasticsearch版本？**

a.是 — 無法透過設定完成。 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

[回到步驟1](#step-1)
