---
title: 快取預熱且網站無法在Adobe Commerce上使用
description: 本文提供當頁面快取準備就緒，但部署停滯或網站停止運作時的解決方案。
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 快取預熱且網站無法在Adobe Commerce上使用

本文提供當頁面快取準備就緒，但部署停滯或網站停止運作時的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 問題

快取熱身指令碼在部署後階段結束時，會以如此高的速率傳送要求，以致於某些執行個體（例如4顆CPU的執行個體）無法處理。 他們的nginx會消耗工作者的數量。

<u>要再現的步驟</u>：

啟動快取暖機作業。

<u>預期結果</u>：

頁面或整個網站載入。

<u>實際結果</u>：

網站無法使用或回應時間太長。

## 解決方案

限制快取預熱期間同時連線的數量。 這需要新增`WARM_UP_CONCURRENCY`部署後變數，以指定快取熱身指令碼可同時傳送的熱身要求數目。 設定此選項有助於管理Adobe Commerce雲端基礎結構的負載。 如需相關步驟，請參閱我們的開發人員檔案中的[Post-deploy變數> WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency)。

## 相關閱讀

使用手冊中的[全頁快取](https://docs.magento.com/user-guide/system/cache-full-page.html)
