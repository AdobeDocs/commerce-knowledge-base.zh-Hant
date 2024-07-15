---
title: 「MDVA-32739修補程式：啟用非同步傳送時傳送的舊電子郵件」
description: MDVA-32739修補程式修正啟用[非同步電子郵件通知](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications)傳送舊銷售電子郵件的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2中修正。
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# MDVA-32739修補程式：啟用非同步傳送時傳送的舊電子郵件

MDVA-32739修補程式修正啟用[非同步電子郵件通知](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications)傳送舊銷售電子郵件的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 停用非同步電子郵件傳送。
1. 建立訂單，並確認電子郵件傳送失敗。
1. 啟用非同步傳送。

<u>預期結果</u>：

系統只會針對上次非同步傳送更新後建立的訂單、出貨、商業發票及銷退折讓單，傳送電子郵件。

<u>實際結果</u>：

系統會透過cronjob傳送舊電子郵件。

## 修正

透過修補程式包含的修正，Adobe Commerce將選取上次執行非同步傳送方法後建立的訂單，並將傳送此類訂單的電子郵件。

依預設，它會以–1天的位移進行選取。

您可以修改`di.xml`，將此值變更為–2天。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
