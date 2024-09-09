---
title: 「ACSD-60303：啟用HTML縮制後，管理員訂單放置問題已解決」
description: 套用ACSD-60303修補程式以修正Adobe Commerce問題，若啟用HTML縮制，則無法發出管理員訂單。
feature: Orders
role: Admin, Developer
source-git-commit: d087c7428307fa2c362986b0569db30618c5233a
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-60303：啟用HTML縮制後，管理員訂單放置問題已解決

ACSD-60303修補程式修正啟用HTML縮制後，無法發出管理員訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-60303。 請注意，此問題已排程在2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p9 - 2.4.4-p10、2.4.5-p8 - 2.4.5-p9、2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用HTML縮制時，無法從管理員面板下訂單。

<u>要再現的步驟</u>：

1. 啟用HTML縮制。
1. 將&#x200B;**[!UICONTROL Application Mode]**&#x200B;設為&#x200B;*[!UICONTROL Production]*。
1. 從「管理員」面板建立訂單。

<u>預期結果</u>：

已成功下訂單。

<u>實際結果</u>：

未建立訂單，且會記錄以下錯誤：

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。