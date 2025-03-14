---
title: ACSD-54007：匯入客戶資料時出現未定義的陣列機碼範圍錯誤(_S)
description: 套用ACSD-54007修補程式，修正匯入客戶資料時顯示「未定義陣列機碼_scope」錯誤的Adobe Commerce問題。
feature: Data Import/Export
role: Admin, Developer
exl-id: b14a14fd-5021-460f-8ca9-c9845859df97
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-54007：匯入客戶資料時出現未定義的陣列機碼範圍錯誤(_S)

ACSD-54007修補程式修正匯入客戶資料時發生&#x200B;*未定義的陣列機碼_scope*&#x200B;錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40時，即可使用此修補程式。 修補程式ID為ACSD-54007。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯入客戶資料時，您會看到&#x200B;*未定義的陣列索引鍵_scope*&#x200B;錯誤。

<u>要再現的步驟</u>：

1. 前往Commerce管理員> **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**，將&#x200B;**[!UICONTROL Entity Type]**&#x200B;設定為&#x200B;**[!UICONTROL Stock Sources]**&#x200B;並匯入庫存來源csv檔案（包含原始碼、SKU、數量和狀態）。
1. 選擇「客戶和地址」（單一檔案），然後嘗試匯入csv檔案，其中包含客戶的詳細地址資訊。

<u>預期結果</u>：

您沒有收到任何錯誤。

<u>實際結果</u>：

您收到下列錯誤： *警告： /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php第84*&#x200B;行中未定義的陣列機碼「_scope」

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
