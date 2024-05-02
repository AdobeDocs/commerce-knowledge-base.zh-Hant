---
title: 「更新程式應用程式無法使用」錯誤
description: 本文會討論當您嘗試使用Web安裝精靈來更新/安裝Adobe Commerce內部部署時，可能會遇到的「更新程式應用程式無法使用」問題的解決方案。
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 「更新程式應用程式無法使用」錯誤

本文會討論當您嘗試使用Web安裝精靈來更新/安裝Adobe Commerce內部部署時，可能會遇到的「更新程式應用程式無法使用」問題的解決方案。

## 問題

整備檢查中會顯示下列訊息：

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## 受影響的產品/版本

* Adobe Commerce內部部署2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x


## 解決方案

若要解決此問題，請參閱是否有 `<magento_root>/update` 包含檔案和子目錄的目錄。 否則，請參閱 [設定更新程式](https://devdocs.magento.com/guides/v2.3/comp-mgr/updater/update-updater.html) （位於我們的開發人員檔案中）。
