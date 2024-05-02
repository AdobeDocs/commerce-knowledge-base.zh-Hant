---
title: 「MDVA-37725：透過非預設網站傳送的電子郵件包含預設網站的標誌URL」
description: MDVA-37725修補程式修正了透過包含預設網站之標誌URL的非預設網站傳送非同步訂購電子郵件的問題。
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725：透過非預設網站傳送的電子郵件包含預設網站的標誌URL

>[!WARNING]
>
> MDVA-37725修補程式已過時。

MDVA-37725修補程式修正了透過包含預設網站之標誌URL的非預設網站傳送非同步訂購電子郵件的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.1.4。 修補程式ID為MDVA-37725。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

非同步訂購電子郵件會透過包含預設網站標誌URL的非預設網站傳送。

<u>必要條件</u>：

1. 第二個網站/商店/商店檢視必須已建立。
1. **非同步傳送** 必須從以下位置啟用設定： **商店** > **設定** > **設定** > **銷售** > **銷售電子郵件** > **一般設定**.
1. **將商店代碼新增至URL** 已開啟設定，以便從存取次要網站 **商店** > **設定** > **設定** > **URL選項**.

<u>要再現的步驟</u>：

1. 從第一家和第二家商店下訂單。
1. 執行cron以傳送銷售電子郵件。
1. 檢查來自第二個網站的電子郵件。

<u>預期結果</u>：

電子郵件的標誌URL包含第二個網站的URL。

<u>實際結果</u>：

電子郵件的標誌URL包含預設網站的URL。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
