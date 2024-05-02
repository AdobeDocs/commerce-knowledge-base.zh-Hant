---
title: 'MDVA-36464：傳送無法在商店檢視層級運作的電子郵件設定'
description: MDVA-36464修補程式修正了在商店檢視層級傳送電子郵件設定無法運作的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21後，即可使用此修補程式。 修補程式ID為MDVA-36464。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464：傳送無法在商店檢視層級運作的電子郵件設定

MDVA-36464修補程式修正了在商店檢視層級傳送電子郵件設定無法運作的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.21。 修補程式ID為MDVA-36464。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.0-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件：</u>

安裝乾淨的Adobe Commerce。

<u>要再現的步驟</u>：

1. 建立其他網站、商店和商店檢視(在此範例中，第二個網站為 *website2*)。
1. 停用 **電子郵件通知** 位於中的全域層級 **儲存** > **設定** > **進階** > **系統** > **郵件傳送設定**.
1. 啟用 **電子郵件通知** 於 *website2* level (**停用電子郵件通訊** = *否*)。
1. 在「管理員」中，建立新使用者，並將其指派給 *website2*.
1. 在Admin中，在客戶編輯頁面上按一下 **重設密碼** 適用於上述在步驟4中建立的客戶。

<u>預期結果</u>：

兩者 **歡迎電子郵件** 和 **重設密碼電子郵件** 都會如預期傳送，因為 **停用電子郵件通訊** = *否* 適用於第二個網站(範例： *website2*)。

<u>實際結果</u>：

* 此 **歡迎電子郵件** 不會觸發建立新客戶之後。
* 此 **重設密碼電子郵件** 未觸發。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
