---
title: 分割資料庫解決方案上的進階報告404錯誤
description: 本文為Adobe Commerce 2.3.x使用者提供修補程式，該修補程式具有[分割資料庫解決方案](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)，在嘗試使用進階報表時發生404錯誤。
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 分割資料庫解決方案上的進階報告404錯誤

本文為Adobe Commerce 2.3.x使用者提供修補程式，該修補程式具有[分割資料庫解決方案](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)，在嘗試使用進階報告時遇到404錯誤。

## 受影響的產品和版本

Adobe Commerce 2.3.0 - 2.3.5-p1

## 問題

此修補程式修正了使用錯誤連線名稱來收集引號資料的問題。 由於使用的連線名稱錯誤，報價資料不會傳送至Magento Business Intelligence (MBI)，且無法產生報表。

## 解決方案

套用本文提供的[修補程式](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)。

## 修補

此修補程式已附加至本文。 若要下載，請按一下以下連結：

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## 如何套用修補程式

解壓縮檔案，並遵循[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式中的指示。
