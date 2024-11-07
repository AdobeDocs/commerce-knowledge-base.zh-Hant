---
title: 「無法存取雲端存放庫上的Adobe Commerce：部署時出現403 Forbidden或404 Not Found錯誤」
description: 「本文討論如何解決雲端基礎結構上的Adobe Commerce失敗部署錯誤，類似以下內容：」
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# 無法存取雲端存放庫上的Adobe Commerce：部署時出現403禁止或404找不到

本文討論如何解決雲端基礎結構上的Adobe Commerce失敗部署錯誤，錯誤類似於以下內容：

*無法存取&#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL： HTTP/1.1 403 Forbidden* &#39;&#39;。 或無法下載&quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot;檔案（HTTP/1.1 404找不到）*&quot;。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x和2.4.x

## 問題

部署上的錯誤訊息指出無法存取存放庫URL。

<u>要再現的步驟</u>

手動觸發部署，或透過執行環境的合併、推播或同步化來觸發。

<u>實際結果</u>

部署卡住。 在專案UI的部署錯誤記錄中，會顯示類似以下內容的錯誤訊息：

*&quot;無法存取&#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL： HTTP/1.1 \[403 Forbidden or 404 Not Found\]&quot;*。

（按一下專案UI中的「失敗」圖示以檢視記錄。）

<u>預期結果</u>

已成功完成部署。

## 原因

該錯誤是由授權金鑰（存取金鑰）無效、未指定或未正確指定所造成。

金鑰無效的部分原因包括：

* 您已使用共用帳戶產生金鑰。
* 由於付款問題，您的授權先前已撤銷。

>[!NOTE]
>
>如果您發現此問題是因為開立商業發票或合約失效問題，請聯絡您的Adobe客戶團隊以取得解決此問題的指引。 授權重新啟動後，您的支援和部署權益將會還原。

## 解決方案

採取以下步驟以解決授權金鑰的問題（請參閱以下章節，以瞭解每個步驟的詳細資訊）：

1. 取得有效的授權金鑰（如果您非常確定您的金鑰有效，請略過此步驟）。
1. 在`env:COMPOSER_AUTH`變數中新增金鑰值（或確定有正確的值），並檢查在專案層級和環境層級的變數中以及專案根目錄中的`auth.json`檔案（如果存在）中是否一致地指定金鑰。
1. 如果未指定授權金鑰值或具有其他值，請更新或刪除`auth.json`，以便在單一位置設定金鑰。

### 1.取得有效的授權金鑰

如果您使用在共用帳戶下建立的金鑰，您需要聯絡Adobe Commerce授權擁有者，他為您提供存取權，並要求他們為您產生金鑰。

如果您的授權先前因付款問題而被撤銷，而且您已解決這些問題且已更新授權，則您需要[產生新的驗證金鑰](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)。

### 2.在env：COMPOSER\_AUTH變數中新增索引鍵值，並檢查auth.json中是否指定了相同的索引鍵

在開發人員檔案中，請參閱[準備現有系統](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview)和[新增驗證金鑰](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview)中的指示和相關資訊。

### 3.更新或刪除auth.json

以下逐步說明如何更新授權金鑰：

1. 登入在雲端基礎結構上擁有您的Adobe Commerce SSH金鑰的電腦。
1. 登入您的專案： `magento-cloud login`
1. 建立分支以更新程式碼（在下列範例中，分支名稱為`auth`是從主要分支建立的）：     `magento-cloud environment:branch auth master`
1. 變更至專案根目錄。
1. 可選：如果您偏好的話，請刪除`auth.json`並繼續[步驟9](#step9)。
1. 在文字編輯器中開啟`auth.json`。

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. 新增正確的驗證金鑰。
1. 儲存變更並退出文字編輯器。
1. 認可並合併您的變更：

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. 等待專案部署。
