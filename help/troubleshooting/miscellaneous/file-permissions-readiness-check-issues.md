---
title: 檔案許可權整備檢查問題
description: 「本文提供檔案許可權整備檢查問題的修正。 如果適用的話，Adobe Commerce檔案系統中的目錄必須可由網頁伺服器使用者和Adobe Commerce檔案系統擁有者寫入。 如果許可權設定不正確，Web設定精靈中會顯示類似下列的錯誤：'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 檔案許可權整備檢查問題

本文提供檔案許可權整備檢查問題的修正。 如果適用的話，Adobe Commerce檔案系統中的目錄必須可由網頁伺服器使用者和Adobe Commerce檔案系統擁有者寫入。 如果您的許可權設定不正確，Web設定精靈中會顯示類似下列的錯誤：

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

您解決此問題的方式取決於您是設定一位使用者還是兩位使用者：

* *一位使用者*&#x200B;表示您是以同時執行網頁伺服器的相同使用者登入Adobe Commerce伺服器。 這類設定在共用託管環境中很常見。
* *兩個使用者*&#x200B;表示您通常&#x200B;*無法*&#x200B;以網頁伺服器使用者的身分登入或切換至該使用者。 您通常會以單一使用者身分登入，並以其他使用者身分執行網頁伺服器。 這是一般私人託管或您擁有自己的伺服器的情況。

## 單一使用者解析度

如果您有命令列存取權，假設已在`/var/www/html/magento2`中安裝Adobe Commerce，請輸入下列命令：

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

如果您沒有命令列存取權，請使用託管提供者提供的FTP使用者端或檔案管理員應用程式來設定許可權。

## 雙使用者解析度

若要選擇在一行中輸入所有命令，請輸入以下假設Adobe Commerce已安裝在`/var/www/html/magento2`中，且Web伺服器群組名稱為`apache`：

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

如果檔案系統許可權設定不正確，且無法由Adobe Commerce檔案系統擁有者變更，您可以以`root`許可權的使用者身分輸入命令：

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
