---
title: '部署失敗：無法套用MDVA-43395修補程式'
description: 本文提供此問題的解決方案，其中嘗試套用MDVA-43395修補程式會導致部署失敗。
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 部署失敗：無法套用MDVA-43395修補程式

本文提供此問題的解決方案，其中嘗試套用MDVA-43395修補程式會導致部署失敗。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

您無法套用MDVA-43395修補程式。

## 原因

如果雲端商戶有以下情況，則不需要個別套用MDVA-43395修補程式 [magento/magento-cloud-patches 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) 已安裝，其中包含修補程式。

## 解決方案

若要解決此問題，請從「 」移除MDVA-43395和MDVA-43443修補程式 `m2-hotfixes` 目錄並重新部署。

如果您能透過以下方式套用MDVA-43443修補程式： `m2-hotfixes` 目錄，您仍需移除該專案，如上所述。 Adobe Commerce的未來版本已包含這些修補程式，因此如果您稍後升級，可能會導致部署失敗。

若要確認是否已套用修正程式，請執行 `vendor/bin/magento-patches -n status |grep 43443` 命令。
43443如果它顯示多個類似這樣的結果，您應該從 `m2-hotfixes` 資料夾：

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## 相關閱讀

* [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中。
* [Commerce雲端修補程式](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) （位於我們的開發人員檔案中）。
