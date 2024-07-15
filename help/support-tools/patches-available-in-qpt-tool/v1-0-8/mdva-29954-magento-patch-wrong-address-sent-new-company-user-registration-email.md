---
title: 'MDVA-29954：傳送新公司使用者註冊電子郵件的地址錯誤'
description: MDVA-29954修補程式可解決「新公司註冊要求」和「您已連結至公司」電子郵件來自錯誤電子郵件地址的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954：傳送新公司使用者註冊電子郵件的地址錯誤

MDVA-29954修補程式可解決「新公司註冊要求」和「您已連結至公司」電子郵件來自錯誤電子郵件地址的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.3.5-p2、2.4.0和2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

安裝Adobe Commerce，其中包含B2B，並啟用&#x200B;**B2B功能**&#x200B;和&#x200B;**公司**。

<u>要再現的步驟</u>：

1. 按一下店面上的&#x200B;**建立帳戶**&#x200B;下拉式清單，然後選取&#x200B;**建立新的公司帳戶**。
1. 填寫必填欄位，然後註冊帳戶。
1. 從後端（**客戶** > **公司**）啟用&#x200B;**公司**。
1. 檢查您用於註冊的電子郵件地址。
1. 依照電子郵件中的指示設定&#x200B;**公司管理員密碼**。
1. 使用&#x200B;**公司管理員密碼**&#x200B;登入前端。
1. 在&#x200B;**我的帳戶** > **公司使用者** > **新增使用者**&#x200B;中建立新的&#x200B;**公司使用者**。
1. 移至&#x200B;**商店** > **設定** > **一般商店電子郵件地址** > **一般連絡人**，並檢查&#x200B;**寄件者電子郵件**。
1. 移至您在步驟7中用來註冊&#x200B;**新使用者**&#x200B;的電子郵件。

<u>預期結果</u>：

「您已連結至公司」電子郵件是從與步驟8中的&#x200B;**寄件者電子郵件**&#x200B;具有相同值的電子郵件地址傳送。

<u>實際結果</u>：

「您已連結至公司」電子郵件是從&#x200B;**公司管理員**&#x200B;電子郵件傳送。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
