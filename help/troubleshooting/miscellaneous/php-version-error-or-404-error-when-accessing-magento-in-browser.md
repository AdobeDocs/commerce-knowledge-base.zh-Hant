---
title: 在瀏覽器中存取Adobe Commerce時，出現PHP版本錯誤或404錯誤
description: 本文提供解決方案，解決您無法在Web瀏覽器中存取Adobe Commerce執行個體，且收到404錯誤或「不支援的PHP版本」錯誤的問題。
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 在瀏覽器中存取Adobe Commerce時，出現PHP版本錯誤或404錯誤

本文提供解決方案，解決您無法在Web瀏覽器中存取Adobe Commerce執行個體，且收到404錯誤或「不支援的PHP版本」錯誤的問題。

## 受影響的產品和版本：

* Adobe Commerce 2.3.x

## 問題：不支援的PHP版本

當您嘗試存取Adobe Commerce店面或Commerce管理員時，會顯示以下訊息：

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### 解決方案

請嘗試下列步驟：

* 將PHP升級至7.3版。如需詳細資訊，請參閱我們的開發人員檔案中的[Adobe Commerce 2.3技術棧疊需求](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html#php)。
* 重新啟動Apache，因為它使用的PHP版本可能與檔案系統上的版本不同。 若要重新啟動Apache，請使用以下命令：
   * Ubuntu： `service apache2 restart`
   * CentOS： `service httpd restart`

## 問題：錯誤404

當您嘗試存取Adobe Commerce店面或Commerce管理員時，會顯示404 （找不到）錯誤。

### 解決方案

請嘗試下列步驟：

* 請確定已啟用[Apache伺服器重寫](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html)。 如果Apache伺服器重寫設定不正確，則無法從正確的位置提供靜態檔案。
* 您在安裝期間輸入的基底URL可能有問題。 當您從命令列安裝Adobe Commerce時，將基底URL指定為`--base-url=`的值，或指定為Web安裝程式「Web設定」頁面上&#x200B;**您的商店地址**&#x200B;欄位的值。 基底URL *必須*&#x200B;以配置（例如`http://`）開頭，並以尾隨斜線(/)結尾。 請使用有效值再次執行安裝程式，然後嘗試存取Adobe Commerce。
