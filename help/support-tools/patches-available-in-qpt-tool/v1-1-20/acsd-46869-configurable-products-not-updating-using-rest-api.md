---
title: 「ACSD-46869：可設定的產品未在結帳時使用REST API進行更新」
description: ACSD-46869修補程式修正了可設定產品在結帳時未使用REST API更新的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20後，即可使用此修補程式。 修補程式ID為ACSD-46869。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869：可設定的產品未在簽出時使用REST API進行更新

ACSD-46869修補程式修正了可設定產品在結帳時未使用REST API更新的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.20。 修補程式ID為ACSD-46869。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL QPT] 登陸頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

結帳期間不會使用REST API更新可設定的產品。

<u>要再現的步驟</u>：

1. 使用顏色和大小屬性建立可設定的產品。
1. 選取 **[!UICONTROL Options]** 並將產品新增至購物車。
1. 前往 **[!UICONTROL Checkout]**，除了數量外多次更新大小，然後檢查請求和回應。
1. 當您更新大小時，會得到下列回應。

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>預期結果</u>：

會根據變更更新值。

<u>實際結果</u>：

`option_value` 不會更新，因此下訂單時，其大小值會變舊。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tools] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在「品質修補工具」指南中。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) 在我們的支援知識庫中。

有關中可用的其他修補程式的資訊 [!DNL QPT]，請參閱 [中可用的修補程式 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在「品質修補工具」指南中。
