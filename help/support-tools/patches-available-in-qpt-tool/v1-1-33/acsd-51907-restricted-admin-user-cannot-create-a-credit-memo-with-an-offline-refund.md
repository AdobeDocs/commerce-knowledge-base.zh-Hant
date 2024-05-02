---
title: 「ACSD-51907：受限制的管理員使用者無法建立離線退款的銷退折讓單」
description: 套用ACSD-51907修補程式以修正Adobe Commerce限制管理員使用者無法以離線退款建立銷退折讓單的問題。
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907：受限制的管理員使用者無法建立離線退款的銷退折讓單

ACSD-51907修補程式修正受限管理員使用者無法以離線退款建立銷退折讓單的效能問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.33。 修補程式ID為ACSD-51907。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限管理員使用者無法以離線退款建立銷退折讓單。

<u>要再現的步驟</u>：

1. 建立 **客戶** 預設網站上的。
1. 建立 **新網站** 相關 *儲存* 和 *存放區檢視*.
1. 將預設網站設定為新網站，清除快取。
1. 變更客戶組態： **管理員** > **儲存** > **設定** > **客戶** > **客戶組態** > **共用客戶帳戶=全域**.
1. 建立新的管理員使用者角色，並將角色範圍設定為新建立的網站 *（僅存取銷售資料）* 在 **管理員** > **系統** > **許可權**.
1. 使用此角色建立新的管理員帳戶。
1. 使用線上付款方式建立新訂單 *(例如Auth.net或PayPal)*.
1. 以受限制的管理員使用者身分登入。
1. 前往 **銷售** > **訂購** >然後 **訂單檢視頁面**.
1. 建立發票。
1. 切換作業選項至「商業發票」頁標。
1. 按一下 **發票**.
1. 按一下 **[!UICONTROL Credit Memo]**.
1. 檢查 **[!UICONTROL Refund to Store Credit]** 核取方塊，將附近的文字欄位設為 *1* 值。
1. 按一下 **[!UICONTROL Refund Offline]** 按鈕。

<u>預期結果</u>：

已建立銷退折讓單，並且 *$1* 已退款至商店點數。

<u>實際結果</u>：

錯誤訊息， *需要更多許可權才能檢視此專案* 隨即顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
