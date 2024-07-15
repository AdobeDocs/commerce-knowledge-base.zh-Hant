---
title: 'MDVA-37916：進階PayPal付款未返回確認頁面'
description: Adobe Commerce的MDVA-37916品質修補程式修正PayPal Payments Advanced付款後未返回確認頁面的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25後，即可使用此修補程式。 修補程式ID為MDVA-37916。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916：進階PayPal付款未返回確認頁面

Adobe Commerce的MDVA-37916品質修補程式修正PayPal Payments Advanced付款後未返回確認頁面的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25時，即可使用此修補程式。 修補程式ID為MDVA-37916。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
雲端基礎結構上的Adobe Commerce 2.3.6-p1

**與Adobe Commerce版本相容：**
雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.6-2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用「PayPal付款進階」方式付款後，客戶不會進入「付款確認」頁面。

<u>要再現的步驟</u>： [熒幕廣播](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. 將產品新增至購物車，並導覽至結帳頁面的付款步驟。
1. 選取&#x200B;**信用卡（Payflow進階）**&#x200B;付款選項。
1. 按一下[繼續]****&#x200B;以使用付款表單開啟iframe。
1. 使用沙箱信用卡詳細資料填寫付款表單。
   * 卡號：4444 3333 2222 1111或4111 111 111 1111
   * 到期日： 12/23
   * CSC： 123
1. 按一下&#x200B;**立即付款**。

<u>預期結果</u>：

處理付款且付款成功之後，您會被重新導向至「訂單確認」頁面。

<u>實際結果</u>：

* 系統不會將您重新導向至「訂購確認」頁面。
* 但訂單已在Adobe Commerce中建立。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 雲端基礎結構上的Adobe Commerce： [升級和修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相關閱讀

若要進一步瞭解支援知識庫中的品質修補工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

如需QPT工具中其他修補程式的詳細資訊，請參閱我們的支援知識庫中的[QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的「修補程式」區段。
