---
title: 找不到修補程式的部署錯誤
description: 「本文提供發生錯誤*找不到下一個修補程式的問題的解決方案： MDVA-XXXXX、ACSD-XXXXX。 請檢查這些修補程式的'status'命令是否適用於目前的Magento版本*。」
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 找不到修補程式的部署錯誤

本文提供升級執行個體時，如果部署失敗且在部署記錄檔中看到錯誤，問題的解決方案： *找不到後續的修補程式：MDVA-XXXXX、ACSD-XXXXX。 請檢查這些修補程式的「狀態」命令是否適用於目前的Magento版本*.

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## 問題

升級Adobe Commerce時發生錯誤： *找不到後續的修補程式*.

## 原因

先前針對舊版套用的修補程式不適用，或不再適用於新版本。

## 解決方案

1. 檢查您的 `.magento.env.yaml` 在「品質_PATCH」區段下的檔案，例如，

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. 在中查詢修補程式ID [品質修補程式發行說明](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) 檢查每個報表是否能套用至您要升級的新版Adobe Commerce。
1. 若修補程式不適用於您要升級的新版Adobe Commerce，請從以下位置移除修補程式ID： `.magento.env.yaml` 檔案。
1. 檢閱錯誤所指示的所有修補程式ID後，請推送變更並重新部署。

## 相關閱讀

* [套用修補程式](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) 雲端基礎結構指南中的Commerce 。
