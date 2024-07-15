---
title: Adobe Commerce的Magento Order Management系統(OMS)逾時
description: 針對Adobe Commerce的Magento Order Management系統(OMS)無法透過ngrok向MOM註冊本機安裝的微服務，因為MOM嘗試回撥時發生逾時的問題，本文提供解決方案。
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Adobe Commerce的Magento Order Management系統(OMS)逾時

針對Adobe Commerce的Magento Order Management系統(OMS)無法透過ngrok向MOM註冊本機安裝的微服務，因為MOM嘗試回撥時發生逾時的問題，本文提供解決方案。

## 受影響的產品和版本

* Adobe Commerce 2.3.1
* OMS
* Ngrok

>[!WARNING]
>
>免責宣告： Adobe Commerce不建議或認可任何建立通道的特定工具。 前述只是建議。 如需詳細資訊，請參閱[ngrok檔案](https://ngrok.com/docs)。

## 問題

<u>要再現的步驟</u>

1. 在本機環境中安裝Adobe Commerce。
1. 設定ngrock以建立通道來公開您的本機伺服器。
1. 嘗試[連線到OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/)。

<u>預期結果</u>

已成功建立連線。

<u>實際結果</u>

MCOM嘗試回撥至群組URL時似乎逾時。

## 原因

逾時的可能原因之一，是伺服器的地理位置太遠，且連線花費太多時間。

## 解決方案

新增引數，在啟動ngrock時指定區域。 如下所示：

```bash
./ngrok http 80 -region eu
```

預設區域為US。 檢視[所有可能的值](https://ngrok.com/docs#config_region)。
