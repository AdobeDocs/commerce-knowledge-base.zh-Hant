---
title: 在雲端基礎結構上重設Adobe Commerce的環境
description: 本文說明在雲端基礎結構上Adobe Commerce上復原環境的不同案例。
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 4439ee25e929a1bdb2216cc10fa0d4506c4f3aed
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 0%

---

# 在雲端基礎結構上重設Adobe Commerce的環境

本文說明在雲端基礎結構上Adobe Commerce上復原環境的不同案例。

選擇最適合您的案例：

* 如果您有計畫的活動（計畫的部署或升級） - [案例1：計畫的活動)](#scen1)。
* 如果您有有效的快照 — [案例2：還原快照](#scen2)。
* 如果您有穩定的組建，但沒有有效的快照 — [案例3：沒有快照，組建穩定（可使用SSH連線）](#scen3)。
* 如果組建已中斷，而且您沒有有效的快照 — [案例4：沒有快照；組建已中斷（沒有SSH連線）](#scen4)。

## 案例1：計畫活動

在計畫的部署或升級中，最簡單且建議使用的[!UICONTROL Rollback]是讓商家在準備時執行下列作業：

>[!NOTE]
>
>一律先在您的&#x200B;**[!UICONTROL Staging Environment]**&#x200B;中測試這些步驟！

<u>升級/部署活動前5天</u>：

1. 檢查目前資料庫的大小。
1. 檢查您在`/data/exports`上的磁碟空間是否足以容納[!UICONTROL Database Dump]。 如果您沒有足夠的磁碟空間，請移除不需要的資料，或建立支援案例並要求擴充磁碟。

<u>變更當天</u>：

1. 將網站放入[!UICONTROL Maintenance Mode]。<br>
深入瞭解使用手冊中的[啟用或停用[!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html)，以及升級手冊中用於升級的[[!UICONTROL Maintenance Mode]選項](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html)。
1. 取得本機[[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html)。

<u>若需要[!UICONTROL Rollback]</u>：

1. 如果應用程式（例如[!DNL MariaDB]）已升級為此計畫活動的一部分，請先將該應用程式重新安裝至先前的版本。
1. [!UICONTROL Rollback]使用本機[!UICONTROL Database Dump]的資料庫，並將它匯回[!DNL MariaDB]。
1. 透過[!DNL Git]將程式碼[!UICONTROL Rollback]至先前的工作版本。

對於升級/規劃的活動[!UICONTROL rollbacks/restores]，不建議使用[!UICONTROL Snapshots]，因為擷取資料所需的時間比本機[!UICONTROL Database Dump]長，如上方&#x200B;**步驟2所述，若需要[!UICONTROL Rollback]**&#x200B;區段。

[!UICONTROL Snapshots]不是儲存在節點/伺服器上，而是儲存在不同的儲存區塊上，而且由於資料必須透過網路從區塊儲存傳輸至新磁碟，所以這個過程需要時間。 然後，會將新磁碟掛載到節點，準備擷取/匯入到連線到節點/伺服器的原始磁碟。

當您將此專案與匯入本機[!UICONTROL Database Dump]進行比較時，資料在節點/伺服器上已經可以擷取，因此會儲存大量時間，因為只需要一個[!UICONTROL Database Import]。

## 案例2：還原快照

閱讀：在開發人員檔案中[在雲端基礎結構上還原Adobe Commerce上的快照](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot)。

>[!NOTE]
>
>在雲端基礎結構帳戶上存取Adobe Commerce之後以及套用重大變更之前，建立快照必須是我們的第一步。 此為最佳實務，強烈建議使用。

閱讀：在開發人員檔案中建立[快照](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot)。

## 案例3：沒有快照、建置穩定（可用SSH連線）

本節說明當您尚未建立快照，但可透過SSH存取環境時，如何重設環境。

步驟如下：

1. 停用組態管理。
1. 解除安裝Adobe Commerce軟體。
1. 重設[!DNL git]分支。

執行這些步驟後：

* 您的Adobe Commerce安裝會回到其Vanilla狀態（資料庫已還原；部署組態已移除；`var`下的目錄已清除）。
* 您的[!DNL git]分支已重設為過去所需的狀態。

請閱讀以下詳細步驟。

### 步驟0 （先決條件）：移除config.php以停用「組態管理」

我們需要停用「組態管理」，以免在部署期間自動套用先前的組態設定。

若要停用「組態管理」，請確定您的`/app/etc/`目錄不包含`config.php`檔案。

若要移除組態檔，請遵循下列步驟：

1. [SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)。
1. 移除組態檔： `rm app/etc/config.php`

深入瞭解組態管理：

* [減少雲端基礎結構上Adobe Commerce的部署停機時間](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) （在我們的支援知識庫中）。
* 在開發人員檔案中[商店設定的組態管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)。

### 步驟1：使用setup：uninstall命令解除安裝Adobe Commerce軟體


解除安裝Adobe Commerce軟體會捨棄並還原資料庫、移除部署設定，以及清除`var`下的目錄。

閱讀：在開發人員檔案中[解除安裝Adobe Commerce軟體](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html)。

若要解除安裝Adobe Commerce軟體，請遵循下列步驟：

1. [SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)。
1. 執行`setup:uninstall` ： `bin/magento setup:uninstall`
1. 確認解除安裝。

系統會顯示下列訊息，確認解除安裝成功：

```php
[SUCCESS]: Magento uninstallation complete.
```

這表示我們已將Adobe Commerce安裝（包括DB）還原為其正版(Vanilla)狀態。

### 步驟2：重設[!DNL git]分支

透過[!DNL git]重設，我們將程式碼還原成過去所需的狀態。

1. 將環境複製到本機開發環境。 您可以在Cloud Console中複製命令：    ![copy_git_clone.png](assets/copy_git_clone.png)
1. 存取認可歷史記錄。 使用`--reverse`以相反順序顯示歷程記錄，以方便使用： `git log --reverse`
1. 選取您擅長的認可雜湊。 若要將程式碼重設為真實狀態(Vanilla)，請尋找建立分支（環境）的第一個認可。
   ![在Git主控台中選取認可雜湊](assets/select_commit_hash.png)
1. 套用硬式[!DNL git]重設： `git reset --h <commit_hash>`
1. 將變更推送至伺服器： `git push --force <origin> <branch>`

執行這些步驟後，系統會重設我們的[!DNL git]分支，並清除整個[!DNL git]變更記錄檔。 最後[!DNL git]個推送會觸發重新部署，以套用所有變更並重新安裝Adobe Commerce。

## 案例4：沒有快照；組建損毀（沒有[!DNL SSH]連線）

本節說明如何在環境處於嚴重狀態時重設環境：建置程式無法成功建置工作應用程式，因此導致[!DNL SSH]連線無法使用。

在此案例中，您必須先使用[!DNL git]重設還原Adobe Commerce應用程式的工作狀態，然後解除安裝Adobe Commerce軟體（若要卸除並還原資料庫、移除部署設定等）。 此情境涉及與情境3相同的步驟，但步驟順序不同，並且有另一個步驟 — 強制重新部署。 步驟如下：

1. [重設 [!DNL git] 分支。](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [停用組態管理。](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [解除安裝Adobe Commerce軟體。](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. 強制重新部署。

執行這些步驟後，您將會獲得與案例3相同的結果。

### 步驟4：強制重新部署

提交認可（這可能是空的認可，雖然我們不建議這麼做）並將其推送到伺服器以觸發重新部署：

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## 如果安裝：解除安裝失敗，請手動重設資料庫

如果執行`setup:uninstall`命令失敗並出現錯誤，而且無法完成，我們可以使用以下步驟手動清除DB：

1. [SSH至您的環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)。
1. 連線到MySQL DB： `mysql -h database.internal` （對於Pro環境，請參閱： [設定MySQL服務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)）。
1. 卸除`main`資料庫： `drop database main;`
1. 建立空的`main`資料庫： `create database main;`
1. 刪除下列組態檔： `config.php`、`config.php.bak`、`env.php`、`env.php.bak`

重設DB後，[進行 [!DNL git] 推送到環境以觸發重新部署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html)，並將Adobe Commerce安裝到新建立的DB。 或[執行重新部署命令](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands)。
