---
title: PayPal Payflow主動式分片活動
description: 2019年4月2日更新
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow主動式分片活動

2019年4月2日更新

Adobe Commerce中的PayPal Payflow Pro整合正受到讀卡機活動的主動鎖定，攻擊者利用被盜的信用卡嘗試數百美元的交易，以檢查信用卡的有效性。

活動目前鎖定此Payflow Pro整合的版本，這些版本包含在Adobe Commerce 2.1.x、2.2.x、2.3.x for Magento Open Source和Commerce （內部部署和雲端）中。 梳理活動是Payflow Pro整合至購物車的方式所固有的。

>[!NOTE]
>
>為解決這些問題，我們提供新的撰寫器套件，將Google reCAPTCHA或CAPTCHA新增至Payflow Pro結帳表單。 我們建議在所有Adobe Commerce版本上安裝這些套件。

此問題會影響下列Adobe Commerce版本：

* Adobe Commerce內部部署v2.1.x、2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce v2.1.x、2.2.x、2.3.x

## 問題

這些攻擊的症狀包括：

* 您的PayPal Payflow Pro帳戶會顯示數百筆已識別的詐騙交易
* PayPal可能會因為傳入的詐騙交易而暫停Payflow Pro帳戶，並收取大筆費用

## 解決方案

為了協助防範這些攻擊，我們建議將Google reCAPTCHA （建議）或CAPTCHA新增至Payflow Pro結帳表單。 這包括安裝撰寫器套件，以及在Commerce管理員中設定Google reCAPTCHA或CAPTCHA 。

### 安裝套件

Adobe已建立兩個封裝選項，以將Google reCAPTCHA及/或CAPTCHA新增至Payflow Pro結帳表單。 安裝其中一個軟體套件將會更新目前的安裝，並新增有助於增強Payflow Pro結帳表單安全性的選項。

這些套件與下列Adobe Commerce部署和版本相容：

Adobe Commerce （所有部署方法）和Magento Open Source2.1.x、2.2.x、2.3.x

安裝時需要Adobe Commerce執行個體使用CLI命令。 可能需要開發人員協助。

>[!NOTE]
>
>除了安裝任何相關的Payflow Pro結帳表單更新外，我們建議安裝並設定Google reCAPTCHA。 此選項提供不可見的檢查及多個組態選項。

#### 安裝Google reCAPTCHA並簽出表單更新

`magento/module-paypal-recaptcha`套件包含與Google reCAPTCHA和Payflow Pro付款表單更新的整合。 即使您已安裝並設定reCAPTCHA模組，我們建議您安裝此套件。

執行以下命令進行安裝。

針對Adobe Commerce內部部署：**&#x200B;**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

雲端基礎結構上的Adobe Commerce的&#x200B;**：**

1. 執行以下命令：

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. 提交和推送變更：

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. 等待部署完成。

#### 安裝驗證碼的簽出表單更新

`magento/module-paypal-captcha`套件包含與原生Adobe Commerce驗證碼模組的整合。

執行以下命令進行安裝：

針對Adobe Commerce內部部署：**&#x200B;**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

雲端基礎結構上的Adobe Commerce的&#x200B;**：**

1. 執行以下命令：

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. 提交和推送變更：

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. 等待部署完成。

### 設定Google reCAPTCHA或CAPTCHA

安裝套件後，請依照以下檔案所述設定Google reCAPTCHA （建議）或驗證碼：

* 使用手冊中的[Google reCAPTCHA](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/captcha/security-google-recaptcha)。
* 使用手冊中的[驗證碼](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/captcha/security-captcha)。

新的結帳表單選項為：

* Google reCAPTCHA：用於PayPal Payflow Pro付款表單
* 驗證碼：Payflow Pro

## PayPal支援和連絡人

請聯絡PayPal Payflow商家支援，瞭解更多有關防欺詐服務的資訊。 您可以要求PayPal支援團隊啟用[基本詐騙防護服務](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/)篩選器，以提供對付款最嚴密的控制功能，以便自動拒絕可能導致詐騙交易的付款，並接受通常不會造成問題的付款。 請注意，一旦您開啟PayPal詐騙防護服務篩選器，交易可能需要最多2小時才能結算。

>[!NOTE]
>
>如需詳細資訊，請參閱PayPal的KB [&quot;Adobe已就我的Payflow Pro整合與我聯絡。 我需要做什麼？&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**PayPal Payflow商家支援詳細資料**

Payflow商家支援的營業時間為星期一至星期五上午7:00至下午8:00 （中部標準時間）。 您可以透過電話或電子郵件聯絡Payflow商家支援，以取得帳戶協助：

* 電話： 1-888-883-9770 （選擇提示2）
* 國際客戶：1-408-967-0191
* 電子郵件： [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

澳洲支援

* 星期一至星期五上午8:00至晚上7:00 （澳洲時間）
* 電話： +61 2 8288 0198
* 電子郵件： [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
