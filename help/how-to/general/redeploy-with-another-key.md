---
title: 雲端上的Adobe Commerce：變更驗證金鑰並重新部署
description: 本文提供如何使用不同的驗證金鑰在雲端基礎結構上重新部署Adobe Commerce的說明。 例如，您可能已將金鑰用於其他帳戶，或者您可能已使用Magento Open Source金鑰而非Adobe Commerce金鑰。
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 雲端上的Adobe Commerce：變更驗證金鑰並重新部署

本文提供如何使用不同的驗證金鑰在雲端基礎結構上重新部署Adobe Commerce的說明。 例如，您可能已將金鑰用於其他帳戶，或者您可能已使用Magento Open Source金鑰而非Adobe Commerce金鑰。

如果您使用不正確的金鑰，部署會失敗。 若要復原，您必須複製專案、將正確的金鑰新增到`auth.json`，然後將變更推送到主分支。

在本文中，我們假設您的專案只有`master`分支（`master`是您首次建立專案時的預設分支）。

使用正確的驗證金鑰重新部署：

1. 登入在雲端基礎結構上擁有您的Adobe Commerce SSH金鑰的電腦。
1. 登入專案：

   ```
   magento-cloud login
   ```

1. 建立分支以更新名稱為`auth`的程式碼：

   ```
   magento-cloud environment:branch auth master
   ```

1. 變更至專案根目錄。
1. 在文字編輯器中開啟`auth.json`。

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 新增正確的驗證金鑰。
1. 儲存變更並退出文字編輯器。
1. 認可並合併您的變更。

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. 等候部署完成。

訊息會指出部署是否成功。 您可以前往熒幕上顯示的&#x200B;**環境路由**&#x200B;之一，確認部署成功。
