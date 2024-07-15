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

1. 商家嘗試在`.magento.env.yaml`檔案的建置階段中插入&#x200B;**SCD\_USE\_BALER**&#x200B;變數，這會啟用Baler Javascript套件組合套件。
1. 商家也新增了打捆機撰寫器相依性： `"magento/module-baler": "1.0.0-alpha"`到`composer.json`的`require`區段。

<u>預期結果</u>：

部署成功。

<u>實際結果</u>：

商家在靜態內容部署階段中，在雲端上的部署記錄檔`<project home>/var/log/cloud.log`中看到以下錯誤訊息：

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## 原因

Baler模組目前處於早期alpha開發階段，且Baler擴充功能的安裝過程複雜。

## 解決方案

您可以在[Github/Alpha/Baler/Getting starting with the alpha](https://github.com/magento/baler/blob/master/docs/ALPHA.md)檢閱現有的BalerAlpha檔案Magento。 但是，它尚未準備好用於生產，使用它時您將自行承擔風險。 建議您改用Adobe Commerce的內建套件組合（基本套件組合）來合併或套件組合Javascript (JS)檔案，以最佳化檔案。

* 您可以在管理員中開啟合併或組合（合併和組合無法同時啟用）： **存放區** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**。
* 您也可以從命令列啟用Adobe Commerce的內建組合（基本組合）： `php -f bin/magento config:set dev/js/enable_js_bundling 1`

若要瞭解詳細資訊，請參閱雲端基礎結構和Adobe Commerce內部部署上的Adobe Commerce上的[CSS和Javascript檔案最佳化](https://support.magento.com/hc/en-us/articles/360044482152)。
