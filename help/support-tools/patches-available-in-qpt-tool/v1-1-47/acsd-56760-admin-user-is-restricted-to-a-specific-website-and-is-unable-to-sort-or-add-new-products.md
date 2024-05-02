---
title: 「ACSD-56760：管理員使用者僅限於特定網站，無法排序或新增產品」
description: 套用ACSD-56760修補程式來修正Adobe Commerce問題，該問題導致僅限特定網站的管理員使用者無法排序或新增產品，以致於網路商店擁有自己的根類別。
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760：管理員使用者僅限於特定網站，無法排序或新增產品

ACSD-56760修補程式修正僅限特定網站的Admin使用者無法排序或新增類別（萬一網站商店有自己的根類別）中的新產品問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.47。 修補程式ID為ACSD-56760。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

僅限特定網站使用的管理員使用者，如果網站商店擁有自己的根類別，則無法在類別內排序或新增產品。

<u>要再現的步驟</u>：

1. 建立 *2* 網站。
1. 建立 **[!UICONTROL restricted admin user]** 僅具有存取權 *1* 網站。
1. 登入身份 **[!UICONTROL restricted admin user]** 並嘗試變更類別中的產品位置。

*案例1*：

* *2* 商店。
* *2* 根類別，指派給每個網站的類別根目錄。

*案例2*：

* *2* 商店。
* 僅限 *1* 根類別會指派給兩個網站。

<u>預期結果</u>：

* *案例1*：受限制的管理員應該能夠排序可用類別中的產品。
* *案例2*：受限制的管理員無法排序可用類別中的產品，因為這也會影響受限制的商店。

<u>實際結果</u>：

* *案例1*：受限制的管理員無法排序可用類別中的產品。
* *案例2*：受限制的管理員可以對可用類別中的產品排序，從而影響受限制的商店。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
