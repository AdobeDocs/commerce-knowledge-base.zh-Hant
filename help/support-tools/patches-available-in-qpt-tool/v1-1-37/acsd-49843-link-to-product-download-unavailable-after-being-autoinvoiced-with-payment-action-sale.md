---
title: 'ACSD 49843：使用[!UICONTROL Payment Action] = [!UICONTROL Intent Sale]自動開立發票後無法使用產品下載連結'
description: 套用ACSD-49843修補程式以修正Adobe Commerce的問題，即當[!UICONTROL Payment Action]設定為[!UICONTROL Intent Sale]時，訂購專案以線上付款方式自動開立商業發票後，無法取得產品下載連結。
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843：使用[!UICONTROL Payment Action] = [!UICONTROL Intent Sale]自動開立商業發票後無法使用產品下載連結

ACSD-49843修補程式修正當[!UICONTROL Payment Action]設定為[!UICONTROL Intent Sale]時，訂購專案以線上付款方式自動開立商業發票後，產品下載連結無法使用的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.37時，即可使用此修補程式。 修補程式ID為ACSD-49843。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當[!UICONTROL Payment Action]設定為[!UICONTROL Intent Sale]時，已訂購專案以線上付款方式自動開立商業發票後，產品下載連結無法使用。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce管理員並導覽至「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**」。

   * 在[!UICONTROL Payment Action]下拉式清單中，選取&#x200B;**[!UICONTROL Intent Sale]**，並將&#x200B;*[!UICONTROL Enable Card Payments]*&#x200B;設為&#x200B;*是*。

1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**」，並確定其已設為&#x200B;*「已開立商業發票」*。
1. 在店面，以客戶身分登入。

   * 新增任何可下載的產品和簡單產品至購物車。
   * 使用[!DNL Braintree Pay]以卡片選項下訂單。

1. 移至&#x200B;**[!UICONTROL My Orders]**，檢視是否已針對訂單自動建立發票，且兩個專案狀態為&#x200B;*「已開立商業發票」*。
1. 移至&#x200B;**[!UICONTROL My Downloadable Products]**&#x200B;並觀察下載連結目前無法使用。
1. 在Admin中，移至該訂單並建立其出貨。
1. 在店面，前往&#x200B;**[!UICONTROL My Downloadable Products]**&#x200B;並觀察下載連結現在是否可用。

<u>預期結果</u>：

當可下載的產品狀態為&#x200B;*「已開發票」*&#x200B;時，可使用下載連結。

<u>實際結果</u>：

即使可下載的產品狀態顯示&#x200B;*「已開發票」*，下載連結仍無法使用。 只有在為實體產品建立出貨後，才能使用此功能。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
