---
title: 部署失敗Fastly模組與Adobe Commerce版本不相容
description: '更新日期： 2019年2月29日'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 部署失敗Fastly模組與Adobe Commerce版本不相容

更新日期： 2019年2月29日

本文提供因Fastly模組與您目前的Adobe Commerce版本不相容而造成部署失敗時的修正。

**問題：** 在新提交和推送後部署失敗，錯誤訊息如下：

>\[例外狀況\]警告：遺失Fastly\\Cdn\\Plugin\\...的引數3，在/app/vendor/magento/framework/Interception/Interceptor.php中呼叫，並在/app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php中定義……

**原因：** Fastly模組v1.2.79中的回溯不相容變更。

**解決方案（暫時）：** 將Fastly模組升級至1.2.82版或更高版本，並在Commerce管理中上傳新的VCL。 然後，提交並推送您的變更以觸發成功部署。

## 受影響的版本

* Adobe Commerce內部部署2.1.X
* 雲端基礎結構上的Adobe Commerce 2.1.X
* Fastly模組1.2.79

## 問題

當您認可並將變更推送至整合、生產或測試環境時，下一個步驟通常是觸發部署程式。 這是在Adobe Commerce的雲端基礎結構版本中自動完成，並在Adobe Commerce內部部署中手動完成。

部署可能會失敗，並出現下列錯誤訊息：

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

如果您在雲端基礎結構解決方案上使用Adobe Commerce，您會在以下位置看到此錯誤訊息： [部署記錄](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html#log-deploy-log). 若為Adobe Commerce內部部署，您會在命令列中看到錯誤。

## 原因

此問題是由於Fastly模組v1.2.79中的回溯不相容變更所導致。

## 解決方案

將Fastly模組升級至1.2.82版或更新版本。

若要這麼做，請執行下列步驟：

1. 執行以下其中一個命令：
   * 如果Fastly模組包含在magento-cloud-metapackage中：    <pre>Composer更新magento/magento-cloud-metapackage</pre>
   * 如果Fastly模組是單獨安裝(例如，如果您是使用Adobe Commerce內部部署，而不是雲端版本) <pre>Composer更新fastly/magento2</pre>
1. 提交並推播變更，如果未自動完成，則觸發部署程式。
1. 在管理員中， [將新VCL上傳到Fastly](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets).
