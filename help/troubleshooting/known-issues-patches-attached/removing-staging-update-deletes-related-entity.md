---
title: 移除中繼更新會刪除相關實體
description: 本文修補與實體相關的已知Adobe Commerce 2.2.3問題（類別、CMS頁面等） 本身會在刪除相關排程更新時移除。
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 移除中繼更新會刪除相關實體

本文修補與實體相關的已知Adobe Commerce 2.2.3問題（類別、CMS頁面等） 本身會在刪除相關排程更新時移除。

>[!NOTE]
>
>Adobe Commerce 2.2.6已修正問題。

## 問題

當您刪除開始日期和結束日期之間的有效排程更新時，也會刪除相關實體（類別、子類別、CMS頁面）。

<u>要再現的步驟（使用類別）</u>：

1. 登入Commerce管理員。
1. 在&#x200B;**目錄** > **類別**&#x200B;下建立新的子類別。
1. 使用開始和結束時間建立新的測試更新。
1. 等到套用更新為止；也就是開始時間。
1. 使用&#x200B;**檢視/編輯**&#x200B;連結刪除更新。

<u>預期結果</u>：

更新已刪除，且子類別仍存在於管理員中。

<u>實際結果</u>：

更新和子類別即會刪除。

## 解決方案

請套用本文提供的修補程式，並清除執行中的快取

```bash
bin/magento
  cache:clean
```

## 修補

修補程式已附加至本文。 若要下載修補程式，請向下捲動至文章結尾，然後按一下檔案名稱或按一下對應的連結：

* [下載MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [下載MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [下載MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### 相容的Adobe Commerce版本：

已針對下列專案建立修補程式：

* 已針對Adobe Commerce （所有部署方法） 2.2.3建立MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch
* 已針對Adobe Commerce （所有部署方法） 2.2.4建立MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch
* 已針對Adobe Commerce （所有部署方法） 2.2.5建立MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch

MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署2.2.0-2.2.2
* 雲端基礎結構上的Adobe Commerce 2.2.0 - 2.2.3

MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署2.1.0 - 2.1.18， 2.2.0 - 2.2.3
* 雲端基礎結構上的Adobe Commerce 2.1.0-2.1.18、2.2.0-2.2.3

MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.2.5

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
