---
title: 'ACSD-51899：預設送貨地址自動填入不正確'
description: 套用ACSD-51899修補程式，修正Adobe Commerce中預設送貨地址自動填入錯誤地址的問題。
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899：預設送貨地址自動填入不正確

ACSD-51899修補程式修正了預設送貨地址自動填入錯誤地址的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.35。 修補程式ID為ACSD-51899。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

預設送貨地址自動填入錯誤的地址

<u>要再現的步驟</u>：

1. 啟用 **店內取貨** 在送貨方式下。
1. 建立 *stock* 和 *來源*.
1. 建立產品並將產品指派給來源。
1. 新增產品至購物車。
1. 按一下 **繼續結帳** 從迷你購物車。
1. 輸入測試電子郵件地址並選取 **在商店中挑選**.
1. 按一下 **選取存放區** 按鈕，並選取要挑選的商店位置。
1. 按一下 **下一個** 按鈕。
1. 導覽至 **首頁** 按一下商店標誌。
1. 開啟 **迷你購物車**.
1. 按一下底部的超連結，命名為 **檢視和編輯購物車**.
1. 按一下 **繼續結帳**.
1. 按一下送貨頁面上的送貨按鈕。

<u>預期結果</u>

送貨位址列位保持空白，但 *國家、地區和郵遞區號*.

<u>實際結果</u>

預設送貨地址會自動填入 *店內取貨* 重新整理頁面後的地址。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
