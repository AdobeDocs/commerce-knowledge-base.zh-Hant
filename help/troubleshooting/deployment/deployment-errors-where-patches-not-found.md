---
title: 部署或手動應用程式期間找不到修補程式錯誤
description: 本文提供發生錯誤*找不到下一個修補程式的問題的解決方案：MDVA-XXXXX、ACSD-XXXXX。 使用'status'命令*檢查這些修補程式在目前Magento版本中的可用性。
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 180f0e00ec1a2c6c3bd2ebca4dafe387c7bb3852
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 部署或手動應用程式期間找不到修補程式錯誤

本文提供升級執行個體時部署失敗且部署記錄中出現錯誤問題的解決方案： *找不到下一個修補程式： MDVA-XXXXX、ACSD-XXXXX。 使用&quot;status&quot;命令*&#x200B;檢查這些修補程式是否可用於目前的Magento版本。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 問題

升級Adobe Commerce時發生錯誤： *找不到下一個修補程式*。

## 原因

先前針對舊版套用的修補程式不適用，或不再適用於新版本。

安裝的品質修補工具套件(`magento/quality-patches`)過期時，也會發生此問題。

例如：

案例1：
* QPT 1.1.71中原本可能提供2.4.7-p9的修補程式
* 較新的QPT版本（例如1.1.72）稍後可能會新增2.4.7-p10的支援
* 如果客戶將Commerce升級至2.4.7-p10，但繼續安裝較舊的QPT版本，QPT可能無法辨識出2.4.7-p10存在相容的修補程式變體

案例2：
* QPT 1.1.72中可能已新增修補程式
* 如果客戶保持已安裝較舊的QPT版本，QPT將無法辨識該修補程式是否存在

在這些情況下，套用修補程式可能會失敗並出現訊息，例如：

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

這是因為已安裝的QPT版本無法將目前的Commerce版本對應到適用的修補程式版本。

## 解決方案

此問題不限於透過`.magento.env.yaml`套用修補程式的部署。 使用手動套用修補程式時，也會發生相同的基本問題：

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

例如：

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

在此情況下，修補程式不適用於命令執行環境中安裝的Adobe Commerce版本。

1. 檢查QUALITY_PATCHES區段底下的`.magento.env.yaml`檔案，例如

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. 在[品質修補程式發行說明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)中查詢修補程式ID，以檢查每個修補程式ID是否可套用至您要升級的新版Adobe Commerce。
1. 如果修補程式不適用於您要升級的新版Adobe Commerce，請從`.magento.env.yaml`檔案中移除修補程式ID。
1. 檢閱錯誤所指示的所有修補程式ID後，請推送變更並重新部署。

## 相關閱讀

* 在雲端基礎結構指南的Commerce中[套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment)。
