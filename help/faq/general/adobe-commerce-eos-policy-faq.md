---
title: Adobe Commerce軟體終止支援常見問題集
description: 下列常見問題集旨在協助商家、開發人員和合作夥伴瞭解Adobe Commerce針對受影響版本Adobe Commerce的已發佈終止支援(EOS)日期的影響。
exl-id: ec147307-46eb-4a3a-8572-a014b091c58a
feature: Best Practices, Compliance, Console
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Adobe Commerce軟體終止支援常見問題集

下列常見問題集旨在協助商家、開發人員和合作夥伴瞭解Adobe Commerce針對受影響版本Adobe Commerce的已發佈終止支援(EOS)日期的影響。

## 一般規定

### 我可以在哪裡找到所有Adobe Commerce版本的軟體支援日期？

您可以在[Adobe Commerce軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)中找到Adobe Commerce軟體生命週期原則與軟體支援日期。 我們也會在[開發人員檔案頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/versions)上發佈終止支援(EOS)日期。

### Adobe終止支援某個Adobe Commerce軟體版本代表什麼意思？

當Adobe終止支援其Adobe Commerce軟體版本時，您可能會遇到以下情況：

* Adobe Commerce將不再針對該版本建立進一步的產品變更（包括功能、品質、安全性及PCI法規遵循變更）。
* EOS版本將不再接受或合併社群提取請求。 Commerce Marketplace中僅與不支援的Adobe Commerce版本相容的擴充功能將會移除。
* 將不支援版本的線上檔案會被移除（例如開發人員檔案資料）。
* Adobe Commerce版本終止支援後提交的支援票證無法解析（下方提供詳細的技術支援資訊）。

### 使用不支援Adobe Commerce軟體的商戶會有什麼影響？

我們強烈建議僅使用支援的軟體。

如果您決定繼續使用已終止支援的軟體，您將不再收到重要的產品更新或技術支援，通常包括最新的安全性更新。 使用不支援的軟體可能會影響下列區域：

**提供安全的購物體驗：**

* 您需要花費資源評估並僱用協力廠商來提供安全性支援、修正和更新。
* 一旦不再支援Adobe Commerce軟體的某個版本，該版本就不再符合[PCI規範](https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security)。 發生此情況時，您可能會遭到罰款、信用卡處理能力被移除，或受到其他處罰。
* 由於大多數的利用漏洞會鎖定與最新安全性更新不符的安裝，因此我們一律建議商戶保持其軟體為最新狀態，並在有安全性更新可用時立即安裝。 商戶必須自行決定如何透過適當的保障與安全控制措施來維護其線上商店的安全，以保護其網站和客戶的個人資料。 其中一種最佳方式是安裝最新的修補程式、修正程式和軟體更新，並持續監控您的網站和Admin Console是否有異常活動。

**有效率地運作**

* 由於舊版的Adobe Commerce軟體不受支援，因此可用的開發人員和合作夥伴數量會日益減少，當他們調整營運方向，以採用更新的技術時，還能為過時的版本提供支援。 一般而言，其結果是軟體維護人才的數量與品質會降低，而軟體的維護成本會增加。
* 對於不支援的Adobe Commerce軟體，周邊技術和相依性也可能會達到其生命週期的終點（例如PHP、MYSQL、REDIS、SOLR）。 因此，管理和維護安全且合規的網站變得越來越困難。
* 擴充功能開發人員也日益注重最新技術和相容的平台。 因此，他們可能無法繼續為不受支援的Adobe Commerce版本維護擴充功能。
* 使用不受支援的Adobe Commerce軟體版本通常會導致在維護舊平台時花費更多金錢和資源，而不是將這些資源用於持續的業務創新和增長。

**積極成長**

* Adobe持續投資開發新技術和新功能。 透過保持最新的軟體，您可以利用更新的技術和功能，協助您的企業更具策略性地運作，並以更快的速度成長。

### 有哪些範例可說明商戶如何透過最新的Adobe Commerce軟體，從新技術中獲益？

您可以透過下列幾種方式，大幅受益於持續使用最新的Adobe Commerce軟體：

* 除了讓您的平台保持最新狀態，並具備最新的安全性保護（包括PCI相容性），升級至支援的版本還能改善效能和擴充性，讓您能夠使用最新的創新技術。
* Adobe Commerce 2.4.4將於2022年4月12日推出，標誌著在商務功能、效能和保護上向前邁進了一步。 為未來數年的Adobe創新奠定基礎，協助商務商務彈性。 最新版本建置在最新版PHP 8.1上，可讓商戶透過以下方式未來證明其數位商業業務：
   * 更快速地存取SaaS服務所提供的創新功能，例如產品Recommendations、付費服務和即時搜尋
   * 更輕鬆、更符合成本效益的維護與升級
   * 持續彈性，可自訂並符合獨特的業務需求
   * 大幅提升效能與擴充能力
   * 監控平台健全狀態的更佳開發人員體驗和工具

