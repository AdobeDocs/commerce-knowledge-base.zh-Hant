---
title: 存取店面或Commerce管理員時出現空白頁面或重新導向回圈錯誤
description: 本文提供當您存取Adobe Commerce店面或後端，但收到空白頁面或重新導向回圈時，此問題的解決方案。
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 存取店面或Commerce管理員時出現空白頁面或重新導向回圈錯誤

本文提供當您存取Adobe Commerce店面或後端，但收到空白頁面或重新導向回圈時，此問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本
* Adobe Commerce內部部署，所有版本
* Magento Open Source，所有版本

## 問題

<u>要再現的步驟</u>

開啟店面或管理頁面。

<u>預期結果</u>

頁面隨即開啟。

<u>實際結果</u>

頁面為空白或顯示 *「此網頁有重新導向回圈」* 錯誤訊息。

## 原因

發生此問題最可能的原因之一，是將Adobe Commerce設定為從不安全URL重新導向至安全URL，但安全URL設定的值會指定不安全URL。

若要修正問題，您必須修正安全連結的值。

## 解決方案

要確定這是問題的原因，請執行以下步驟：

1. 檢查 `web/secure/enable_upgrade_insecure` ， `web/secure/use_in_adminhtml` （如果您的Admin中出現空白/回圈重新導向問題）或 `web/secure/use_in_frontend` （如果您在商店前端有空白/回圈重新導向問題） `'core_config_data'` 資料庫表格。
   * 如果 `web/secure/enable_upgrade_insecure` 設為「1」，然後設定Adobe Commerce以新增回應標題 `Content-Security-Policy: upgrade-insecure-requests`，因此指示瀏覽器使用HTTPS，將所有透過HTTP的查詢重新導向至HTTPS （適用於管理員和店面）。
   * 如果 `web/secure/use_in_adminhtml` 設為「1」，Adobe Commerce會針對管理員頁面的所有HTTP請求傳回HTTPS重新導向。
   * 如果 `web/secure/use_in_frontend` 設為「1」，Adobe Commerce會針對商店首頁的所有HTTP請求傳回HTTPS重新導向。
1. 檢查 `web/secure/base_url` 和 `web/unsecure/base_url` 中的值 `'core_config_data'` 表格。 如果兩者開頭都是    `http`，則您需要修正「安全」值。

修正問題：

1. 設定以開頭的值 `https` 的 `web/secure/base_url.`
1. 若要套用變更，請執行以下命令來清除設定快取：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
