---
title: 'ACSD-45781：行動裝置上未顯示商店前端搜尋欄位'
description: MDVA-45781修補程式可解決行動裝置上未顯示商店前端搜尋欄位的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19後，即可使用此修補程式。 修補程式ID為MDVA-45781。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 0ae90f6d-1c04-4599-b21d-4d02fd6b36db
feature: Cache, Native Luma Frontend Development, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-45781：行動裝置上未顯示商店前端搜尋欄位

MDVA-45781修補程式可解決行動裝置上未顯示商店前端搜尋欄位的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19時，即可使用此修補程式。 修補程式ID為MDVA-45781。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

行動裝置上未顯示商店前端搜尋欄位

<u>要再現的步驟</u>：

1. 前往Commerce Admin > **商店** > **設定** > **目錄** > **目錄搜尋**&#x200B;並設定：
   * 啟用搜尋Recommendations以&#x200B;*否*
   * 啟用搜尋建議給&#x200B;*否*
1. 按一下&#x200B;**儲存設定**&#x200B;按鈕。
1. 清除快取。
1. 使用標準Luma主題，使用行動裝置瀏覽。
1. 按一下&#x200B;**搜尋**&#x200B;按鈕。

<u>預期結果</u>：

輸入搜尋表單隨即出現。

<u>實際結果</u>：

沒有任何反應。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
