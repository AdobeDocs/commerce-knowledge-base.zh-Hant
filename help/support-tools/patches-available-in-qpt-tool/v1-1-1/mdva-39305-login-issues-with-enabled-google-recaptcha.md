---
title: 'MDVA-39305：啟用Google reCAPTCHA時的登入問題'
description: MDVA-39305修補程式修正了註冊客戶無法以已啟用的Google reCAPTCHA登入的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1後，即可使用此修補程式。 修補程式ID為MDVA-39305。 請注意，此問題已排程在Adobe Commerce 2.4.4和2.4.7版中修正。
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305：已啟用Google reCAPTCHA的登入問題

MDVA-39305修補程式修正了註冊客戶無法以已啟用的Google reCAPTCHA登入的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1時，即可使用此修補程式。 修補程式ID為MDVA-39305。 請注意，此問題已排程在Adobe Commerce 2.4.4和2.4.7版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.2-p1、2.4.3-p3、2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1-p1 - 2.4.3-p3、2.4.4-p1 - 2.4.4-p5、2.4.5 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

註冊客戶無法使用已啟用的Google reCAPTCHA登入。

<u>要再現的步驟</u>：

1. 移至&#x200B;**存放區** > **組態** > **安全性** > **Google reCAPTCHA存放區**&#x200B;並啟用&#x200B;**Google reCAPTCHA**。
1. 移至&#x200B;**前端**。
1. 在瀏覽器中開啟&#x200B;**開發人員工具主控台**。

<u>預期結果</u>：

主控台中沒有CSP警告。

<u>實際結果</u>：

主控台中的CSP警告。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
