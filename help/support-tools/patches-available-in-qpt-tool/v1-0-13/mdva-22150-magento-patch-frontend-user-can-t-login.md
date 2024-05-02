---
title: 「MDVA-22150 Adobe Commerce修補程式：前端使用者無法登入」
description: MDVA-22150修補程式可解決前端使用者在使用抵用券中止購買後無法登入的問題。 當前端使用者在完成購買前在已停用的產品上使用優惠券代碼時，就會發生這種情況。 結果是前端使用者無法再登入且會收到503錯誤。 此問題的另一個影響是，在管理員中管理客戶購物車的功能停止運作。
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-22150 Adobe Commerce修補程式：前端使用者無法登入

MDVA-22150修補程式可解決前端使用者在使用抵用券中止購買後無法登入的問題。 當前端使用者在完成購買前在已停用的產品上使用優惠券代碼時，就會發生這種情況。 結果是前端使用者無法再登入且會收到503錯誤。 此問題的另一個影響是，在管理員中管理客戶購物車的功能停止運作。

此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.13。 請注意，Adobe Commerce 2.3.4版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.2

**與Adobe Commerce版本相容：** 雲端基礎結構和Adobe Commerce 2.3.1上的Adobe Commerce - 2.3.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟：</u>

1. 登入管理員並建立可設定的產品。
1. 前往 **購物車規則**，並建立包含折扣的優惠券代碼。
1. 在前端建立客戶帳戶。
1. 將產品新增至購物車、依照結帳程式進行，然後輸入優惠券。
1. 輸入抵用券後，請勿提交訂單，但會中止訂單並登出。
1. 返回「管理員」並停用整個可設定產品。

<u>預期結果：</u>

產品未顯示在店面的購物車中，或顯示產品已如預期停用的適當錯誤訊息。

<u>實際結果：</u>

* 嘗試重新登入前端時，您會陷入無限回圈（這最終會在一段較長的時間後顯示例外狀況）。
* 在管理員中管理客戶的購物車功能停止運作。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
