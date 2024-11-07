---
title: 安裝失敗；無法建立install.log
description: 本文提供因安裝精靈在安裝期間未建立'install.log'而造成安裝失敗的修正。
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 安裝失敗；無法建立install.log

本文提供因安裝精靈在安裝期間未建立`install.log`而造成安裝失敗的修正。

## 問題

如果同時執行Adobe Commerce處理序，可能會造成建立安裝記錄時發生問題。 （例如，兩個不同安裝位於不同的頁簽頁面。）

## 原因

Installation-fails-cannot-create-install.log
檢閱`php.ini`中`open_basedir`的設定。 安裝精靈使用[sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP呼叫來取得暫存目錄的值。 如果[open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir)設定為拒絕連線至`sys_get_temp_dir`指定的目錄，安裝會失敗。
檢閱`php.ini`中`open_basedir`的設定。 安裝精靈使用[sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP呼叫來取得暫存目錄的值。 如果[open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir)設定為拒絕連線至`sys_get_temp_dir`指定的目錄，安裝會失敗。


## 解決方案

若要解決此問題，請變更`open_basedir`的值，然後重新啟動網頁伺服器。

如果您不確定如何變更此值，請使用下列步驟：

1. 如果您尚未這樣做，請建立[phpinfo.php](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software)。
1. 在瀏覽器的位址或位置欄位中輸入下列URL： `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. 尋找`php.ini`的位置。     在顯示的結果中，`php.ini`通常指定為&#x200B;**載入的組態檔**。
1. 以具有根許可權的使用者身分，在文字編輯器中開啟`php.ini`。
1. 找到`open_basedir`的值並加以變更。
1. 將您的變更儲存至`php.ini`。
1. 重新啟動網頁伺服器。
