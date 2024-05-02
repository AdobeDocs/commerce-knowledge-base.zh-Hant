---
title: 存取Adobe Commerce上的全網站分析工具時出現403錯誤
description: 當您嘗試在Adobe Commerce上存取全網站分析工具時收到403錯誤時，本文提供解決方案。
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 存取Adobe Commerce上的全網站分析工具時出現403錯誤

當您嘗試在Adobe Commerce上存取全網站分析工具時收到403錯誤時，本文提供解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.4.1和更新版本。

## 問題

嘗試存取全網站分析工具時出現403錯誤。

<u>要再現的步驟：</u>

登入Commerce管理面板，然後按一下 **報表** > *系統分析* > **全網站分析工具**.

<u>預期結果：</u>

您會看到全網站分析工具。

<u>實際結果：</u>

您會看到： *錯誤403。*


## 解決方案

若要確定全網站分析工具具有應用程式的適當存取權，請在CLI中執行以下命令。 取代 `<store URL>` 搭配您的商店URL：

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

根據您收到的回應代碼採取步驟。

### 403禁止的回應代碼

如果回應代碼為403，您可能會有Cloudflare機器人保護，這會封鎖全網站分析工具。 若要存取該工具，請將其IP加入白名單：

* 107.23.33.174
* 3.225.9.244
* 3.88.83.85

### 更正200回應代碼和JSON輸出

如果回應是正確的200程式碼和JSON輸出， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 升級全網站分析工具存取權的問題。


### 500 （嚴重錯誤）回應代碼

如果回應代碼為500 （嚴重錯誤），請安裝MDVA-38526修補程式。 根據您想要的修正程式型別，使用下列其中一個連結來下載修正程式：

* 雲端基礎結構上的Adobe Commerce修補程式： [MDVA-38526_EE_2.4.1-p1_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* 雲端基礎結構上的Adobe Commerce撰寫器修補程式： [MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

此修補程式適用於雲端基礎結構版本2.4.1及更新版本的Adobe Commerce。

### 回應不是JSON

如果回應輸出不是JSON，原因可能是PWA/Headless實施。 如果您使用Headless實作，請更新UPPER設定以略過Adobe Commerce Origin請求。 若要這麼做，請在「Adobe Commerce管理員」中的 **商店** > **設定** > **一般** > **Web** > **向上PWA設定** > **前方名稱允許清單**，新增 *swat*.

![Upper_configuration](assets/upward_pwa.png)

如果您還是無法存取全網站分析工具，請在下次登入Commerce管理面板時導覽至 **報表** > *系統分析* > **全網站分析工具**， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## 相關閱讀

* [全網站分析工具指南](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html)
