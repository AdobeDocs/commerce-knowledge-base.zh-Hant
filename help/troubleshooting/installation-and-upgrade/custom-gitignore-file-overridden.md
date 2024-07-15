---
title: Composer install命令覆寫.gitignore檔案、Adobe Commerce
description: 本文提供雲端基礎結構2.4.2-p1和2.3.7上的Adobe Commerce上的撰寫器覆寫追蹤「.gitignore」檔案時的解決方案。
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Composer install命令覆寫.gitignore檔案、Adobe Commerce

本文提供雲端基礎結構2.4.2-p1和2.3.7上的Adobe Commerce上的撰寫器覆寫追蹤`.gitignore`檔案時的解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.4.2-p1和2.3.7。

## 問題

執行composer install命令時正在覆寫`.gitignore`檔案。

<u>要再現的步驟</u>：


1. 為您的工作區建立空白目錄。
1. 在根目錄中執行此命令：

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \#或2.3.7

1. 然後執行下列命令：
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` #個已提交至存放庫的檔案
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>預期結果</u>：

撰寫器不會覆寫`.gitignore`。

<u>實際結果</u>：

每次composer安裝執行都會覆寫`.gitignore`。

## 解決方案

若要保留您的自訂`.gitignore file`，您需要在`magento-deploy-ignore`區段中忽略它。

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## 相關閱讀

* [追蹤的.gitignore檔案已由撰寫器覆寫！Magento2 GitHub中的](https://github.com/magento/magento2/issues/32888)。
