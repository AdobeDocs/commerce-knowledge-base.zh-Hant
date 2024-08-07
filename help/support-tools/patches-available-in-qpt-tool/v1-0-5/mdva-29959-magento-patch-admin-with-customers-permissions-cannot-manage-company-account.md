---
title: 「MDVA-29959修補程式：具有「客戶」許可權的管理員無法管理公司帳戶」
description: '[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版中提供的MDVA-29959修補程式修正了具有「客戶」ACL所有許可權的受限制管理員使用者無法管理公司（新增或刪除公司）的問題。 請注意，此問題已在Adobe Commerce 2.3.4的B2B中修正。'
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# MDVA-29959修補程式：具有「客戶」許可權的管理員無法管理公司帳戶

[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版中提供的MDVA-29959修補程式，修正了具有「客戶」ACL所有許可權的受限制管理員使用者無法管理公司（新增或刪除公司）的問題。 請注意，此問題已在Adobe Commerce 2.3.4的B2B中修正。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce的B2B 2.3.0-2.3.3-p1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

擁有「客戶」ACL所有許可權的管理員使用者無法管理公司（新增或刪除公司）。

<u>要再現的步驟</u>

1. 在Commerce管理員中，建立新的管理員角色，並將使用者指派給該角色。
1. 僅指派「客戶」資源給角色。
1. 以此角色的使用者身分登入。
1. 請嘗試刪除公司帳戶。

<u>預期結果：</u>

已成功刪除公司帳戶。

<u>實際結果：</u>

您無法刪除公司帳戶。 您收到&#x200B;*很抱歉，您需要許可權才能檢視此內容。*&#x200B;錯誤訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
