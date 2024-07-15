---
title: 'MDVA-30599：customer_is_guest設定不正確'
description: MDVA-30599修補程式修正使用API建立的訪客報價錯誤地標示為已登入客戶的報價的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6後，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599：customer_is_guest設定不正確

MDVA-30599修補程式修正使用API建立的訪客報價錯誤地標示為已登入客戶的報價的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6時，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.4 - 2.4.0

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用API建立的訪客報價錯誤地標示為已登入客戶的報價。

<u>要再現的步驟</u>：

1. 在Adobe Commerce店面，以訪客使用者身分將產品新增到購物車。
1. 在您的Adobe Commerce DB中，找到對應的`quote_id_mask`。
1. 傳送API要求給來賓購物車的`quoteGuestCartRepositoryV1`購物車存放庫介面。 這可透過Swagger或cURL要求完成。

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>預期結果</u>：

回應時，您收到`"customer_is_guest": true`

<u>實際結果</u>：

回應時，您收到`"customer_is_guest": false`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 安裝修補程式後所需的其他步驟

此修補程式將對所有新客用車有效。 如果您需要修正現有的客用購物車，請為`quote.customer_id`為NULL的那些記錄設定`quote.customer_is_guest = 1`。 您可以執行類似下列的查詢：

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>我們強烈建議先在中繼/整合環境中測試查詢，然後再於生產環境中執行。 我們也建議在使用DB進行任何操作之前先進行最近的備份。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
