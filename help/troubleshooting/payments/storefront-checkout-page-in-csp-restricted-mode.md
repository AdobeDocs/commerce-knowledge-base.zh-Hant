---
title: 疑難排解中的storefront結帳頁面 [!UICONTROL CSP] 受限模式
description: 本文說明在CSP限制模式下檢視結帳頁面時可能遇到的錯誤，並提供修正這些錯誤的解決方案。
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# 疑難排解中的storefront結帳頁面 [!UICONTROL CSP] 受限模式

本文提供在中檢視結帳頁面時，Adobe Commerce 2.4.7問題的說明和修正 **[!UICONTROL CSP restricted mode]**，使用&quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*「瀏覽器主控台記錄檔中的錯誤訊息。

## 受影響的產品和版本

雲端基礎結構、Adobe Commerce內部部署和Magento Open Source上的Adobe Commerce：

* 2.4.7
* 2.4.6畫素
* 2.4.5畫素
* 2.4.4畫素

## 問題 — Storefront結帳頁面已損毀或無法載入

此 **店面結帳** 頁面損毀或無法載入，請使用&quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*「瀏覽器主控台記錄檔中的錯誤訊息。

<u>要再現的步驟</u>：

1. 前往店面。
1. 新增產品至購物車並繼續結帳。

<u>預期結果</u>：

結帳頁面會正常完整載入。

<u>實際結果</u>：

簽出頁面為空白或缺少元件。 下列專案 [!DNL JS] 錯誤會顯示在瀏覽器主控台記錄檔中： &quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source 2.4.7版及更新版本中， **[!UICONTROL CSP]** 設定於 `restrict-mode`，預設情況下，適用於店面和管理區域以及中的付款頁面 `report-only` 模式。
對應的 **[!UICONTROL CSP]** 標題不包含 `unsafe-inline` 內的關鍵字 `script-src` 付款頁面的指示。 此外，僅限 [!DNL whitelisted] 允許內嵌指令碼。

### 解決方案

使用者可能會看到瀏覽器錯誤，因為某些指令碼因以下原因遭到封鎖 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>若要修正此問題，您必須</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 使用封鎖的指令碼 `SecureHtmlRenderer` 類別。
1. 使用 `CSPNonceProvider` 允許執行指令碼的類別。
Adobe Commerce和Magento Open Source 2.4.7及更新版本包含 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 提供者協助產生唯一 [!DNL nonce] 每個請求的字串。 這些 [!DNL nonce] 字串接著會附加至 [!UICONTROL CSP] 標頭。

   使用 `generateNonce` 中的函式 `Magento\Csp\Helper\CspNonceProvider` 以取得 [!DNL nonce] 字串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [新增 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 至模組的 `csp_whitelist.xml` 檔案。

## 問題 — 付款方式遺失或無法運作

付款方法遺失或無法用於 **店面結帳** 頁面，使用&quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*「瀏覽器主控台記錄檔中的錯誤訊息。

<u>要再現的步驟</u>：

1. 前往店面。
2. 新增產品至購物車並繼續結帳。
3. 選取付款方式。

<u>預期結果</u>：

您可以選取付款方式並繼續成功下訂單。

<u>實際結果</u>：

付款方式遺失或無法運作。 下列專案 [!DNL JS] 錯誤會顯示在瀏覽器主控台記錄檔中： &quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source 2.4.7版及更新版本中， **[!UICONTROL CSP]** 設定於 `restrict-mode`，預設情況下，適用於店面和管理區域以及中的付款頁面 `report-only` 模式。
對應的 **[!UICONTROL CSP]** 標題不包含 `unsafe-inline` 內的關鍵字 `script-src` 付款頁面的指示。 此外，僅限 [!DNL whitelisted] 允許內嵌指令碼。

### 解決方案

使用者可能會看到瀏覽器錯誤，因為某些指令碼因以下原因遭到封鎖 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>若要修正此問題，您必須</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 使用封鎖的指令碼 `SecureHtmlRenderer` 類別。
1. 使用 `CSPNonceProvider` 允許執行指令碼的類別。
Adobe Commerce和Magento Open Source 2.4.7及更新版本包含 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 提供者協助產生唯一 [!DNL nonce] 每個請求的字串。 這些 [!DNL nonce] 字串接著會附加至 [!UICONTROL CSP] 標頭。

   使用 `generateNonce` 中的函式 `Magento\Csp\Helper\CspNonceProvider` 以取得 [!DNL nonce] 字串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [新增 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 至模組的 `csp_whitelist.xml` 檔案。

## 問題 — 客戶無法下訂單

客戶無法下訂單，請使用&quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*「瀏覽器主控台記錄檔中的錯誤訊息。

<u>要再現的步驟</u>：

1. 前往店面。
2. 新增產品至購物車並繼續結帳。
3. 選取付款方式。
4. 按一下 **下單**.

<u>預期結果</u>：

您可以成功下訂單。

<u>實際結果</u>：

您無法下訂單。 下列專案 [!DNL JS] 錯誤會顯示在瀏覽器主控台記錄檔中： &quot;*拒絕執行內嵌指令碼，因為它違反了以下內容安全性原則指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source 2.4.7版及更新版本中， **[!UICONTROL CSP]** 設定於 `restrict-mode`，預設情況下，適用於店面和管理區域以及中的付款頁面 `report-only` 模式。
對應的 **[!UICONTROL CSP]** 標題不包含 `unsafe-inline` 內的關鍵字 `script-src` 付款頁面的指示。 此外，僅限 [!DNL whitelisted] 允許內嵌指令碼。

### 解決方案

使用者可能會看到瀏覽器錯誤，因為某些指令碼因以下原因遭到封鎖 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>若要修正此問題，您必須</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 使用封鎖的指令碼 `SecureHtmlRenderer` 類別。
1. 使用 `CSPNonceProvider` 允許執行指令碼的類別。
Adobe Commerce和Magento Open Source 2.4.7及更新版本包含 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 提供者協助產生唯一 [!DNL nonce] 每個請求的字串。 這些 [!DNL nonce] 字串接著會附加至 [!UICONTROL CSP] 標頭。

   使用 `generateNonce` 中的函式 `Magento\Csp\Helper\CspNonceProvider` 以取得 [!DNL nonce] 字串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [新增 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 至模組的 `csp_whitelist.xml` 檔案。
