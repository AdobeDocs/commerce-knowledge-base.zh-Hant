---
title: 安裝或升級期間發生記憶體不足錯誤
description: 本文會介紹安裝/升級Adobe Commerce內部部署和Magento Open Source內部部署產品期間記憶體不足錯誤的解決方案。
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 安裝或升級期間發生記憶體不足錯誤

本文會介紹安裝/升級Adobe Commerce內部部署和Magento Open Source內部部署產品期間記憶體不足錯誤的解決方案。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.x
* Magento Open Source內部部署2.3.x

## 問題

使用Web安裝精靈安裝或更新Adobe Commerce或Magento Open Source應用程式或元件（如擴充功能、主題或語言套件）時，會顯示類似下列的錯誤：

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

錯誤

```bash
proc_open(): fork failed - Cannot allocate memory
```

也可以在指令行上顯示。

## 解決方案 {#solution}

我們建議您[在開發人員檔案中](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)配置2GB的記憶體給PHP，以確保您的安裝或升級成功。

如果您已經這樣做，請在您的電腦上建立交換檔案。 如果Linux電腦需要更多記憶體資源且RAM已滿，它就會使用&#x200B;*交換空間*。 交換空間用於記憶體中的非使用中頁面。

以下只是建議；可能有其他選項可供使用。 繼續之前，請先洽詢網路管理員或其他知識豐富的資源。 您必須執行命令，以具有`root`許可權的使用者身分建立交換檔案。

### 在Ubuntu上交換檔案 {#swap-file-on-ubuntu}

使用下列參考中所述的`fallocate`命令：

* [如何在Ubuntu 14.04 (Digitalocean)上新增交換功能](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [如何在Ubuntu 16.04 (Digitalocean)上新增交換空間](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [交換常見問題集(help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### 在CentOS上交換檔案 {#swap-file-on-centos}

使用下列參考中所述的`mkswap`命令：

* [如何在CentOS 6 (Digitalocean)上新增交換功能](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [如何在CentOS 7 (Digitalocean)上新增交換功能](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [交換空間（RedHat客戶入口網站）](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
