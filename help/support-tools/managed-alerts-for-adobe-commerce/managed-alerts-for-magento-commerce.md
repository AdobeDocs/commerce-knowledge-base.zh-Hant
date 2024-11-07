---
title: Adobe Commerce的管理警報
description: 如果您是雲端基礎結構專業版的Adobe Commerce規劃架構客戶，則可以使用受管理警報來瞭解您網站的健康情況。 如果您是雲端基礎結構入門計畫架構客戶的Adobe Commerce，您只會收到Apdex和錯誤率條件的警報。
exl-id: 4d08eaad-a3ce-4f6c-9c32-58e44e1d6534
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Adobe Commerce的管理警報


我們設定了重要的儀表板和警報，協助您瞭解網站何時達到關鍵儲存和Apdex等級（使用者對應用程式和服務回應時間的滿意度）。 這可協助您在注意到回應時間緩慢或中斷之前採取行動。 您將能夠使用下列文章來疑難排解警示。 在使用警示之前，請先設定通知通道。 請參閱我們的開發人員檔案中的[New Relic設定通知通道](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service)。

>[!NOTE]
>
>如果Adobe Commerce警示原則的託管警示無法使用，可能是因為此帳戶是新建立的或New Relic最近已設定。 每個星期二都會執行一個程式，將警示原則新增至這些帳戶。 下次程式執行後的第二天，您應該可以使用警示原則。 如果原則仍然遺失，[請提交Adobe Commerce支援請求](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket)並包含您的專案ID。

請參閱下表中的知識庫文章連結，提供這些警示的疑難排解步驟：

* Adobe Commerce的管理警報：CPU警告警報
* Adobe Commerce的管理警示：CPU嚴重警示
* Adobe Commerce的管理警報：記憶體警告警報
* Adobe Commerce的管理警示：記憶體嚴重警示
* Adobe Commerce的管理警報：Apdex警告警報
* Adobe Commerce的管理警示：Apdex嚴重警示
* Adobe Commerce的管理警報：磁碟警告警報
* Adobe Commerce的管理警示：磁碟嚴重警示
* 在Adobe Commerce上管理警報：MariaDB警報
* Adobe Commerce上的受管理警報： Redis記憶體警告警報
* Adobe Commerce上的受管理警報：Redis記憶體嚴重警報

>[!NOTE]
>
>「警告警示」和「嚴重警示」的設定臨界值是根據我們正在使用客戶群的歷史效能資料進行的研究而定，並代表Adobe Commerce支援和工程團隊的最新深入分析。 請注意，這些臨界值可能會根據最新的持續分析而有所變更。 一般的警報流程是接收警報，其嚴重性會由低到高的順序排列。 因此，在收到「嚴重」警示之前，您可能會收到「警告」警示。 請參閱文章連結以了解疑難排解步驟。

<table style="width: 128.434%; height: 660px;" width="100%">
<tbody>
<tr style="height: 44px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 44px;">
<p><strong>嚴重程度</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 44px;">
<p><strong>CPU</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 44px;">
<p><strong>記憶體</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 44px;">
<p><strong>磁碟</strong></p>
</td>
<td class='"wysiwyg-text-align-center wysiwyg-text-align-center' style="width: 9%; height: 44px;">
<p><strong>Apdex</strong></p>
</td>
<td style="width: 7.058036%; height: 44px;">
<p><strong>MariaDB</strong></p>
</td>
<td class="wysiwyg-text-align-center med-col">
<p><strong>Redis記憶體</strong></p>
</td>
<td class="wysiwyg-text-align-center large-col" style="width: 24.5638%; height: 44px;">
<p><strong>疑難排解文章</strong></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md">Adobe Commerce的管理警報：CPU警告警報</a><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md"></a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">關鍵</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-cpu-critical-alert.md">Adobe Commerce的管理警示：CPU嚴重警示</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-memory-warning-alert.md">Adobe Commerce的管理警報：記憶體警告警報</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">關鍵</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">
<p> </p>
<p>✅</p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-memory-critical-alert.md#_critical_memory">Adobe Commerce的管理警示：記憶體嚴重警示</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Adobe Commerce的管理警報：Apdex警告警報</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">關鍵</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-critical-alert.md">Adobe Commerce的管理警示：Apdex嚴重警示</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md">Adobe Commerce的管理警報：磁碟警告警報</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">關鍵</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md">Adobe Commerce的管理警示：磁碟嚴重警示</a></p>
</td>
</tr>
<tr style="height: 44px;">
<td style="width: 17.8571%; height: 44px;">警告與嚴重</td>
<td style="width: 6.14286%; height: 44px;"> </td>
<td style="width: 10.5714%; height: 44px;"> </td>
<td style="width: 7.14286%; height: 44px;"> </td>
<td style="width: 9%; height: 44px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 44px;">✅</td>
<td style="width: 24.5638%; height: 44px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 44px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-mariadb-alerts.md">在Adobe Commerce上管理警報：MariaDB警報</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">警告</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-warning-alert.md">Adobe Commerce上的受管理警報： Redis記憶體警告警報</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">關鍵</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-critical-alert.md">Adobe Commerce上的受管理警報：Redis記憶體嚴重警報</a></p>
</td>
</tr>
</tbody>
</table>
