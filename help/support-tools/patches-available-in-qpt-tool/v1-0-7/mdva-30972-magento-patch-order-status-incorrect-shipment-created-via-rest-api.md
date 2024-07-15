---
title: 'MDVA-30972：訂單狀態透過REST API建立的出貨不正確'
description: MDVA-30972修補程式可解決透過REST API建立出貨期間，訂單狀態變更不正確的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972：訂單狀態透過REST API建立的出貨不正確

MDVA-30972修補程式可解決透過REST API建立出貨期間，訂單狀態變更不正確的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0至2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當管理員透過REST API為具有&#x200B;*疑似詐騙*&#x200B;訂單狀態的訂單建立部分出貨時，訂單狀態會變更為&#x200B;*處理*。 它應該保留在&#x200B;*可疑的詐騙*。

<u>必要條件</u>：

* 已設定PayPal EC或其他線上付款方式。
* 已設定REST API的整合。

<u>要再現的步驟</u>：

1. 建立包含兩個或多個專案的訂單。
1. 登入&#x200B;**管理員** > **銷售** > **訂單**。 開啟您剛建立的訂單。
1. 在訂單詳細資訊頁面上，向下捲動至&#x200B;**訂單總計**。 按一下&#x200B;**狀態**&#x200B;下拉式清單，並選取&#x200B;*可疑詐騙*。 然後按一下&#x200B;**提交註解**&#x200B;按鈕。
1. 立即檢查訂單是否有&#x200B;*疑似詐騙*&#x200B;狀態。
1. 使用REST API從訂單中建立一個料號的出貨：

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. 再次在「管理員」中開啟訂單，並檢查其狀態。

<u>預期結果</u>：

* 訂單狀態= *疑似詐騙*。
* 如果從「管理員」建立相同的出貨，則訂單狀態不會變更。

<u>實際結果</u>：

訂單狀態= *處理中*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
