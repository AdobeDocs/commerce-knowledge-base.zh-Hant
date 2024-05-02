---
title: 啟用Early-alpha Baler模組發生部署錯誤
description: 商家在生產環境中使用Baler模組時會遇到部署錯誤，因為功能目前處於早期Alpha開發階段。
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 啟用Early-alpha Baler模組發生部署錯誤

商家在生產環境中使用Baler模組時會遇到部署錯誤，因為功能目前處於早期Alpha開發階段。

>[!WARNING]
>
>Early-alpha Baler Javascript套件組合未準備好投入生產使用，若要自行承擔使用風險。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.x和2.4.x。
* Adobe Commerce內部部署2.3.x和2.4.x。

## 問題

我們不建議商家在生產環境中使用Baler模組，因為它目前處於早期Alpha開發階段。 使用它可能會導致部署錯誤。

<u>要再現的步驟</u>：

1. 商家嘗試插入 **SCD\_USE\_BALER** 變數在的建置階段 `.magento.env.yaml` 檔案啟用Baler Javascript套件組合。
1. 商家也新增了打捆機撰寫器相依性： `"magento/module-baler": "1.0.0-alpha"` 至 `require` 部分 `composer.json`.

<u>預期結果</u>：

部署成功。

<u>實際結果</u>：

商家在雲端的部署記錄中看到以下錯誤訊息： `<project home>/var/log/cloud.log`，在靜態內容部署階段上：

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## 原因

Baler模組目前處於早期alpha開發階段，且Baler擴充功能的安裝過程複雜。

## 解決方案

您可以檢閱現有的貝勒Alpha檔案，網址為 [Github/Magento/Baler/Alpha快速入門](https://github.com/magento/baler/blob/master/docs/ALPHA.md). 但是，它尚未準備好用於生產，使用它時您將自行承擔風險。 建議您改用Adobe Commerce的內建套件組合（基本套件組合）來合併或套件組合Javascript (JS)檔案，以最佳化檔案。

* 您可以在管理員中開啟合併或套件組合（合併和套件組合不能同時啟用）： **商店** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**.
* 您也可以從命令列啟用Adobe Commerce的內建組合（基本組合）： `php -f bin/magento config:set dev/js/enable_js_bundling 1`

若要進一步瞭解，請參閱 [雲端基礎結構和Adobe Commerce內部部署上的Adobe Commerce上的CSS和Javascript檔案最佳化](https://support.magento.com/hc/en-us/articles/360044482152).
