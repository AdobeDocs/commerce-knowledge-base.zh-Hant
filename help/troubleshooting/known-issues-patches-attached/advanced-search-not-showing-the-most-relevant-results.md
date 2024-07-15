---
title: 進階搜尋未顯示最相關的結果
description: 本文針對已知Adobe Commerce問題提供修補程式，該問題中的進階搜尋不會先顯示最相關的結果。
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 進階搜尋未顯示最相關的結果

本文針對已知Adobe Commerce問題提供修補程式，該問題中的進階搜尋不會先顯示最相關的結果。

## 受影響的版本 {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce （所有部署選項） 2.x.x
* Magento Open Source2.x.x

## 問題 {#Advancedsearchnotshowingmostrelevantresults-Description}

進階搜尋功能不會像快速搜尋那樣先傳回最相關的結果。 問題不取決於所選的搜尋引擎型別。

<u>要再現的步驟：</u>

1. 在店面，前往快速搜尋，搜尋「合身的外套」。
1. 請注意，「Orion Two-Tone Fitted Jacket」是第一個結果。
1. 前往進階搜尋，並在名稱欄位中搜尋「Fitted Jacket」。

<u>預期結果：</u>

「Orion Two-Tone Fitted Jacket」是使用進階搜尋時的第一個結果，是最相關的結果。

<u>實際結果：</u>

「Orion Two-Tone Fitted Jacket」不是第一個結果，不過它是最相關的結果。

## 解決方案 {#Advancedsearchnotshowingmostrelevantresults-Solution}

若要解決此問題，請套用本文附加的修補程式。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-7256\_EE\_2.1.7\_v1.composer.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

此修補程式會新增依進階搜尋結果的相關性進行排序的實作，作為預設排序欄位。

此修補程式與所有受影響的版本和版本相容。

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
