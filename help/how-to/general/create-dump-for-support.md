---
title: 如何在支援代理程式要求時建立「已清除」傾印
description: 本文提供當Adobe Commerce支援代理程式要求您提供資料庫時，如何從Adobe Commerce管理員建立「已清除」傾印（備份）和程式碼的相關資訊。 此傾印會排除您的媒體檔案，以加速處理過程，並產生更小的檔案。 進行資料庫備份時，所有敏感資料都會經過雜湊處理。
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: e07ade849a4105b5e499b5282d75cb1b5321b6ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 如何在支援代理程式要求時建立「已清除」傾印


## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.3.x、2.4.x。

## 建立「已清除」的傾印

從管理員建立「已清除」傾印：

1. 在Commerce Admin中，前往 **系統** > **支援** > **資料收集器**.
1. 按一下 **新增備份**.
1. 幾分鐘後，按一下 **重新整理狀態** （可能需要更長的時間，每5分鐘重複一次，直到完成）。
1. 重新定位產生的傾印檔案(從 `/var/support` 到Adobe Commerce根目錄的目錄。

然後，您可以提供到傾印檔案（您的存放區地址和顯示的檔案名稱）的直接下載連結給支援。

如果您無法從管理員建立傾印，請考慮使用CLI命令，如所述 [執行支援公用程式](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-spt-util.html) （位於我們的開發人員檔案中）。

## 相關閱讀

* [在雲端基礎結構上為Adobe Commerce建立完整資料庫備份](/help/how-to/general/create-database-dump-on-cloud.md) 在我們的支援知識庫中。
