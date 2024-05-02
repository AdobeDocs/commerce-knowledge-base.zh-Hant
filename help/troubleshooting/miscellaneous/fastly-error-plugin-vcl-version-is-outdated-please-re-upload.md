---
title: 「Fastly錯誤：外掛程式VCL版本已過時！ 請重新上傳'
description: 當您看到訊息「*Plugin VCL版本已過時！ 請重新上傳。*" (在Commerce管理員的Fastly設定中)，因為尚未安裝最新的Fastly模組。
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Fastly錯誤：外掛程式VCL版本已過時！ 請重新上傳

本文提供當您看到訊息時的解決方案»*外掛程式VCL版本已過時！ 請重新上傳。*&quot;在Fastly設定中，在Commerce管理員中，由於未安裝最新的Fastly模組。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.2.x.、2.3.x<br>
Fastly：此錯誤可能會影響Fastly模組的所有版本，但最新版本除外。 如需最新版本的相關資訊，請參閱 [Fastly發行說明](https://github.com/fastly/fastly-magento2/releases) 在GitHub上。

## 問題

1. 登入Commerce管理面板。
1. 瀏覽至 **商店** > **設定** > **進階** > **系統** > **完整頁面快取**   **Fastly快取。**
1. 在 **自動上傳和服務啟用** 區段，將會有一個&quot;*外掛程式VCL版本已過時！ 請重新上傳。*」通知。
1. 您嘗試藉由按一下「上傳VCL至Fastly」按鈕來上傳VCL片段，但您仍會看到警告。*外掛程式VCL版本已過時！ 請重新上傳。*&quot;

## 原因

Fastly擴充功能已更新（連同隨附的VCL組態和範本），但更新的VCL組態尚未上傳到Fastly服務。 更新Adobe Commerce模組時 `Fastly_Cdn`，您必須再次將更新的VCL設定上傳到Fastly。

## 解決方案

1. 檢查是否已安裝最新的ECE-Tools，以及 [目前版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) （位於我們的開發人員檔案中）。 ECE-Tools的相依性中有Fastly套件的版本。

   這可能不是Fastly外掛程式的最新版本，但可能是比您目前安裝的版本更新的版本，最佳實務是安裝最新的ECE工具。

1. 如果您不在目前版本的ECE-Tools上，請依照下列步驟執行 [升級](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) （位於我們的開發人員檔案中）。
1. 升級ECE-Tools之後，檢查您是否擁有最新版本的 [Fastly外掛程式](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) 已安裝。
1. 如果Fastly外掛程式不是目前版本，請依照下列步驟執行 [將外掛程式升級至最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) （位於我們的開發人員檔案中）。

## 相關閱讀

* 如需有關設定和設定Fastly的資訊，請參閱 [設定Fastly服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) （位於我們的開發人員檔案中）。
* 如需有關Fastly的一般資訊，請參閱 [fastly.com](https://www.fastly.com/).
