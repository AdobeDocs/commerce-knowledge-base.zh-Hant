---
title: ACSD-49497：訂單在出貨後仍在處理，且已部分退款
description: 套用ACSD-49497修補程式，以修正Adobe Commerce問題，此問題的訂單狀態在出貨後仍維持為處理狀態，且已套用部分退款。
exl-id: d195bcf4-bb8b-4373-8aad-a5b953b07443
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-49497：訂單在出貨後仍在處理，且已部分退款

ACSD-49497修補程式修正了訂單狀態在出貨後仍為處理且套用部分退款的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-49497。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使在出貨後，新訂單的狀態仍維持在&#x200B;*[!UICONTROL Processing]*&#x200B;狀態，且已套用部分退款。

<u>要再現的步驟</u>：

1. 建立含有多個專案的訂單。
1. 從&#x200B;**[!UICONTROL Admin]**，建立訂單的商業發票。
1. 從&#x200B;**[!UICONTROL Admin]**&#x200B;建立銷退折讓單，並只退款部份的專案。
1. 從&#x200B;**[!UICONTROL Admin]**，要求運送訂單中剩餘的專案。
1. 觀察訂單狀態。

<u>預期結果</u>：

訂單的狀態應為&#x200B;*[!UICONTROL Complete]*。

<u>實際結果</u>：

訂單的狀態仍為&#x200B;*[!UICONTROL Processing]*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
