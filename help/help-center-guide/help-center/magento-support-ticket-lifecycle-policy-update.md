---
title: Adobe Commerce支援票證生命週期原則更新
description: 本文提供Adobe Commerce支援票證生命週期原則更新的相關資訊。
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Adobe Commerce支援票證生命週期原則更新

本文提供Adobe Commerce支援票證生命週期原則更新的相關資訊。

下表說明更新的案例。 各情境的詳細資訊請參閱下節。

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>票證狀態</strong></td>
 <td class="wysiwyg-text-align-center"><strong>「解決」的天數</strong></td>
 <td class="wysiwyg-text-align-center"><strong>「關閉」的天數</strong></td>
 <td class="wysiwyg-text-align-center"><strong>通知時間</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>工程師提供解決方案</strong></td>
 <td class="wysiwyg-text-align-center">「等待您的回覆」</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">第3天和第6天</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>正在等待客戶的資訊</strong></td>
 <td class="wysiwyg-text-align-center">「等待您的回覆」</td>
 <td class="wysiwyg-text-align-center">不適用</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">第1、3和6天</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>客戶設為「已解決」或要求工程師設為「已解決」</strong></td>
 <td class="wysiwyg-text-align-center">「已解決」</td>
 <td class="wysiwyg-text-align-center">立即</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">第1天</td>
 </tr>
 </tbody>
 </table>

## 詳細情境

### 當工程師提供解決方案時

1. 將解決方案提供給客戶後，工程師會將票證狀態設為「等待您的回覆」。
1. 如果在狀態變更為「等待您的回覆」後3天沒有客戶回應，票證會移至「已解決」並通知客戶。
1. 如果在狀態變更為「等待您的回覆」後6天內客戶沒有回應，票證即會關閉並通知客戶。

### 當需要客戶的額外資訊時

1. 如果需要客戶的更新，工程師會將票證設為「等待您的回覆」。
1. 在第1天和第3天將通知傳送給客戶，請求客戶跟進。
1. 如果在狀態變更為「等待您的回覆」後6天內客戶沒有回應，票證即會關閉並通知客戶。

### 由客戶設定為「已解決」的票證

當客戶將票證設定為「已解決」時，將會在一天內關閉並通知客戶。

### 客戶指引支援以關閉票證

當客戶指示Adobe Commerce支援關閉票證時，票證會在一天內關閉並通知客戶。

## 相關閱讀

* [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Adobe Commerce說明中心起始頁面上未顯示「提交票證」連結](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [票證提交表單：商家未顯示在組織下拉式清單中](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
