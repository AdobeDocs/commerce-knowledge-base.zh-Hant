---
title: 疑難排解[!UICONTROL CSP]限制模式中的storefront結帳頁面
description: 本文說明在CSP限制模式下檢視結帳頁面時可能遇到的錯誤，並提供修正這些錯誤的解決方案。
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# 疑難排解[!UICONTROL CSP]限制模式中的storefront結帳頁面

本文針對&#x200B;**[!UICONTROL CSP restricted mode]**&#x200B;中檢視結帳頁面時Adobe Commerce 2.4.7問題提供說明和修正，其中的&quot;*拒絕執行內嵌指令碼，因為它違反下列內容安全性原則指示：「script-src ...*」錯誤訊息在瀏覽器主控台記錄中。

## 受影響的產品和版本

雲端基礎結構、Adobe Commerce內部部署和Magento Open Source上的Adobe Commerce：

* 2.4.7
* 2.4.6畫素
* 2.4.5畫素
* 2.4.4畫素

## 問題 — Storefront結帳頁面已損毀或無法載入

**storefront checkout**&#x200B;頁面已損毀或無法載入，因為「*拒絕執行內嵌指令碼，因為它違反了下列內容安全性原則指令：瀏覽器主控台記錄檔中的「script-src ...*」錯誤訊息。

<u>要再現的步驟</u>：

1. 前往店面。
1. 新增產品至購物車並繼續結帳。

<u>預期結果</u>：

結帳頁面會正常完整載入。

<u>實際結果</u>：

簽出頁面為空白或缺少元件。 瀏覽器主控台記錄中顯示下列[!DNL JS]錯誤： &quot;*拒絕執行內嵌指令碼，因為它違反下列內容安全性原則指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更新版本中，**[!UICONTROL CSP]**&#x200B;預設會針對店面和管理區域中的付款頁面設定為`restrict-mode`，針對所有其他頁面則設定為`report-only`模式。
對應**[!UICONTROL CSP]**&#x200B;標題在付款頁面的`script-src`指示詞內不包含`unsafe-inline`關鍵字。 此外，僅允許[!DNL whitelisted]個內嵌指令碼。

### 解決方案

使用者可能會看到瀏覽器錯誤，因為某些指令碼因為&#x200B;**[!UICONTROL CSP]**&#x200B;而被封鎖：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>若要修正此問題，您必須</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)使用`SecureHtmlRenderer`類別的封鎖指令碼。
1. 使用`CSPNonceProvider`類別允許執行指令碼。
Adobe Commerce和Magento Open Source 2.4.7及更新版本包含一個**[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]提供者，以便為每個請求產生唯一的[!DNL nonce]字串。 然後會將這[!DNL nonce]個字串附加至[!UICONTROL CSP]標頭。

   在`Magento\Csp\Helper\CspNonceProvider`中使用`generateNonce`函式以取得[!DNL nonce]字串。

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

1. [新增 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)至模組的`csp_whitelist.xml`檔案。

## 問題 — 付款方式遺失或無法運作

**storefront checkout**&#x200B;頁面上缺少付款方法或付款方法無法運作，且「*Refused to execute inline script，因為它違反了下列內容安全性原則指令：「script-src ...*」瀏覽器主控台記錄檔中的錯誤訊息。

<u>要再現的步驟</u>：

1. 前往店面。
2. 新增產品至購物車並繼續結帳。
3. 選取付款方式。

<u>預期結果</u>：

您可以選取付款方式並繼續成功下訂單。

<u>實際結果</u>：

付款方式遺失或無法運作。 瀏覽器主控台記錄中顯示下列[!DNL JS]錯誤： &quot;*拒絕執行內嵌指令碼，因為它違反下列內容安全性原則指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更新版本中，**[!UICONTROL CSP]**&#x200B;預設會針對店面和管理區域中的付款頁面設定為`restrict-mode`，針對所有其他頁面則設定為`report-only`模式。
對應**[!UICONTROL CSP]**&#x200B;標題在付款頁面的`script-src`指示詞內不包含`unsafe-inline`關鍵字。 此外，僅允許[!DNL whitelisted]個內嵌指令碼。

### 解決方案

使用者可能會看到瀏覽器錯誤，因為某些指令碼因為&#x200B;**[!UICONTROL CSP]**&#x200B;而被封鎖：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>若要修正此問題，您必須</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)使用`SecureHtmlRenderer`類別的封鎖指令碼。
1. 使用`CSPNonceProvider`類別允許執行指令碼。
Adobe Commerce和Magento Open Source 2.4.7及更新版本包含一個**[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]提供者，以便為每個請求產生唯一的[!DNL nonce]字串。 然後會將這[!DNL nonce]個字串附加至[!UICONTROL CSP]標頭。

   在`Magento\Csp\Helper\CspNonceProvider`中使用`generateNonce`函式以取得[!DNL nonce]字串。

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

1. [新增 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)至模組的`csp_whitelist.xml`檔案。

## 問題 — 客戶無法下訂單

客戶無法下訂單，因為&quot;*拒絕執行內嵌指令碼，因為它違反了下列內容安全性原則指令：瀏覽器主控台記錄檔中的&quot;script-src ...*&quot;錯誤訊息。

<u>要再現的步驟</u>：

1. 前往店面。
2. 新增產品至購物車並繼續結帳。
3. 選取付款方式。
4. 按一下&#x200B;**下訂單**。

<u>預期結果</u>：

您可以成功下訂單。

<u>實際結果</u>：

您無法下訂單。 瀏覽器主控台記錄中顯示下列[!DNL JS]錯誤： &quot;*拒絕執行內嵌指令碼，因為它違反下列內容安全性原則指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更新版本中，**[!UICONTROL CSP]**&#x200B;預設會針對店面和管理區域中的付款頁面設定為`restrict-mode`，針對所有其他頁面則設定為`report-only`模式。
對應**[!UICONTROL CSP]**&#x200B;標題在付款頁面的`script-src`指示詞內不包含`unsafe-inline`關鍵字。 此外，僅允許[!DNL whitelisted]個內嵌指令碼。

### 解決方案

使用者可能會看到瀏覽器錯誤，因為某些指令碼因為&#x200B;**[!UICONTROL CSP]**&#x200B;而被封鎖：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>若要修正此問題，您必須</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style)使用`SecureHtmlRenderer`類別的封鎖指令碼。
1. 使用`CSPNonceProvider`類別允許執行指令碼。
Adobe Commerce和Magento Open Source 2.4.7及更新版本包含一個**[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce]提供者，以便為每個請求產生唯一的[!DNL nonce]字串。 然後會將這[!DNL nonce]個字串附加至[!UICONTROL CSP]標頭。

   在`Magento\Csp\Helper\CspNonceProvider`中使用`generateNonce`函式以取得[!DNL nonce]字串。

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

1. [新增 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes)至模組的`csp_whitelist.xml`檔案。
