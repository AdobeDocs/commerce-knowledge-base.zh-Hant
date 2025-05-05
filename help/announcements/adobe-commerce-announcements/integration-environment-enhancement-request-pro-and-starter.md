---
title: 整合環境增強功能要求 — Pro與Starter
description: 如果您是雲端基礎結構Adobe Commerce Pro計畫架構客戶，目前使用標準規模的整合環境，或您是雲端基礎結構Adobe Commerce入門計畫架構客戶，目前使用標準規模的中繼環境，而且想要更多電力，您可以請求升級至增強型整合環境，此環境可提供約四倍的效能。 本文將Pro客戶的指示與Starter客戶的指示分開。
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 整合環境增強功能要求 — Pro與Starter

如果您是雲端基礎結構Adobe Commerce Pro計畫架構客戶，目前使用標準規模的整合環境，或您是雲端基礎結構Adobe Commerce入門計畫架構客戶，目前使用標準規模的中繼環境，而且想要更多電力，您可以請求升級至增強型整合環境，此環境可提供約四倍的效能。 本文將Pro客戶的指示與Starter客戶的指示分開。

>[!NOTE]
>
> 升級至增強式整合可能無法解決所有效能問題，因為它將取決於安裝的全部資源需求，包括協力廠商整合或自訂。
>
> 您也必須確保在整合環境中遵循最佳實務以獲得最佳效能，即使這並非最終解決方案。 請參閱下列檔案以取得指引： 《Commerce on Cloud Infrastructure指南》中的[Pro架構](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)和[入門架構](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)。

## Pro

1. 如果您使用Pro，若要升級，您必須將整合分支的數目減少至兩個（**主要整合分支包含在總計**&#x200B;中）。 **注意：請勿在此總計中計算主要分支。 主要分支不會被視為整合分支。**&#x200B;請依照開發人員檔案中[使用Cloud Console管理分支](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=zh-Hant)中的步驟操作。
1. 商家需要[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以連絡原因「*要求雲端設定變更*」要求升級至增強整合環境。
1. Adobe客戶工程團隊會確認整合環境的數量，並開始變更。
1. 升級完成時，商家將在票證中收到通知。
1. 商家重新部署整合環境。 請依照開發人員檔案中[合併分支](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch)中的步驟操作。 *注意*：在您執行時，部署會自動發生： <pre>git push origin &lt;branch-name></pre>

效能提升表示成功升級至增強整合環境。

**附註**：

* 標準尺寸與增強型尺寸是唯一可用的兩種尺寸。
* 指定商店的所有整合環境大小相同，大小無法獨立調整。
* 若您需要兩個以上的增強型整合環境，請洽詢您的Adobe客戶團隊。

## 入門者

1. 入門計畫不能有任何整合分支：商家必須刪除整合環境，並僅離開中繼環境。 請依照開發人員檔案中[使用雲端主控台管理分支](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=zh-Hant)中的步驟操作。 可用的環境數量將減少，最多允許一個整合環境。
1. 商家需要[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以連絡原因&#x200B;*「要求雲端組態變更」* - **您的中繼環境是具名的整合環境**，要求升級至增強整合環境。
1. Adobe客戶工程團隊會確認整合環境的數量，並開始變更。
1. 升級完成時，商家將在票證中收到通知。
1. 商家重新部署整合環境。 請依照開發人員檔案中[合併分支](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch)中的步驟操作。 *注意*：在您執行時，部署會自動發生： <pre>git push origin &lt;branch-name></pre>

效能提升表示成功升級至增強整合環境。

**附註**：

* 標準尺寸與增強型尺寸是唯一可用的兩種尺寸。
* 指定商店的所有整合環境大小相同，大小無法獨立調整。
* 如果您需要測試環境以外的整合環境，請洽詢您的Adobe客戶團隊。
* 如果在2020年9月17日之後購買，則由於擴充的整合環境，此增強功能將不再適用。
