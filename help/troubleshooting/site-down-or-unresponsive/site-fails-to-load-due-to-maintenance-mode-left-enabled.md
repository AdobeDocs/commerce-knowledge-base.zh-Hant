---
title: 由於維護模式保持啟用狀態，網站無法載入
description: 本文提供網站因維護模式保持啟用或未自動停用而未載入時的修正。 您可能會收到錯誤訊息： *服務暫時無法使用由於維護停機時間或容量問題，伺服器暫時無法服務您的要求。*
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 由於維護模式保持啟用狀態，網站無法載入

本文提供網站因維護模式保持啟用或未自動停用而未載入時的修正。 您可能會收到錯誤訊息： *服務暫時無法使用由於維護停機時間或容量問題，伺服器暫時無法服務您的要求。*

## 受影響的版本和產品

* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce內部部署2.2.x、2.3.x

## 問題

維護模式是部署流程的一部分。 但是，如果該模式已自動啟用且未停用，或商家手動啟用維護模式且忘記停用，則可能會導致部署失敗。

## 原因

啟用維護模式會導致網站無法載入。

## 解決方案

若要檢查目前的維護模式狀態，請從CLI執行以下命令：

```
bin/magento maintenance:status
```

若要停用維護模式，請在CLI中執行以下命令：

```
bin/magento maintenance:disable
```

## 相關閱讀

若要瞭解何時使用維護模式，請參閱開發人員檔案中的[啟用或停用維護模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。