### 要避免軟體終止支援問題，該怎麼辦？

您的Commerce平台是貴公司的重要商務系統，及時瞭解最新資訊是商務的重要持續投資。 數位店面的最新技術和安全性更新在許多層面上都很重要，可協助促進創新和成長。

移至最新版Adobe Commerce軟體可能需要時間和資源才能順利執行。 您最好在支援結束日期之前儘早進行規劃，以確保您有適當的時間和資源在預算內如期實現您的策略目標。 為了協助您進行下一次升級，Adobe已發佈[2.4升級指南](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=zh-Hant)，其中包含要遵循的最佳實務和技術步驟，以及執行升級時要使用的工具和資源。

另一個重要的考量是儘早預留開發人員和合作夥伴資源。 合作夥伴的時間和資源經常在支援結束日期之前預定，導致協助移轉專案的資源大幅減少。 建議您至少每年討論一次三年滾動計畫，並確定下一年的計畫和預算。 使用[Adobe的發行行事曆](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/schedule)追蹤發行日期。

### Adobe Commerce支援終止時，我可以使用協力廠商服務提供者提供軟體支援嗎？

可以，您可以尋找會針對不支援的Adobe Commerce版本提供支援的安全性公司、開發人員或合作夥伴。 您有責任評估這些提供者、視需要重新認證合規性，以及識別並解決可能影響您的企業和客戶的持續性安全性威脅。

### 我擁有Adobe Commerce的授權，授權期限超過所述的支援結束日期或該版本。 如果我選擇不移至支援的版本，Adobe會在授權有效期內繼續為不受支援的版本提供軟體支援嗎？

Adobe Commerce授權提供您存取及使用一般可用Adobe Commerce版本的權利，包括存取及使用不支援的版本。 無論您的軟體版本是否受到支援，都需要以目前的授權費用持續保持最新狀態，才能繼續存取及使用Adobe Commerce軟體。 這會在您的Adobe Commerce合約結束時結束。

Adobe Commerce授權不針對達到並超過支援結束日期的版本提供軟體支援。 重要的是，如果您仍使用不受支援的軟體，您將需要自行管理並支付安全性修補程式和PCI法規遵循重新認證的費用，而且可能會承擔額外的安全性風險和責任。

### 軟體版本到達並超過支援結束日期時是否會「關閉」？

否，一旦達到或超過支援結束日期，Adobe Commerce軟體不會「關閉」。 只要您的帳戶狀況良好，即使是不支援的Adobe Commerce軟體，您的授權仍然有效，但是您將負責PCI法規遵循重新認證，並且無法再提交支援票證。 最重要的是，您將不會再收到協助保護數位店面的安全性修補程式。

### 授權過期後，我可以繼續使用Adobe Commerce軟體嗎？

Adobe Commerce授權到期後，您必須停止使用Adobe Commerce軟體，並刪除該軟體的所有版本。 只要您的帳戶正常運作，Adobe Commerce授權即可讓您存取及使用一般可用的Adobe Commerce版本。

## 技術布建

### 在軟體版本的支援結束日期之前開啟的支援票證，即便在支援結束日期過後，是否仍會繼續處理以供解決？

可以，即使軟體版本的支援結束日期已過，在軟體版本支援結束日期之前開啟的支援票證仍會繼續處理並解決。 但是，解決支援票證可能取決於解決是否依賴於Adobe Commerce控制範圍以外的元件（即PHP、jQuery等），這些元件已過期或達到支援終止狀態。 在這些情況下，可透過指示您升級到最新版本來解決支援服務單。

### 如果我開啟軟體支援即將結束之軟體版本的票證，Adobe會優先處理這些票證，以便在支援結束日期前解決嗎？

否，Adobe不會根據這些軟體版本的支援結束日期，重新排列支援票證的優先順序。 支援票證會根據票證的連絡原因、環境和業務影響所衍生的內部演演算法來處理。

### 對於在支援日期結束前開啟的支援票證，是否有警報提醒商家即將結束支援？

否，沒有提醒警報通知支援票證使用者支援日期即將結束。 票證開啟者有責任知道其所在的Adobe Commerce版本的支援結束日期，這些日期可在我們的[Adobe Commerce軟體生命週期原則](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)中找到。

### 如果軟體版本的支援票證在該版本的支援結束日期之後開啟，是否仍可繼續處理以解決問題？

否，Adobe Commerce將無法解決在該軟體版本的支援結束日期之後開啟的支援票證。
