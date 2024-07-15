---
title: 'MDVA-35910：停用「以客戶身分登入」時表單驗證中斷'
description: MDVA-35910修補程式解決停用**以客戶身分登入**擴充功能時，建立客戶帳戶表單驗證中斷的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-35910。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910：停用「以客戶身分登入」時表單驗證中斷

MDVA-35910修補程式可解決當&#x200B;**以客戶身分登入**&#x200B;擴充功能停用時，建立客戶帳戶表單驗證中斷的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19時，即可使用此修補程式。 修補程式ID為MDVA-35910。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.1-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 瀏覽至&#x200B;**商店>設定>客戶**。 停用Admin中的&#x200B;**以客戶**&#x200B;身分登入。
1. 在&#x200B;**以Customer**&#x200B;身分登入，設定&#x200B;**啟用延伸模組** = *否*。
1. 儲存設定，並排清快取。
1. 導覽回店面，然後按一下&#x200B;**註冊** （建立客戶帳戶）。
1. 填寫帳戶表單，然後確認&#x200B;**確認電子郵件**&#x200B;下的驗證是否正常運作。

<u>預期結果</u>：

客戶帳戶建立處理完成，且沒有錯誤。

<u>實際結果</u>：

客戶帳戶建立程式未完成，而是顯示javascript主控台錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
