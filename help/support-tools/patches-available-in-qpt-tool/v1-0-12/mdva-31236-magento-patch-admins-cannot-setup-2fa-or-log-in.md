---
title: 'MDVA-31236：管理員無法設定2FA或登入'
description: MDVA-31236修補程式修正了具有自訂資源存取權的Commerce管理員使用者無法設定[雙因素驗證(2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)或登入的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12後，即可使用此修補程式。
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236：管理員無法設定2FA或登入

MDVA-31236修補程式修正具有自訂資源存取權的Commerce管理員使用者無法設定[雙因素驗證(2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)或登入的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12時，即可使用此修補程式。

## 受影響的產品和版本

**在雲端基礎結構2.4.0上為Adobe Commerce版本** Adobe Commerce建立修補程式。

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.4.0-2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

沒有管理員許可權的使用者目前無法設定其個人2FA存取權。 2FA如在Adobe Commerce中實作，包含兩個ACL角色。 一個角色會影響全域系統組態，只有在設定系統時才需要這個角色。 第二個ACL角色會影響個別使用者2FA帳戶。 管理員使用者需要設定第二種型別的2FA ACL。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
