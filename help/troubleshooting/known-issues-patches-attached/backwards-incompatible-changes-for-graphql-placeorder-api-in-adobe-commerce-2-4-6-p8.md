---
title: 「Adobe Commerce 2.4.6-p8中 [!DNL GraphQL] 'placeOrder' [!DNL API] 的回溯不相容變更」
promoted: true
description: 本文提供已知的Adobe Commerce 2.4.6-p8版雲端和內部部署問題的修補程式，其中'placeOrder' [!DNL GraphQL API] 未傳回預期的錯誤回應，如舊版2.4.6修補程式所示。 對於使用PWA店面或其他任何以 [!DNL GraphQL API]為基礎的店面的商家，這可能會導致結帳體驗中斷。
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Adobe Commerce 2.4.6-p8中[!DNL GraphQL] `placeOrder` [!DNL API]的回溯不相容變更

本文提供已知的Adobe Commerce 2.4.6-p8版雲端和內部部署問題的修補程式，其中`placeOrder` [!DNL GraphQL API]未傳回預期的錯誤回應，如舊版2.4.6修補程式所示。 對於使用[!DNL PWA]店面或其商店中任何其他以[!DNL GraphQL API]為基礎的店面的商家，這可能會導致結帳體驗中斷。

>[!NOTE]
>
>如果您在套用修補程式時遇到任何問題，請聯絡支援服務。

## 受影響的產品和版本

* 雲端上的Adobe Commerce 2.4.6-p8
* Adobe Commerce內部部署2.4.6-p8

## 問題

在Adobe Commerce 2.4.6-p8僅限安全性修補程式上升級後，[`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)不會傳回預期的錯誤回應，如任何先前的2.4.6修補程式版本中所見。 對於使用[!DNL PWA]店面或其商店中任何其他以[!DNL GraphQL API]為基礎的店面的商家，這可能會導致結帳體驗中斷。

<u>要再現的步驟</u>：

執行`placeOrder` [!DNL GraphQL]要求（您預期會有錯誤回應）。

<u>預期結果</u>：

您會收到預期的錯誤回應。

<u>實際結果</u>：

您收到的不是預期的錯誤回應，而是成功的回應，但新的`errors`金鑰看起來像這樣：

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## 適用於Adobe Commerce on Cloud和Adobe Commerce內部部署軟體的解決方案

若要解決此問題，請套用修補程式。
若要下載，請按一下以下連結：

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## 如何套用修補程式

解壓縮檔案，並參閱我們的支援知識庫中的[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hant)提供的撰寫器修補程式，以取得指示。

## 僅適用於Adobe Commerce on Cloud商家 — 如何判斷是否已套用修補程式

考慮到無法輕鬆檢查問題是否已修補，您可能想要檢查是否已成功套用修補程式。

<u>您可以執行下列步驟，以範例檔案`VULN-27015-2.4.7_COMPOSER.patch` **為例</u>**：

1. [安裝 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant)。
1. 執行命令： <br>
   ![ac-13283-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您應該會看到類似以下的輸出，其中VULN-27015傳回&#x200B;*已套用*&#x200B;狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

