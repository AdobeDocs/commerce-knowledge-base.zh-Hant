---
title: 'MDVA-23426Magento修補程式：從Outlook以附件形式傳送的電子郵件'
description: MDVA-23426Magento修補程式修正了透過MS Outlook的Magento，以附件形式傳送電子郵件的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13後，即可使用此修補程式。 請注意，問題已在Magento2.3.5中修正。
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# MDVA-23426Magento修補程式：從Outlook以附件形式傳送的電子郵件

MDVA-23426Magento修補程式修正了透過MS Outlook的Magento，以附件形式傳送電子郵件的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.13。 請注意，問題已在Magento2.3.5中修正。

## 受影響的產品和版本

**修正程式是針對Magento版本建立的：** Magento Commerce Cloud2.3.3。

**與Magento版本相容：** Magento Commerce和Magento Commerce Cloud2.3.3 - 2.3.4-p2。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

會以空白內文接收電子郵件，而內容會作為附件納入。

<u>先決條件：</u> Outlook/Exchange正作為使用者端/伺服器組合使用。

<u>要再現的步驟：</u> 1. 提交訂單，訂單通知或出貨通知已傳送。2.已收到電子郵件。

<u>實際結果：</u> 電子郵件會顯示空白內文，內容會以ATT\*標示的附件形式包含在電子郵件中。 <u>預期結果：</u>

所收到的電子郵件不含附件，且電子郵件正文包含內容。

## 套用修補程式

如需如何套用QPT修補程式的說明，請根據您的Magento產品使用下列連結：

* Magento Commerce： DevDocs [使用品質修補程式工具套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud： DevDocs [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) .

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [檢查修補程式，以找出品質Magento工具的問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
