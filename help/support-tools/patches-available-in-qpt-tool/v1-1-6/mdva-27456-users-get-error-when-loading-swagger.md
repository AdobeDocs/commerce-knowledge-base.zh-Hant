---
title: MDVA-27456：使用者載入Swagger時發生錯誤
description: MDVA-27456修補程式修正使用者嘗試載入Swagger時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-27456。 請注意，問題已在Adobe Commerce 2.3.7中修正。
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456：使用者載入Swagger時發生錯誤

MDVA-27456修補程式修正使用者嘗試載入Swagger時發生錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-27456。 請注意，問題已在Adobe Commerce 2.3.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.3.5-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者載入Swagger時發生錯誤。

<u>要再現的步驟</u>：

前往`../swagger.`

<u>預期結果</u>：

Swagger會載入而不會發生任何錯誤。

<u>實際結果</u>：

使用者收到下列錯誤： *無法載入API定義*。 錯誤記錄檔包含：

*report.CRITICAL：報表識別碼： webapi-5ea9c6da19cb1；訊息： &quot;\DateTime&quot;引數型別無效。 請驗證引數，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
