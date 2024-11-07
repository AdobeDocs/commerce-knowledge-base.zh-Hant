---
title: 部署後.magento.env.yaml變更未顯示在env.php中
description: 本文針對.magento.env.yaml檔案的變更在部署後未反映在app/etc/env.php中的問題提供解決方案。
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 部署後.magento.env.yaml變更未顯示在env.php中

>[!NOTE]
>
>如果您有此問題，請升級至ece-tools 2002.1.5進行修正。 2002.1.5具有在每個部署上重設opcache的功能，因此永遠不需要變更設定`opcache.enable_cli=1`。 如果您不想升級，則必須按照解決方案中所述進行因應步驟。

本文針對`.magento.env.yaml`檔案中的變更未在部署後`app/etc/env.php`中反映的問題提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有[支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)）。

## 問題

在`.magento.env.yaml`檔案中所做的變更不會影響產生的`app/etc/env.php`。

<u>要再現的步驟：</u>

變更`.magento.env.yaml`中的任何值，並推送至伺服器，伺服器應定義目前取出環境的組態（和部署設定）。 如需相關步驟，請參閱我們的開發人員檔案中的[環境變數>部署變數](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy)。

<u>預期結果：</u>

在`.magento.env.yaml`檔案中所做的變更會影響產生的`app/etc/env.php`。

<u>實際結果：</u>

這些變更對部署後的`app/etc/env.php`變數沒有影響。

## 原因

問題可能是由於`php.ini`檔案中`opcache.enable_cli`引數的值不正確所造成。

## 解決方案

1. 檢查系統是否已根據[Adobe Commerce效能最佳實務>軟體建議](https://experienceleague.adobe.com/en/docs/commerce-operations/performance-best-practices/software)進行設定。
1. 透過執行： `php -i | grep opcache.enable_cli`，檢查`php.ini`中的`opcache.enable_cli`指示詞是否設定為`0`
1. 如果輸出看起來像`opcache.enable_cli=1`，請編輯專案根目錄中的`php.ini`檔案，並將`opcache.enable_cli=1`變更為`opcache.enable_cli=0`
1. 重新部署專案。

## 相關閱讀

* [適用於Adobe Commerce的雲端>建置和部署](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml)。
