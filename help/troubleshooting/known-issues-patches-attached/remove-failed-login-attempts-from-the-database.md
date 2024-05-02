---
title: 從資料庫移除失敗的登入嘗試
description: 本文說明如何從Adobe Commerce內部部署和Adobe Commerce的雲端基礎結構資料庫移除預先存在的失敗登入認證。 若是2.2.10+和2.3.3+版本，您只需要執行附加的指令碼。 若是舊版2.3.0-2.3.2-p2，您必須套用修補程式以停止記錄，並執行附加的指令碼以移除先前存在的失敗登入認證。
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# 從資料庫移除失敗的登入嘗試

>[!NOTE]
>
>本文已在2020年4月13日更新，採用名為DB\_CLEANUP\_SCRIPT\_v2的新指令碼。 請使用附加的DB\_CLEANUP\_SCRIPT\_v2指令碼，清除其他表格中預先存在的失敗登入資料。 即使您先前已執行DB\_CLEANUP\_SCRIPT\_v2來協助確保已清除其他表格，您仍需使用DB\_CLEANUP\_SCRIPT\_v1。

本文說明如何從Adobe Commerce內部部署和Adobe Commerce的雲端基礎結構資料庫移除預先存在的失敗登入認證。 若是2.2.10+和2.3.3+版本，您只需要執行附加的指令碼。 若是舊版2.3.0-2.3.2-p2，您必須套用修補程式以停止記錄，並執行附加的指令碼以移除先前存在的失敗登入認證。

## **受影響的產品和版本**

* 此問題會影響雲端基礎結構2.2.x、2.3.x及舊版上的Magento Open Source、Adobe Commerce內部部署和Adobe Commerce。
* Adobe Commerce 1.x部署不受影響。

## 問題

2019年向Adobe Commerce回報了錯誤，允許將失敗的登入嘗試登入Adobe Commerce 2.3.x和2.2.x中的資料庫。為回應此問題，Adobe Commerce在Adobe Commerce 2.3.3和2.2.10 （2019年10月發行）中納入了修正。 雖然該錯誤的修正已停止記錄失敗的登入嘗試，但在更新到這些目前版本之前收集的資訊可能仍然存在。 此最新修正會清除先前記錄的登入嘗試資訊（如果有的話）。   CVE-2019-8118的說明和追蹤，請參閱 [常見弱點與暴露](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## 解決方案

您需要使用附加的指令碼和修補程式，還是只需要指令碼，端視您的Adobe Commerce版本而定：

**Adobe Commerce和Magento Open Source版本2.3.0-2.3.2-p2**

對於這些版本，您必須套用修補程式並執行附加的資料庫清理指令碼，以結束持續記錄並消除記錄。

1. 執行Composer修補程式以停止記錄。 此修補程式已附加至文章。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結 [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). 如需如何套用修補程式的說明，請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中。

1. 現在執行指令碼以清除先前存在的失敗登入嘗試的資料庫。 此指令碼已附加至文章。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結 [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

請參閱 [**如何執行指令碼**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) 區段以取得指示。

**Adobe Commerce和Magento Open Source 2.3.3及更高版本/2.2.10及更高版本**<br>
僅針對這些版本，執行以下指令碼以清除舊記錄（先前透過2019年10月發佈的修正已結束這些版本的記錄）。 此指令碼已附加至文章。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結 [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

請參閱 [**如何執行指令碼**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) 一節，以取得指示。

**如何執行指令碼**

請依照下列指示執行指令碼：

1. Put `DB_CLEANUP_SCRIPT_v2.php` 在Adobe Commerce或Magento Open Source安裝的根目錄中（與包含下列專案的應用程式相同的目錄中） `app/bootstrap.php`)。
1. 在終端機中執行此命令： `php DB_CLEANUP_SCRIPT_v2.php` 而且會開始資料庫清理程式。

如果您在執行指令碼時遇到任何問題，請 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 或寄電子郵件給我們： [security@magento.com](mailto:security@magento.com).

**附加的檔案**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
