---
title: '''MDVA-43824：訂單取消動作失敗，錯誤為「您尚未取消專案」'
description: '''MDVA-43824修補程式可解決訂單取消動作失敗的問題，並出現錯誤：*您尚未取消專案*。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-43824。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。'
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824：訂單取消動作失敗，錯誤為「您尚未取消專案」

MDVA-43824修補程式解決訂單取消動作失敗的問題，錯誤為： *您尚未取消專案*。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-43824。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p3、2.4.1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法取消由登入客戶所下的訂單。 訂單取消動作因下列錯誤而失敗：

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>要再現的步驟</u>：

1. 建立銷售規則（優惠券型態為「特定優惠券」或「無優惠券」）。
1. 前往店面，以客戶身分登入，然後將產品新增到購物車。
1. 如果購物車價格規則具有優惠券作為「特定優惠券」，請前往購物車並套用購物車價格規則。 購物車價格規則應已成功套用。
1. 前往結帳並使用任何付款方式下訂單。
1. 前往Commerce Admin > **銷售** > **訂單**。
1. 開啟步驟4中的訂單。
1. 按一下&#x200B;**取消**&#x200B;按鈕。

<u>預期結果</u>：

已成功取消訂單，沒有發生任何錯誤。

<u>實際結果</u>：

訂單取消動作失敗，錯誤如下： *您尚未取消專案。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
