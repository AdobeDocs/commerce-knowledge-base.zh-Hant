---
title: 針對雲端基礎結構上的Adobe Commerce提出假期突增容量要求
description: 在旺季假日的銷售季節（大約是11月中旬至1月中旬），Adobe建議所有託管於雲端基礎結構的Adobe Commerce商戶為增加的流量做好準備。
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: dfd3f788f42677b631ffb5b3153a1c79c2cc1ca3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 針對雲端基礎結構上的Adobe Commerce提出假期突增容量要求

在旺季假日的銷售季節（大約是11月中旬至1月中旬），Adobe建議所有託管於雲端基礎結構的Adobe Commerce商戶為增加的流量做好準備。

**計畫和預估流量**

我們建議雲端基礎結構上的所有Adobe Commerce商家 [利用這組建議來估計旺季流量](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) 每年假期銷售旺季時節。

完成建議的預估後，如果您的團隊已找出任何您認為需要額外容量的日期，請繼續下一個步驟，以取得有關如何請求激增容量的資訊。

**檢視您的升級記錄**

您可以在中檢視要求調整大小的歷程記錄 [專案入口網站（入門UI）](https://devdocs.magento.com/cloud/onboarding/onboarding-tasks.html)，下 **專案** > **服務** > **CPU使用量追蹤**.
下列資訊適用於每個調整大小請求：

* **調整開始日期的大小**：更新請求的日期。
* **大小結束日期**：叢集恢復為先前大小的日期。
* **vCPU大小**：放大後的叢集大小。
* **使用天數**：叢集保持向上擴充了多少天。
* **期間vCPU**：以使用的天數變更vCPU大小。 （例如，vCPU大小192 x 25天等於4,800）。

**請求突增容量**

雲端基礎結構上的Adobe Commerce商戶預期在節日季節需要額外的容量，應： [提交突增容量支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) 透過我們的 [說明中心](/help/overview.md)，指出票證內的日期和預期容量需求。 請注意，容量增加需要使用您的授權超額容量。

**我們建議在需要容量時，至少提前48個營業時間提交這些票證；此外，鑑於此期間的容量有限，我們建議儘量提前提交黑色星期五/網路星期一期間的要求。**


**更多說明？**

需要更多有關高峰期流量準備的指引嗎？ 雲端基礎結構上的Adobe Commerce商家可以聯絡他們的Adobe客戶團隊，以取得為成功的旺季做準備的協助、策略和規劃秘訣。 我們也建議您檢視 [Magento部落格](https://magento.com/blog) 全年策略秘訣。

## 複查產能的資源

在我們的支援知識庫中：

* [雲端上Adobe Commerce的CPU配置計算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [檢查雲端上的Adobe Commerce是否需要主機執行個體的大小調整](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [檢查雲端上Adobe Commerce的主機的CPU設定](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [識別並測量雲端上Adobe Commerce的中斷情形](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
