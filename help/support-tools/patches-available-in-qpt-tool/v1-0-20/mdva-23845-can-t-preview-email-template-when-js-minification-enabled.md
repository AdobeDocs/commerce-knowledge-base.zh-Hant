---
title: 「MDVA-23845：啟用JS縮制時無法預覽電子郵件範本」
description: MDVA-23845Magento修補程式修正啟用JS縮制時，無法在Admin中預覽電子郵件範本的問題。
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# mdva-23845：啟用JS縮制時無法預覽電子郵件範本

MDVA-23845Magento修補程式修正啟用JS縮制時，無法在Admin中預覽電子郵件範本的問題。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-23845。 請注意，問題已在Magento版本2.3.5中修正。

## 受影響的產品和版本

**此修補程式是針對Magento版本：** Magento Commerce Cloud2.3.3所建立

**與Magento版本相容：** Magento Commerce和MagentoCommerce Cloud2.3.2-2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u> ：

1. 在&#x200B;**管理員>商店>設定> JavaScript設定>縮制JavaScript檔案** = *是*&#x200B;中啟用&#x200B;**JS縮制**。
1. 將Magento切換至生產模式。
1. 移至&#x200B;**管理員>行銷>通訊>電子郵件範本** 。
1. 按一下「**新增範本**」。
1. 選取&#x200B;**新訂單**&#x200B;範本。
1. 按一下&#x200B;**載入範本**&#x200B;按鈕。
1. 以&#x200B;**新訂單**&#x200B;填滿&#x200B;**範本名稱**。
1. 按一下&#x200B;**儲存範本**&#x200B;按鈕。
1. 在電子郵件範本格線中，按一下&#x200B;**動作**&#x200B;欄中的&#x200B;**預覽**&#x200B;連結。

<u>預期結果</u> ：

電子郵件範本預覽會如預期顯示在開啟的快顯視窗中。

<u>實際結果</u> ：

電子郵件範本預覽未出現在開啟的快顯視窗中。 彈出式視窗是空的，可能會出現JS錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的Magento產品使用下列連結：

* Magento Commerce： DevDocs [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) 。
* Magento Commerce Cloud： DevDocs [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) 。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [檢查修補程式，以找出品質修補程式工具的Magento問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
