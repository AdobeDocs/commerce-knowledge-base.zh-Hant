---
title: 使用品質修補工具檢查Adobe Commerce問題的修補程式
description: 本文提供品質修補工具(QPT)的概觀，以及說明其使用方式的資源連結。
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 使用品質修補工具檢查Adobe Commerce問題的修補程式

本文提供品質修補工具(QPT)的概觀，以及說明其使用方式的資源連結。

## 受影響的產品和版本

* Adobe Commerce內部部署，全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 什麼是品質修補工具

此 [品質修補工具](https://github.com/magento/quality-patches) (QPT)是由Adobe和Magento Open Source社群開發的個別修補程式。

它可讓您：

* 套用封裝內含的品質修補程式
* 回覆先前套用的修補程式
* 檢視已安裝Adobe Commerce版本可用的品質修補程式的一般資訊。

以下是您可以取得狀態表以檢視可用修補程式的範例：

![Magento_修補程式_清單](assets/status_table.png)

此工具旨在協助您針對使用Adobe Commerce時可能遇到的問題自助提供修補程式，或輕鬆套用Adobe Commerce支援人員建議的修補程式。

>[!NOTE]
>
>QPT僅適用於品質修補程式。 安全性修補程式可在 [Magento安全中心](https://magento.com/security/patches).

## Quality Patches Tool提供的修補程式

請參閱 [品質修補工具](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我們的開發人員檔案中，取得可用修補程式的清單。

## 如何安裝及使用品質修補工具

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce的安裝和使用命令不同，因為對於雲端，QPT套件包含在ece-tools套件中。

### 如何在Adobe Commerce內部部署安裝及使用QPT

請參閱 [軟體更新指南>修補](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 於我們的開發人員檔案中，取得如何安裝及使用QPT套用和還原修補程式的詳細資訊。

### 如何在雲端基礎結構上安裝和使用適用於Adobe Commerce的QPT

請參閱 [Adobe Commerce雲端>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) 在我們的開發人員檔案中，取得有關如何安裝和使用QPT以在雲端基礎結構上的Adobe Commerce上套用及還原修補程式的詳細資訊。

## 相關閱讀

* [品質修補程式工具發行說明](https://devdocs.magento.com/quality-patches/release-notes.html) （位於我們的開發人員檔案中）。
* [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中。
