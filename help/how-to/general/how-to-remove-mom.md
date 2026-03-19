---
title: 如何移除Magento Order Management (MOM)
description: 本文說明如何移除Magento Order Management (MOM)系統。
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# 如何移除Magento Order Management (MOM)

1. 依照[停用或啟用整合](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration)中的步驟來停用MOM整合。
1. 依照[解除安裝模組](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html?lang=zh-Hant)中的步驟停用MOM模組。
1. 為了擷取完整訂單資料，我們提供API。 您可以檢閱我們的Adobe | Magento OMS檔案中的[訂單存放庫](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository)以瞭解更多資訊，其中涵蓋訂單資訊(order_repository)。 使用我們的Adobe | Magento OMS檔案中的[規格區段](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services)，以使用其他API來擷取不同的資訊型別。
