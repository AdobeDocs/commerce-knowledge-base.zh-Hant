---
title: 'MDVA-42855：結帳時未將新的客戶地址儲存到通訊錄'
description: MDVA-42855修補程式修正結帳時新客戶地址未儲存至通訊錄的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-42855。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 37fc51f4-773e-4bef-9fb1-e6629562b94a
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-42855：結帳時沒有將新的客戶地址儲存到通訊錄

MDVA-42855修補程式修正結帳時新客戶地址未儲存至通訊錄的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-42855。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳時，新的客戶地址不會儲存到通訊錄。

<u>要再現的步驟</u>：

1. 建立客戶帳戶並更新預設的出貨與帳單地址。
1. 新增產品至購物車，並導覽至結帳頁面。
1. 送貨時，按一下&#x200B;**+新地址**。
1. 輸入您的新地址，並保留&#x200B;**儲存於通訊錄**&#x200B;核取方塊。
1. 在付款時，勾選「**我的帳單和送貨地址相同**」核取方塊。
1. 下訂單。
1. 檢查通訊錄。

<u>預期結果</u>：

新的送貨地址會儲存在通訊錄中。

<u>實際結果</u>：

新的送貨地址未儲存在通訊錄中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
