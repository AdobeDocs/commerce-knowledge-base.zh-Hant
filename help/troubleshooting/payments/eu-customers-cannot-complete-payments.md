---
title: 歐盟客戶無法完成付款
description: 本文針對歐盟客戶無法完成付款的問題提供修正。
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# 歐盟客戶無法完成付款

本文針對歐盟客戶無法完成付款的問題提供修正。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有版本
* Adobe Commerce內部部署2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x

## 問題

來自歐盟的客戶抱怨他們的信用卡交易遭到拒絕。

## 原因

歐盟修訂了名為「付款服務指示(PSD)」的規範，更新版本為[PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN)。 這是歐盟(EU)的指令，旨在規範整個歐盟和歐洲經濟區(EEA)的支付服務與支付服務提供者。 PSD2需要強大的客戶驗證(SCA)，以提高付款資料安全性和驗證。 如果您的支付解決方案不符合指示要求，可能導致客戶無法完成支付。 如需詳細資訊，請參閱[相關的Adobe Commerce DevBlog文章](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460)。

## 解決方案

遵循DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations)的[Adobe Commerce付款提供者Recommendations區段中的建議。
