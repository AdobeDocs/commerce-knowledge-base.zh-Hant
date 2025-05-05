---
title: 將網站新增至安全性掃描時出現錯誤訊息
description: 本文針對使用者無法新增網站至[Commerce安全性掃描](https://account.magento.com/scanner/dashboard/)的問題提供可能的解決方案。
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# 將網站新增至安全性掃描時出現錯誤訊息

本文提供使用者無法新增網站至[Commerce安全性掃描](https://account.magento.com/scanner/dashboard/)時，問題的可能解決方案。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法和版本）
* Magento Open Source

## 問題

使用者無法將網站新增至[Commerce安全性掃描](https://account.magento.com/scanner/dashboard/)。 嘗試新增網站時出現下列錯誤訊息： *無法送出網站進行掃描。*

## 解決方案

1. 請確定在連線埠80和443上未封鎖下列IP位址：
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. 確認代碼會區分大小寫。 如果點選&#x200B;**新增網站**&#x200B;連結後超過30分鐘，程式碼可能已過期。
1. 別忘了清除快取，並確認驗證程式碼顯示在首頁原始碼本文中。 確認程式碼應根據HTML標籤規格插入：HTML註解可插入頁面內文（建議將其放在頁尾區段）；META標籤應僅放置在head區段中。
1. 按一下&#x200B;**驗證確認代碼**&#x200B;之前，請開啟瀏覽器的開發人員主控台，按一下&#x200B;**網路**&#x200B;索引標籤，然後檢查來自magento.com的回應。 應該是HTTP 200 （確定），而且回應本文應該包含JSON物件。
1. 如果回應代碼為HTTP 200，且回應本文為JSON物件，且`verified`屬性值是`false`，則表示在頁面上找不到代碼。 `details`屬性值應該包含說明。 例如，如果存放區使用自我簽署SSL憑證，則可能會發生連線錯誤。

如果您仍然無法新增網站，請完成以下步驟：

1. 在頁面上放置另一個HTML註解：

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. 提交支援票證並提供以下資訊：
   * Adobe Commerce商店URL
   * MAGEID + Magento.com帳戶電子郵件
   * 名字+姓氏
   * 公司名稱
   * 以逗號分隔的通知電子郵件清單

## 相關閱讀

* 使用手冊中的[安全性掃描](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/security-scan)。
