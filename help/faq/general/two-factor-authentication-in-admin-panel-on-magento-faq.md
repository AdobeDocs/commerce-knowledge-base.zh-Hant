---
title: Adobe Commerce常見問題集的「管理面板」中的雙因素驗證
description: 1. **什麼是管理面板上的雙因素驗證？ 變更內容?**雙因素驗證(2FA)是額外的保全性層級，可驗證您的身分識別，因此即使有人知道您的密碼，也只有您可以存取您的管理員帳戶。 Adobe在2.3.0版中新增Commerce管理面板中2FA的支援，以保護管理員帳戶免受未經授權的存取。 在2.4.0中，Admin Panel上的2FA預設為啟用，且在透過UI或Web API登入Admin之前必須先設定。 Adobe強烈建議不要停用2FA模組。
exl-id: 77b57c11-fcde-4bc6-814e-45fa990cc491
feature: Admin Workspace, Best Practices
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---

# Adobe Commerce常見問題集的「管理面板」中的雙因素驗證

1. **什麼是Admin Panel上的雙因素驗證？ 變更內容？** 雙因素驗證(2FA)是驗證您身分的額外安全性層，即使有人知道您的密碼，也只有您可以存取管理員帳戶。 Adobe在2.3.0版中新增Commerce管理面板中2FA的支援，以保護管理員帳戶免受未經授權的存取。 在2.4.0中，Admin Panel上的2FA預設為啟用，且在透過UI或Web API登入Admin之前必須先設定。 Adobe強烈建議不要停用2FA模組。
1. **為何2.4.0中預設會啟用2FA？** 透過2FA提供額外的驗證層級，這是安全的預設設定，可提供額外的驗證層級，使管理入口網站更安全，減少略過攻擊的攻擊面，並降低安全事件的潛在風險。
1. **此2FA設定可以在2.4.0上停用嗎？** 我們強烈建議您不要停用此安全性最佳實務，以及具有雙因素驗證的額外保護層。
1. **哪些版本支援2FA？** 2.3.0已新增對2FA的支援，但在2.4.0中預設為啟用。
1. **如何在2.3上啟用2FA？** 如需在Adobe Commerce 2.3上啟用2FA的步驟，請參閱 [安裝2FA](https://devdocs.magento.com/guides/v2.3/security/two-factor-authentication.html#install-2fa) （位於我們的開發人員檔案中）。
1. **無論所有IP或網路為何，是否需要2FA作為管理員？** 在2.4.0中，2FA預設為啟用，無論是否使用IP或網路都為必要。 這是我們建議所有客戶遵循的安全性最佳實務。 如需2FA的其他詳細資料，請參閱 [雙因素驗證](https://devdocs.magento.com/guides/v2.4/security/two-factor-authentication.html) （位於我們的開發人員檔案中）。
1. **我沒有智慧型手機，該如何啟用2FA？** Admin Panel上的2FA支援下列驗證器：Google authenticator、Authy、U2F key和Duo Security。 未擁有智慧型手機的管理員使用者可以使用U2F金鑰，或針對Google authenticator等驗證者使用瀏覽器擴充功能。
1. **您可以在Adobe Commerce中僅對少數使用者啟用2FA，或每個使用者在登入時都需要使用2FA嗎？** Adobe Commerce建議所有管理員使用者在登入其管理員帳戶時啟用2FA。 對於在Adobe Commerce 2.4及更高版本上執行的網站商店，預設會為每個使用者啟用2FA。
1. **在「管理面板」上設定2FA時的預期行為為何，我是否能在設定時使用已收到電子郵件的連結，並使用與我已登入並要求2FA設定的不同瀏覽器？** 使用者無論是否已登入，都應該能夠在任何瀏覽器中開啟電子郵件連結。 基於安全理由，他們在此過程中只能開啟一個工作階段，如果他們切換瀏覽器，則需要再次驗證。 2FA的優點在於可強制使用者使用兩種不同的方法來驗證其身分。 在此設定案例中，存取使用者的電子郵件只是一個方法，這表示他們仍必須提供另一個方法。 在這個過程中，只有密碼作為第二個選項。 因此，使用者無法單獨使用電子郵件連結來登入，而且如果他們切換瀏覽器或尚未登入，在可以繼續之前，系統會提示使用者輸入密碼。
1. **2FA設定是否需要變更ACL設定，並授與非管理員使用者的存取權以變更2FA管理員設定，以允許個別使用者設定其個人2FA？** 有兩種「雙因素驗證」 [ACL](https://devdocs.magento.com/guides/v2.4/ext-best-practices/tutorials/create-access-control-list-rule.html) 介面中的資源。 一個允許全域設定(**商店** >設定> **設定** > **安全性** > **2FA**)和另一個可讓使用者使用其個人2FA (**系統** > **許可權** > **2FA**)。 全域設定可供管理員型別使用者設定系統，而非管理員使用者需要第二類ACL才能登入並設定自己的2FA設定。 允許全域設定的ACL可讓擁有設定許可權的管理員設定全域設定，而不需要個別使用者變更設定。 當使用者登入並看到「存取遭拒」畫面，他們可以造訪https://``<magento store>``/&lt;admin _path=&quot;&quot;>/tfa/tfa/requestconfig/存取個人設定。 這是2.4.1/2.3.6/2.4.0-p1 （安全性套件1.1.0）中的已知問題，並將在2.4.2/2.3.7/2.4.1-p1 （安全性套件1.1.1）中解決。
