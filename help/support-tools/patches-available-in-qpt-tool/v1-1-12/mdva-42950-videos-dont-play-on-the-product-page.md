---
title: MDVA-42950：影片不會在產品頁面上播放
description: MDVA-42950修補程式解決未在產品頁面上播放視訊的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-42950。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: e19e5ff0-9ddd-41de-b64b-4c3aef4d16a5
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-42950：影片不會在產品頁面上播放

MDVA-42950修補程式解決未在產品頁面上播放視訊的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-42950。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

未在產品頁面上播放影片。

<u>要再現的步驟</u>：

1. 導覽至&#x200B;**商店** > **設定** > **目錄** > **產品影片**，以設定YouTube API金鑰。
1. 將來自YouTube的視訊新增至任何可由父級設定的簡單產品中。
1. 在內容> **設計** > **組態** > **HTML標題** > **指令碼和樣式表**&#x200B;中新增HTML標題：

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. 前往PDP，並選取產品設定，以在像片與影片清單中檢視影片。
1. 嘗試播放視訊。

<u>預期結果</u>：

視訊正在播放。

<u>實際結果</u>：

視訊無法播放。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
