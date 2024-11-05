---
title: 為現有Cloud Starter專案設定Adobe Commerce Intelligence連線
description: 本文提供解決方案，協助您為現有的Cloud Starter專案設定Adobe Commerce Intelligence連線。
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# 為現有Cloud Starter專案設定Adobe Commerce Intelligence連線

>[!NOTE]
>
>Adobe Commerce Intelligence先前稱為Magento Business Intelligence (MBI)。

本文提供解決方案，協助您為現有的Cloud Starter專案設定Adobe Commerce Intelligence連線。

## 受影響的產品和版本

雲端入門版Adobe Commerce （所有版本）

## 問題

您想要為現有的Cloud Starter專案設定Commerce Intelligence連線。

>[!NOTE]
>
>Adobe不再支援新的Cloud Starter訂閱，但如果您有現有的Starter專案，您將需要遵循下方提供的步驟來設定連線。

## 解決方案

若要針對雲端入門專案啟用Commerce Intelligence，請建立Commerce Intelligence帳戶、建立SSH金鑰，最後連線至您的Adobe Commerce資料庫。

請依照下列步驟執行：

1. 建立您的Adobe Commerce Intelligence帳戶：

   * 移至[accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login)。
   * 導覽至&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**。
   * 按一下&#x200B;**[!UICONTROL Create Instance]**。 如果沒有看見此按鈕，請連絡您的客戶成功案例經理或客戶技術顧問。
   * 選取您的Cloud Starter訂閱。 如果您只有Cloud Starter訂閱，系統就會自動選取此選項。
   * 按一下&#x200B;**[!UICONTROL Continue]**。
   * 輸入您的資訊以建立您的帳戶。

   ![建立MBI帳戶](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * 移至您的收件匣並驗證電子郵件地址。

   ![驗證電子郵件地址](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * 建立密碼。

   ![建立密碼](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * 建立帳戶後，您可以選擇將使用者新增至新帳戶。 您現在可以新增技術管理員，以執行下列步驟。

   ![新增使用者](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. 輸入商店的相關資訊以設定您的偏好設定。

   ![新增商店資訊](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   在連線資料庫以進行入門流程中的第三步之前，您需要收集一些資訊。 您將在步驟9中填寫&#x200B;*[!UICONTROL Connect your database]*&#x200B;頁面。

1. 建立專屬的Commerce Intelligence使用者。

   * 在[account.adobe.com](https://account.adobe.com/)上建立新使用者。
   * 移至[https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/)產生您的Adobe Commerce帳戶。
   * 為什麼是新的使用者？ Adobe Commerce Intelligence需要新增至專案的使用者來持續擷取新資料，以傳輸到帳戶的Commerce Intelligence Data Warehouse。 此使用者將擔任該連線。 步驟4會將此使用者新增至專案。
   * 之所以有專屬的Commerce Intelligence使用者，是為了防止新增的使用者不慎停用或刪除並停止Commerce Intelligence連線。

1. 將新建立的使用者新增至專案的主要環境，做為&#x200B;*貢獻者*。

   ![新增使用者為貢獻者](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. 取得Commerce Intelligence SSH金鑰。

   * 移至Commerce Intelligence設定使用者介面的&#x200B;**[!UICONTROL Connect your database]**&#x200B;頁面，然後向下捲動至&#x200B;**[!UICONTROL Encryption settings]**。
   * 針對欄位&#x200B;**[!UICONTROL Encryption Type]**，請選擇&#x200B;**[!UICONTROL SSH Tunnel]**。
   * 從下拉式清單，您可以複製並貼上提供的MagentoBI Essentials公開金鑰。

   ![加密設定](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. 將新的MagentoBI Essentials公開金鑰新增到步驟5中建立的Commerce Intelligence使用者。

   * 移至[accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login)。 針對已建立的新Commerce Intelligence使用者，使用您的帳戶登入資訊登入。 然後前往&#x200B;**[!UICONTROL Account Settings]**&#x200B;標籤。
   * 向下捲動頁面，並展開SSH金鑰的下拉式清單。 然後按一下&#x200B;**[!UICONTROL Add a public key]**。

   ![新增公開金鑰](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * 從上方新增MagentoMBI Essentials SSH公開金鑰。

   ![新增SSH公開金鑰](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. 提供Business IntelligenceEssentials [!DNL MySQL]認證。

   * 更新您的`.magento/services.yaml`。

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * 更新您的`.magento.app.yaml`。

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. 取得將資料庫連線至Commerce Intelligence的資訊。

   執行`echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp`以取得連線資料庫的資訊。

   您應會收到與以下輸出類似的資訊：

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. 連線您的Adobe Commerce資料庫。

   ![連線您的Adobe Commerce資料庫](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *輸入*：

   * 整合名稱： [選擇整合的名稱。]
   * 主機： `mbi.internal`
   * 連線埠：3306
   * 使用者名稱： mbi
   * 密碼：步驟8的輸出中提供[輸入密碼。]
   * 資料庫名稱：主要
   * 資料表首碼：如果沒有資料表首碼，[請留空]

1. 設定您的[!UICONTROL Timezone Settings]。

   ![時區設定](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *輸入*

   * 資料庫：時區：UTC
   * 想要的時區： [選擇資料顯示的時區。]

1. 取得加密設定的資訊。

   * 專案UI會提供SSH存取字串。 此字串可用來收集設定&#x200B;**[!UICONTROL Encryption settings]**&#x200B;時遠端位址和使用者名稱所需的資訊。 選取&#x200B;**[!UICONTROL SSH]**&#x200B;以檢視您的使用者名稱與遠端位址。 *@*&#x200B;之前的文字字串是您的使用者名稱，*@*&#x200B;之後的文字字串是您的遠端位址。

   ![存取網站主版](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. 輸入您[!UICONTROL Encryption Settings]的資訊。

   ![加密設定](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *輸入*

   * 加密型別： SSH通道
   * 遠端位址： ssh.us-3.magento.cloud
   * 使用者名稱：vfbfui4vmfez6-master-7rqtwti—mymagento
   * 連線埠：22

1. 按一下&#x200B;**[!UICONTROL Save Integration]**。
1. 您現在已成功連線至您的Commerce Intelligence Essentials帳戶。
1. 如果您是Adobe Commerce Intelligence Pro客戶，請聯絡您的客戶成功經理或客戶技術顧問，以協調後續步驟。

## 相關閱讀

[在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
