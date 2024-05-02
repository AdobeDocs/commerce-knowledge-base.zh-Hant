---
title: 針對雲端基礎結構上Adobe Commerce的所有頁面，將HTTP重新導向至HTTPS （強制TLS）
description: 在Commerce管理員中啟用Fastly的**強制TLS**功能，對雲端基礎結構存放區上Adobe Commerce的所有頁面啟用全域HTTP到HTTPS重新導向。
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 針對雲端基礎結構上Adobe Commerce的所有頁面，將HTTP重新導向至HTTPS （強制TLS）

啟動Fastly的 **強制TLS** Commerce管理員中的功能，可為雲端基礎結構存放區上Adobe Commerce的所有頁面啟用全域HTTP至HTTPS重新導向。

本文提供詳細資訊 [步驟](#steps)，快速瞭解強制TLS功能、受影響的版本以及相關檔案的連結。

## 步驟 {#steps}

### 步驟1：設定安全URL {#step-1-configure-secure-urls}

在此步驟中，我們會定義存放區的安全URL。 如果已完成此操作，請前往 [步驟2：啟用強制TLS](#step-2-enable-force-tls).

1. 登入Commerce管理員。
1. 瀏覽至 **商店** > **設定** > **一般** > **Web**.
1. 展開 **基礎URL （安全）** 區段。    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. 在 **安全基底URL** 欄位中，指定商店的HTTPS URL。
1. 設定 **在店面上使用安全URL** 和 **在管理員上使用安全URL** 設定為 **是**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. 按一下 **儲存設定** 以套用變更。

**使用手冊中的相關檔案：**   [儲存URL](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### 步驟2：啟用強制TLS {#step-2-enable-force-tls}

1. 在Commerce管理員中，導覽至 **商店** > **設定** > **進階** > **系統**.
1. 展開 **完整頁面快取** 區段，然後 **Fastly設定**，然後 **進階設定**.
1. 按一下 **強制TLS** 按鈕。    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. 在出現的對話方塊中，按一下 **上傳**.    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. 對話方塊關閉後，請確定「強制TLS」的目前狀態顯示為 **已啟用**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**相關Fastly檔案：**   [強制TLS指南](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) 適用於Adobe Commerce 2.

## 關於強制TLS

TLS （傳輸層安全性）是一種安全HTTP連線的通訊協定，取代了較不安全的上一代 — SSL （安全通訊端層）通訊協定。

Fastly的Force TLS功能可讓您強制將網站頁面的所有傳入未加密請求傳送到TLS。

>>
其運作方式為傳回 *301已永久移動* 對任何未加密請求的回應，這會重新導向至等同的TLS。 例如，針對下列專案提出要求： *http://www.example.com/foo.jpeg* 將重新導向至 *https://www.example.com/foo.jpeg*.

[保護通訊安全](https://docs.fastly.com/guides/securing-communications/) （Fastly檔案）

## 受影響的版本

* **雲端基礎結構上的Adobe Commerce：**
   * 版本： 2.1.4和更新版本
   * 計畫：雲端基礎結構上的Adobe Commerce雲端基礎結構上的入門計畫架構和Adobe Commerce Pro計畫架構（包括Pro Legacy）
* **Fastly：** 1.2.4

## 路由不需要變更.yaml

若要啟用HTTP至HTTPS的重新導向，請執行下列動作： **全部** 頁面時，您不需要將頁面新增至 `routes.yaml` 設定檔 — 僅需在整個存放區中啟用「強制TLS」 (使用Commerce管理員)即可。

## 相關Fastly檔案

* [Adobe Commerce 2的強制TLS指南](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [強制TLS重新導向](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [保護通訊安全](https://docs.fastly.com/guides/securing-communications/)
