---
title: 'MDVA-23764Magento修補程式：載入動態區塊時發生錯誤'
description: MDVA-23764Magento修補程式修正了中的錯誤
exl-id: b884ade6-f88d-4c79-8e84-5a59252abb75
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# MDVA-23764Magento修補程式：載入動態區塊時發生錯誤

MDVA-23764Magento修補程式修正了中的錯誤

```php
JsFooterPlugin.php
```

這會影響動態區塊的顯示。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13時，即可使用此修補程式。 請注意，問題已在Magento2.3.5中修正。

## 受影響的產品和版本

**此修補程式是針對Magento版本：** Magento Commerce Cloud2.3.3所建立。

**與Magento版本相容：** Magento Commerce和Magento Commerce Cloud2.3.2 - 2.3.4-p2。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟：</u>

嘗試載入類似以下內容的URL： https://\[magento domain\]/banner/ajax/load/。

<u>實際結果：</u>

擲回類似下列的錯誤： *未攔截的TypeError： strpos()預期引數1為字串，null指定於……（程式碼行）* 。

<u>預期結果：</u>

載入的URL沒有發生錯誤。

## 套用修補程式

如需如何套用QPT修補程式的說明，請根據您的Magento產品使用下列連結：

* Magento Commerce： DevDocs [使用品質修補程式工具套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* Magento Commerce Cloud： DevDocs [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) 。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用品質修補程式工具檢查是否有修補程式可用於您的Magento問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
