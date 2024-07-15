---
title: 「MDVA-28661：變更管理員電子郵件時公司使用者管理的問題」
description: MDVA-28861修補程式修正使用者變更管理員電子郵件時出現錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5後，即可使用此修補程式。 修補程式ID為MDVA-28861。
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661：變更管理員電子郵件時公司使用者管理的問題

MDVA-28861修補程式修正使用者變更管理員電子郵件時出現錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5時，即可使用此修補程式。 修補程式ID為MDVA-28861。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.0到2.4.1 （包括2.3.5-p1）搭配B2B擴充功能

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

變更&#x200B;**公司管理員**&#x200B;電子郵件地址後，會傳回錯誤，且不會顯示&#x200B;**公司使用者**&#x200B;清單。

<u>要再現的步驟</u>：

1. 啟用公司功能(如需詳細資訊，請參閱[安裝B2B：在開發人員檔案中的Commerce管理員](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin)中啟用B2B功能，並建立擁有兩個使用者（一個管理員和兩個使用者）的新公司，且所有使用者都有電子郵件地址)。
1. 前往&#x200B;**Commerce管理員** > **客戶** > **公司**，並開啟您的公司帳戶。
1. 開啟「**公司管理員**」標籤，並將管理員變更為第一個使用者，其中包括將「**公司管理員**」電子郵件變更為第一個使用者的電子郵件。
1. 前往Adobe Commerce前端，並以第一個使用者的身分登入。
1. 移至&#x200B;**公司使用者**&#x200B;區段。

<u>預期結果</u>：

**公司使用者**&#x200B;清單應按預期顯示。

<u>實際結果</u>：

未顯示&#x200B;**公司使用者**&#x200B;清單，且顯示類似下列的錯誤：

```bash
No such entity with id = 2
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。

若要深入瞭解B2B公司功能，請參閱我們的開發人員檔案中的下列文章：

* [B2B開發人員指南](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [管理公司角色](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B擴充功能組態路徑參考](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
