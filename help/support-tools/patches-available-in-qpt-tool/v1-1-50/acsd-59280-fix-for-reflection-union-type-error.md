---
title: '''ACSD-59280： 2.4.4-pX安裝中的''ReflectionUnionType：：getName()''錯誤'''
description: 套用ACSD-59280修補程式以修正Adobe Commerce問題，此問題發生在安裝2.4.4-pX版本期間發生「呼叫未定義方法ReflectionUnionType：：getName()」錯誤。
feature: Install, Upgrade
role: Admin, Developer
source-git-commit: a7a42520c6c7d74e995d104271afa2b15b537de7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-59280： 2.4.4-pX安裝中有`ReflectionUnionType::getName()`個錯誤

ACSD-59280修補程式修正了在安裝2.4.4-pX版本期間發生`call to undefined method ReflectionUnionType::getName()`錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-59280。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

2.4.4-pX安裝期間發生`ReflectionUnionType::getName()`錯誤。

<u>要再現的步驟</u>：

使用&#x200B;*[!UICONTROL Composer]*&#x200B;執行全新安裝。

<u>預期結果</u>：

安裝程式會順利完成，而不會發生錯誤。

<u>實際結果</u>：

您在`setup:upgrade`處理序期間看到下列錯誤：

`Call to undefined method ReflectionUnionType::getName()`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
