---
title: 新網域正在重新導向至預設網域
description: 本文修正了新網域重新導向至現有或不同環境中的預設網域的問題。
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# 新網域正在重新導向至預設網域

本文修正了新網域重新導向至現有或不同環境中的預設網域的問題。

## 受影響的產品和版本

* Cloud Pro基礎架構上的Adobe Commerce （所有版本）

## 問題

新網域正在重新導向到目前環境中的預設網域或其他環境的預設網域。

## 原因

新增網域後未更新變數，或環境中設定了錯誤的[!DNL Fastly]服務時，就會發生這種情況。

## 解決方案

1. 如果網域在相同環境中重新導向，請確定您已設定[變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables)。
1. 如果網域正在重新導向到另一個環境，請執行以下命令，檢查您是否已設定正確的[!DNL Fastly]服務： `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>您可以登入每個環境（測試/生產）並檢查`/mnt/shared/fastly_tokens.txt`檔案，以找到[!DNL Fastly] API認證。 如需詳細資訊，請參閱Commerce on Cloud Infrastructure指南中的[設定 [!DNL Fastly] 服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)。

如果上述兩個設定都正確，請提交支援票證。

## 相關閱讀

* [在我們支援知識庫中設定新網域](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html)的檢查清單。
