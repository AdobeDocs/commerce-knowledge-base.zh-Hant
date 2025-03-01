---
title: ACSD-53704：過期後誤算的獎勵點數餘額歷史記錄
description: 套用ACSD-53704修補程式，修正Adobe Commerce中在獎勵點到期日之後錯誤計算獎勵點餘額歷史記錄的問題。
feature: Rewards
role: Admin, Developer
exl-id: 5300cc22-0425-4467-b1e2-8bd799afb5fd
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-53704：過期後誤算的獎勵點數餘額歷史記錄

ACSD-53704修補程式修正了獎勵點到期日後獎勵點餘額歷史記錄計算錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39時，即可使用此修補程式。 修補程式ID為ACSD-53704。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在獎勵點數到期日之後，就會錯誤計算獎勵點數餘額歷史記錄。

<u>要再現的步驟</u>：

1. 在店面建立客戶。
1. 為不同到期日的客戶新增獎勵積分。
1. 檢查`magento_reward_history`表格，並將最新回報點數記錄的到期日設定為過去日期：

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. 在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]**&#x200B;和&#x200B;**[!UICONTROL Reward Points Balance]**&#x200B;中檢查獎勵歷史記錄格線。

<u>預期結果</u>：

獎勵積分餘額只會顯示未到期的積分。

<u>實際結果</u>：

獎勵積分餘額反映包含過期積分的金額。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
