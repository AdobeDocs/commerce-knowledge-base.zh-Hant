---
title: 'MDVA-32313修補程式：產品已新增至包含錯誤設定的願望清單'
description: MDVA-32313修補程式可解決無法正確將可設定產品新增至願望清單的問題，因為可設定產品新增至願望清單時，會指派錯誤的設定。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313修補程式：產品已新增至包含錯誤設定的願望清單

MDVA-32313修補程式可解決無法正確將可設定產品新增至願望清單的問題，因為可設定產品新增至願望清單時，會指派錯誤的設定。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.10。 請注意，Adobe Commerce 2.4.2版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.0

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.3.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 建立客戶。
1. 登入客戶帳戶。
1. 導覽至 **產品清單** 頁面。
1. 選擇可設定的產品(例如： *configurable\_1* )並選取「 」上偏好的顏色和大小選項 **產品清單** 頁面(**請勿開啟產品頁面。**)。
1. 按一下其他可設定產品的願望清單圖示(例如： *configurable\_2*)，而不需選取任何顏色/大小選項。

<u>預期結果</u>：

此 *configurable\_2* 產品會如預期新增到願望清單，但未選取任何選項。

<u>實際結果</u>：

此 *configurable\_2* 產品已新增到願望清單，其設定來自 *configurable\_1* 產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
