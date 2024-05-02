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

MDVA-29954修補程式可解決「新公司註冊要求」和「您已連結至公司」電子郵件來自錯誤電子郵件地址的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.8。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.3.5-p2、2.4.0和2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

使用B2B安裝Adobe Commerce **B2B功能** 和 **公司** 已啟用。

<u>要再現的步驟</u>：

1. 按一下 **建立帳戶** 店面的下拉式清單，然後選取 **建立新的公司帳戶**.
1. 填寫必填欄位，然後註冊帳戶。
1. 啟用 **公司** 從後端(**客戶** > **公司**)。
1. 檢查您用於註冊的電子郵件地址。
1. 設定 **公司管理員密碼** 依照電子郵件中的指示進行。
1. 使用登入前端 **公司管理員密碼**.
1. 建立新的 **公司使用者** 在 **我的帳戶** > **公司使用者** > **新增使用者**.
1. 前往 **商店** > **設定** > **一般商店電子郵件地址** > **一般連絡人**，並勾選 **寄件者電子郵件**.
1. 前往您用來註冊 **新使用者** 在步驟7中。

<u>預期結果</u>：

「您已連結至公司」電子郵件是從與 **寄件者電子郵件** 在步驟8中。

<u>實際結果</u>：

「您已連結至公司」電子郵件是從 **公司管理員** 電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
