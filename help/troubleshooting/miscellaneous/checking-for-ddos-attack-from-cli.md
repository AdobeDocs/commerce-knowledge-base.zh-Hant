---
title: 正在檢查來自CLI的DDoS攻擊
description: 本文會討論如何嘗試從伺服器的命令列介面(CLI)檢查分散式拒絕服務(DDoS)攻擊的問題。
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# 正在檢查來自CLI的DDoS攻擊

本文會討論如何嘗試從伺服器的命令列介面(CLI)檢查分散式拒絕服務(DDoS)攻擊的問題。

## 受影響的產品和版本

* Adobe Commerce，所有版本
* Magento Open Source，所有版本

## 問題

您的網站速度很慢，而且除了CLI之外，您無權存取任何其他分析應用程式工具來檢查是否存在DDoS攻擊。 DDoS攻擊的症狀會因您的網路組態、使用的軟體等而有很大的差異。

不過，建議您使用專門設計來協助識別DDoS攻擊的分析軟體產品。

## 原因

網站速度緩慢的可能原因有很多，包括伺服器效能緩慢、CPU使用率高，或指令碼、程式碼或廉價硬體中的設定錯誤。 有時可能是由於DDoS攻擊所造成。 您必須檢查DDoS攻擊的兩個基本工具是Adobe Commerce記錄檔和CLI。

同樣需要注意的是，使用專門設計來識別DDoS攻擊的軟體對於您的調查非常有用。

## 解決方案步驟

1. 檢查Adobe Commerce記錄檔以檢視是否發生DDoS攻擊以外的其他情況。 如需詳細資訊，請參閱開發人員檔案中的下列文章：
   * [Adobe Commerce和Magento Open Source記錄檔位置](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * 雲端基礎結構記錄位置上的[Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. 開始使用CLI來使用`netstat`命令檢查您目前所有的網際網路連線： `netstat -na`。 這會顯示所有使用中建立的伺服器連線。 在這裡，您可能會注意到來自相同IP位址的連線過多。
1. 若要將已建立的連線結果進一步縮小為僅連線至連線埠80 （您網站的http連線埠）的連線，以便從一個IP位址或一組IP位址排序並識別太多連線，請使用以下命令： `netstat -an | grep :80 | sort`。 您可以對連線埠443上的https重複相同的命令： `netstat -an | grep :443 | sort`。 另一個選項是將原始指令同時延伸至連線埠80和443： `netstat -an | egrep ":80|:443" | sort`。
1. 若要檢視伺服器上是否有許多作用中的`SYNC_REC`，請使用命令：     `netstat -n -p|grep SYN_REC | wc -l`     這個值通常小於5，但若是DDoS攻擊，可能會高很多，不過對於某些伺服器，數字可能會高一些，這是正常情況。
1. 若要列出所有傳送`SYNC_REC`狀態的IP位址，請使用命令： `netstat -n -p | grep SYN_REC | sort -u`。
1. 若要進一步列出所有傳送`SYNC_REC`狀態的唯一IP位址，請使用命令： `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`。
1. 您也可以使用`netstat`命令來計數及計算每個IP位址與伺服器之間的連線數目： `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`。
1. 若要列出連線到伺服器的UDP或TCP通訊協定連線計數，請使用命令： `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`。
1. 若要檢查已建立的連線，而不僅僅是所有連線，並顯示每個IP位址的連線計數，請使用命令： `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`。
1. 若要顯示依連線埠80之IP位址列出的連線計數，請使用命令： `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`。

請務必找人為您找到的資料進行適當的分析，以判斷您是否確實遭受DDoS攻擊。 在上述步驟中使用伺服器CLI的`netstat`命令，可協助您分析是否遭受DDoS攻擊，但使用特別設計來協助識別DDoS攻擊的軟體分析產品，以及適當的分析，是您識別DDoS威脅的最佳工具。

如果您發現受到DDoS攻擊，您可以採取的步驟取決於您的網路設定以及DDoS攻擊是如何發生的，但一般建議是連絡您的ISP、為您的伺服器取得新的IP位址，和/或洽詢熟練處理DDoS問題的IT專業人員，以分析您的特定情況並提供建議。

## 開發人員檔案中的相關閱讀：

* [DDoS保護](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [使用CLI命令](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* 適用於Commerce的[雲端CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
