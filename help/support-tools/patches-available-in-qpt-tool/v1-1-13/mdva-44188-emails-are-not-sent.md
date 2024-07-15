---
title: '''MDVA-44188：電子郵件不會傳送至包含''''的ID。-"`'
description: MDVA-44188修補程式修正電子郵件未傳送至包含'的電子郵件ID的問題。-'。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-44188。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 2abd300a-6cf3-4973-9b36-1bba7b578378
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-44188：電子郵件未傳送至包含&#39;&#39;的ID。-&quot;

MDVA-44188修補程式修正電子郵件未傳送至包含`.-`之電子郵件ID的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-44188。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法傳送電子郵件給使用者名稱中包含`.-`的電子郵件ID。

<u>要再現的步驟</u>：

1. 使用包含`.-`的電子郵件地址註冊客戶。 例如，`.-foo@example.com`。
1. 下訂單。

<u>預期結果</u>：

電子郵件識別碼包含`.-`的使用者會照常接收電子郵件。

<u>實際結果</u>：

電子郵件未傳送至包含`.-`的電子郵件識別碼。 錯誤記錄中顯示下列錯誤： *無法新增無效的電子郵件地址至郵寄佇列*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
