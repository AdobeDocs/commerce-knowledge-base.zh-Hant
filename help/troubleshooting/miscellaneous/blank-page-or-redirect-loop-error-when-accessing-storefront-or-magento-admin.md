---
title: 存取店面或Commerce管理員時出現空白頁面或重新導向回圈錯誤
description: 本文提供當您存取Adobe Commerce店面或後端，但收到空白頁面或重新導向回圈時，此問題的解決方案。
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
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

頁面空白或顯示&#x200B;*「此網頁有重新導向回圈」*&#x200B;錯誤訊息。

## 原因

發生此問題最可能的原因之一，是將Adobe Commerce設定為從不安全URL重新導向至安全URL，但安全URL設定的值會指定不安全URL。

若要修正問題，您必須修正安全連結的值。

## 解決方案

要確定這是問題的原因，請執行以下步驟：

1. 檢查`'core_config_data'` DB表格中的`web/secure/enable_upgrade_insecure` 、 `web/secure/use_in_adminhtml` （如果您在Admin中有空白/回圈重新導向問題）或`web/secure/use_in_frontend` （如果您在商店前端有空白/回圈重新導向問題）值。
   * 如果`web/secure/enable_upgrade_insecure`設為「1」，則Adobe Commerce會設定為新增回應標頭`Content-Security-Policy: upgrade-insecure-requests`，進而指示瀏覽器使用HTTPS，重新導向所有透過HTTP的查詢
至HTTPS，適用於管理員和店面。
   * 如果`web/secure/use_in_adminhtml`設為「1」，Adobe Commerce會針對管理員頁面的所有HTTP請求傳回HTTPS重新導向。
   * 如果`web/secure/use_in_frontend`設為「1」，Adobe Commerce會針對商店首頁的所有HTTP要求傳回HTTPS重新導向。
1. 檢查`'core_config_data'`資料表中的`web/secure/base_url`和`web/unsecure/base_url`值。 如果兩者開頭都是    `http`，則您需要修正「安全」值。

修正問題：

1. 為`web/secure/base_url.`設定以`https`開頭的值
1. 若要套用變更，請執行以下命令來清除設定快取：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## 相關閱讀

[在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
