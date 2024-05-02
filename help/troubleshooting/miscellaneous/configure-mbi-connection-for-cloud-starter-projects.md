---
title: 為現有的Adobe Commerce入門專案設定Cloud Intelligence連線
description: 本文提供解決方案，協助您為現有的Adobe Commerce入門專案設定Cloud Intelligence連線。
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# 為現有的Adobe Commerce入門專案設定Cloud Intelligence連線

>[!NOTE]
>
>Adobe Commerce Intelligence先前稱為Magento Business Intelligence (MBI)。

本文提供解決方案，協助您為現有的Adobe Commerce入門專案設定Cloud Intelligence連線。

## 受影響的產品和版本

雲端入門版Adobe Commerce （所有版本）

## 問題

您想要為現有的Commerce Starter專案設定Cloud Intelligence連線。

>[!NOTE]
>
>Adobe不再支援新的Cloud Starter訂閱，但如果您有現有的Starter專案，您將需要遵循下方提供的步驟來設定連線。

## 解決方案

若要針對雲端入門專案啟用Commerce Intelligence，請建立Commerce Intelligence帳戶、建立SSH金鑰，最後連線至您的Adobe Commerce資料庫。

請依照下列步驟執行：

1. 建立您的Adobe Commerce Intelligence帳戶：

   * 前往 [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * 瀏覽至 **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * 按一下 **[!UICONTROL Create Instance]**. 如果沒有看見此按鈕，請連絡您的客戶成功案例經理或客戶技術顧問。
   * 選取您的Cloud Starter訂閱。 如果您只有Cloud Starter訂閱，系統就會自動選取此選項。
   * 按一下 **[!UICONTROL Continue]**.
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

   在連線資料庫以進行入門流程中的第三步之前，您需要收集一些資訊。 您將填入 *[!UICONTROL Connect your database]* 步驟9中的頁面。

1. 建立專屬的Commerce Intelligence使用者。

   * 建立新使用者 [account.adobe.com](https://account.adobe.com/).
   * 前往 [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) 以產生您的Adobe Commerce帳戶。
   * 為什麼是新的使用者？ Adobe Commerce Intelligence需要新增至專案的使用者持續擷取新資料，以傳輸到帳戶的Commerce Intelligence資料倉儲。 此使用者將擔任該連線。 步驟4會將此使用者新增至專案。
   * 擁有專屬的Commerce Intelligence使用者是為了防止新增的使用者不慎停用或刪除並停止Commerce Intelligence連線。

1. 將新建立的使用者新增到專案的主要環境，做為 *投稿人*.

   ![將使用者新增為投稿人](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. 取得Commerce Intelligence SSH金鑰。

   * 前往 **[!UICONTROL Connect your database]** Commerce Intelligence頁面設定使用者介面，然後向下捲動至 **[!UICONTROL Encryption settings]**.
   * 對於欄位， **[!UICONTROL Encryption Type]**，選擇 **[!UICONTROL SSH Tunnel]**.
   * 從下拉式清單，您可以複製並貼上提供的MagentoBI Essentials公開金鑰。

   ![加密設定](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. 將新的MagentoBI Essentials公開金鑰新增到步驟5中建立的Commerce Intelligence使用者。

   * 前往 [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). 針對已建立的新Commerce Intelligence使用者，以您的帳戶登入資訊登入。 然後前往 **[!UICONTROL Account Settings]** 標籤。
   * 向下捲動頁面，並展開SSH金鑰的下拉式清單。 然後按一下 **[!UICONTROL Add a public key]**.

   ![新增公開金鑰](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * 從上方新增MagentoMBI Essentials SSH公開金鑰。

   ![新增SSH公開金鑰](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. 提供Business IntelligenceEssentials MySQL認證。

   * 更新您的 `.magento/services.yaml`.

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

   * 更新您的 `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. 取得將資料庫連線至Commerce Intelligence的資訊。

   執行 `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` 以取得連線資料庫的資訊。

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
   * 密碼： [在步驟8的輸出中提供輸入密碼。]
   * 資料庫名稱：主要
   * 表格首碼： [如果沒有表格首碼，則保留空白]

1. 設定您的 [!UICONTROL Timezone Settings].

   ![時區設定](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *輸入*

   * 資料庫：時區：UTC
   * 所需時區： [選擇要顯示資料的時區。]

1. 取得加密設定的資訊。

   * 專案UI會提供SSH存取字串。 此字串可用來收集設定您的時遠端位址和使用者名稱所需的資訊。 **[!UICONTROL Encryption settings]**. 選取 **[!UICONTROL SSH]** 檢視您的使用者名稱與遠端位址。 在之前的文字字串 *@* 是您的使用者名稱和之後的文字字串 *@* 是您的遠端位址。

   ![存取網站主版](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. 為您的輸入資訊 [!UICONTROL Encryption Settings].

   ![加密設定](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *輸入*

   * 加密型別： SSH通道
   * 遠端位址： ssh.us-3.magento.cloud
   * 使用者名稱：vfbfui4vmfez6-master-7rqtwti—mymagento
   * 連線埠：22

1. 按一下 **[!UICONTROL Save Integration]**.
1. 您現在已成功連線至您的Commerce Intelligence Essentials帳戶。
1. 如果您是Adobe Commerce Intelligence Pro客戶，請聯絡您的客戶成功經理或客戶技術顧問，以協調後續步驟。
