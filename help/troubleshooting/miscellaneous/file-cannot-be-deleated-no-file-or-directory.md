---
title: 「無法刪除檔案。 警告！ unlink：沒有這類檔案或目錄錯誤 [!DNL Admin]"
description: 本文提供發生錯誤*無法刪除檔案之問題的解決方案。 警告！取消連結沒有這樣的檔案或目錄錯誤* [!DNL Admin] 當您執行 [!DNL Javascript/CSS] 排清。
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *無法刪除檔案。 警告！unlink：沒有這類檔案或目錄錯誤* 從 [!DNL Admin]

本文提供出現錯誤問題的解決方案 *無法刪除檔案。 警告！unlink：沒有這類檔案或目錄錯誤* 從 [!DNL Commerce Admin] 當您執行 [!DNL JavaScript/CSS] 排清。

## 受影響的產品和版本

* Adobe Commerce 2.4.0 - 2.4.6、所有部署方法

## 問題

當您執行時，會發生錯誤 [!DNL JS/CSS] 排清：

*無法刪除「/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b」檔案。 警告！unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b)：沒有這樣的檔案或目錄*

或：您會在下列位置看到上述錯誤： [!DNL Admin]、和/或中的類似錯誤 [!DNL New Relic] 或在部署記錄檔中。

或者：您無法存取進階報告，且analytics_collect_data cron作業失敗並出現此錯誤：

*無法刪除「/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0」檔案。 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0)：沒有這樣的檔案或目錄*

<u>要再現的步驟：</u>

方法1：

1. 登入 [!DNL Admin].
1. 前往 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 按一下 **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

方法2：

1. 登入 [!DNL Admin].
1. 前往 **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. 變更 [!UICONTROL Base URL] 或 [!UICONTROL Base URL (Secure)].
1. 按一下 **[!UICONTROL Save Config]**.

## 解決方案

如果您使用Adobe Commerce雲端基礎結構，並擁有 [!DNL magento/magento-cloud-patches] 已安裝的1.0.22包含修補程式，您不需要另外安裝ACSD-50165。

雲端基礎結構上的Adobe Commerce：將Commerce的雲端修補程式升級至1.0.22 (**或更新版本**)，其中包含此修正： [Commerce雲端修補程式](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce內部部署：套用ACSD-50165，使用 [品質修補程式工具>使用狀況](/docs/commerce-operations/tools/quality-patches-tool/usage.html). ACSD-50165修補程式隨附 [!DNL QPT] [v1.1.30。](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## 相關閱讀

* [[!DNL Quality Patches Tool] >發行說明](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) Commerce工具指南中的。
* [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) Commerce工具指南中的。
