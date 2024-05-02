---
title: 網站和API效能低
description: 針對雲端基礎結構2.2.1上已知的Adobe Commerce問題，提供修補程式，該問題與寫入「debug.log」所需的長時間導致低網站和API效能有關。
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 網站和API效能低

本文針對由於寫入時間較長而導致網站和API效能偏低的相關雲端基礎結構2.2.1已知的Adobe Commerce問題，提供修補程式 `debug.log`.

## 問題

網站效能緩慢。 API作業執行速度緩慢，例如使用更新產品 `PUT` 方法。 當您進一步瞭解使用New Relic的作業時，大部分的記憶體和CPU都是透過寫入來消耗 `/var/log/debug.log`.

## 解決方案

若要解決此問題，請套用修補程式。 修補程式會分割並將記錄、付款和運送方法記錄檔寫入個別檔案。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### 相容的Adobe Commerce版本

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.2.1

此修補程式也與下列Adobe版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.2.0、2.2.2、2.2.3
* Adobe Commerce內部部署2.2.0、2.2.2、2.2.3

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中取得指示。

## 附加的檔案
