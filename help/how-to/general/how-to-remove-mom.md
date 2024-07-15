---
title: 如何移除Magento Order Management(MOM)
description: 本文說明如何移除Magento Order Management(MOM)系統。
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# 如何移除Magento Order Management(MOM)

1. 依照[停用或啟用整合](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration)中的步驟來停用MOM整合。
1. 依照[解除安裝模組](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html)中的步驟停用MOM模組。
1. 為了擷取完整訂單資料，我們提供API。 您可以檢閱我們Adobe中的[訂單存放庫](https://omsdocs.magento.com/specifications/#magento.sales.order_repository)，以瞭解更多資訊 | Magento包含訂單資訊(order_repository)的OMS檔案。 在我們的Adobe中使用[規格區段](https://omsdocs.magento.com/specifications/#services) | MagentoOMS檔案，以使用其他API來擷取不同的資訊型別。
