---
title: 安裝失敗；無法建立install.log
description: 本文提供因安裝精靈在安裝期間未建立'install.log'而造成安裝失敗的修正。
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 安裝失敗；無法建立install.log

本文提供因安裝精靈未建立 `install.log` 安裝期間。

## 問題

如果同時執行Adobe Commerce處理序，可能會造成建立安裝記錄時發生問題。 （例如，兩個不同安裝位於不同的頁簽頁面。）

## 原因

Installation-fails-cannot-create-install.log檢閱您的設定 `open_basedir` 在 `php.ini`. 安裝精靈會使用 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP呼叫以取得暫存目錄的值。 如果 [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) 設為拒絕連線至指定的目錄 `sys_get_temp_dir`，安裝會失敗。
檢閱您的設定， `open_basedir` 在 `php.ini`. 安裝精靈會使用 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP呼叫以取得暫存目錄的值。 如果 [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) 設為拒絕連線至指定的目錄 `sys_get_temp_dir`，安裝會失敗。


## 解決方案

若要解決此問題，請變更 `open_basedir` 並重新啟動網頁伺服器。

如果您不確定如何變更此值，請使用下列步驟：

1. 如果您尚未這麼做，請建立 [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. 在瀏覽器的位址或位置欄位中輸入下列URL： `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. 尋找位置 `php.ini`.     `php.ini` 通常指定為 **已載入的組態檔** 在顯示的結果中。
1. 以具有root許可權的使用者身分，開啟 `php.ini` 在文字編輯器中。
1. 找出 `open_basedir` 並加以變更。
1. 將變更儲存至 `php.ini`.
1. 重新啟動網頁伺服器。
