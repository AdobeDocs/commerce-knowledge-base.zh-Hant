---
title: Adobe Commerce 2.4.1和2.3.6建立帳戶按鈕停用Hotfix
description: 當您在表單上的任何欄位中輸入不正確的值後，難以建立新帳戶時，本文提供此問題的Hotfix。 例如，當您以錯誤的格式輸入電子郵件地址、將名字或姓氏欄位留空或未輸入符合密碼要求的值時。 第1季版本（2.4.2、2.4.1-p1和2.3.6-p1）將包含永久修正。
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1和2.3.6建立帳戶按鈕停用Hotfix

當您在表單上的任何欄位中輸入不正確的值後，難以建立新帳戶時，本文提供此問題的Hotfix。 例如，當您以錯誤的格式輸入電子郵件地址、將名字或姓氏欄位留空或未輸入符合密碼要求的值時。 第1季版本（2.4.2、2.4.1-p1和2.3.6-p1）將包含永久修正。

## 問題

如果購物者輸入了無效的資料，則&#x200B;**建立新帳戶**&#x200B;頁面上的&#x200B;**建立帳戶**&#x200B;按鈕仍會停用。 這可防止購物者在發生錯誤後重新嘗試建立帳戶。

<u>要再現的步驟</u>：

1. 移至&#x200B;**建立新的客戶帳戶**。
1. 填寫表單欄位。 在&#x200B;**密碼**&#x200B;欄位中，輸入不符合密碼要求的值。 例如：
   * **密碼**&#x200B;與&#x200B;**確認密碼**&#x200B;欄位中的密碼不相符。
   * **密碼**&#x200B;與&#x200B;**確認密碼**&#x200B;欄位中的密碼不夠長。
1. 按一下&#x200B;**建立帳戶**&#x200B;按鈕。

<u>預期結果</u>：

* **建立帳戶**&#x200B;按鈕應該保持作用中/啟用狀態。
* 使用者應該能夠建立新帳戶。

<u>實際結果</u>：

* **建立帳戶**&#x200B;按鈕保持停用，即使使用有效/正確的資料填寫所有必要欄位後也是如此。
* 客戶無法建立新帳戶。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下下列連結： [下載MC-38509-composer.patch](assets/MC-38509-composer.patch.zip)

## 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.3.6和2.4.1。
* Adobe Commerce內部部署2.3.6和2.4.1。

此修補程式與任何其他Adobe Commerce版本不相容。

## 如何套用修正程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 相關閱讀

* [GitHub Adobe Commerce >提交無效的建立帳戶表單會使提交按鈕停用](https://github.com/magento/magento2/issues/30513)
* [Adobe Commerce使用手冊>快速入門>建立帳戶](https://docs.magento.com/user-guide/magento/magento-account-create.html)
