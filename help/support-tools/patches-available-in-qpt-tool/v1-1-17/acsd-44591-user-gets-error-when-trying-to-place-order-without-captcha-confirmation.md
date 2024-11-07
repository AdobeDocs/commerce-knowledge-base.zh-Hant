---
title: 「ACSD-44591：訂單未通過驗證碼確認時發生錯誤」
description: ACSD-44591修補程式解決使用者嘗試下訂單時未經過驗證碼確認會發生錯誤的問題。
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591：未進行驗證碼確認的訂單發生錯誤

ACSD-44591修補程式解決使用者嘗試下訂單時未經過驗證碼確認會發生錯誤的問題。
安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-44591。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者嘗試在未進行驗證碼確認的情況下下訂單時出現錯誤。

<u>要再現的步驟</u>：

1. 設定Google ReCaptcha v2 （我不是自動機制）。
1. 啟用ReCaptcha以進行簽出。
1. 嘗試下單而不按一下ReCaptcha。
1. 收到遺失ReCaptcha （*ReCaptcha驗證失敗，請再試一次*）的錯誤訊息後，請按一下&#x200B;**ReCaptcha**，然後嘗試下訂單。

<u>預期結果</u>：

使用不正確的ReCaptcha將不會下訂單。

<u>實際結果</u>：

您會收到下列錯誤：

* *ReCaptcha驗證失敗，請再試一次*
* *沒有識別碼= 1*&#x200B;的此類購物車

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
