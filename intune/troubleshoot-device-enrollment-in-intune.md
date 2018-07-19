---
title: Řešení potíží při registraci zařízení
description: Doporučení pro řešení potíží s registrací zařízení
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b540cd2b2751712604c0ae7172015cb109c9c1d8
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039433"
---
# <a name="troubleshoot-device-enrollment-in-intune"></a>Řešení potíží s registrací do služby Intune

Tento článek obsahuje doporučení pro řešení potíží s registrací zařízení. Pokud tyto informace váš problém nevyřeší, přečtěte si téma [Jak získat podporu pro Microsoft Intune](get-support.md), ve kterém najdete další způsoby, jak získat nápovědu.


## <a name="initial-troubleshooting-steps"></a>První kroky při řešení potíží

Než začnete řešit potíže, ujistěte se, že jste správně nakonfigurovali Intune pro povolení registrace. Můžete si prostudovat informace o těchto požadavcích na konfiguraci:

-   [Příprava registrace zařízení v Microsoft Intune](setup-steps.md)
-   [Nastavení správy zařízení s iOSem a Mac OS](ios-enroll.md)
-   [Nastavení správy pro zařízení s Windows](windows-enroll.md)
-   [Nastavení správy zařízení s Androidem](android-enroll.md) – nejsou třeba žádné další kroky

Můžete také zkontrolovat správné nastavení času a data na zařízení uživatele:

1. Restartujte zařízení.
2. Zkontrolujte, že nastavení času a data se přibližně shoduje s časem GMT (interval -12 až +12 hodin vzhledem k času GMT, podle časového pásma koncového uživatele).
3. Odinstalujte a znovu nainstalujte Portál společnosti Intune (pokud se používá).

Uživatelé spravovaných zařízení můžou pro vaši potřebu shromažďovat protokoly registrace a diagnostiky. Pokyny pro uživatele ke shromažďování protokolů najdete tady:

- [Odeslání chyb registrace zařízení s Androidem správci IT](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Odeslání chyb zařízení s iOSem správci IT](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Obecné problémy s registrací
K těmto problémům může docházet na všech platformách zařízení.

### <a name="device-cap-reached"></a>Dosažení limitu zařízení
**Problém:** Při registraci se uživateli na zařízení zobrazí chyba, na zařízení se systémem iOS třeba chyba **Portál společnosti není dočasně k dispozici**, a protokol DMPdownloader.log v Configuration Manageru obsahuje chybu **DeviceCapReached**.

**Řešení:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Kontrola počtu zaregistrovaných a povolených zařízení

Podle následujícího postupu zkontrolujte, jestli nemá uživatel přiřazeno více zařízení, než je maximální povolený počet:

1. V Intune zvolte **Registrace zařízení** > **Omezení registrace** > **Omezení limitů počtů zařízení**. Poznamenejte si hodnotu uvedenou ve sloupci **Limit počtu zařízení**.

2. V Intune zvolte **Uživatelé** > **Všichni uživatelé** > vyberte požadovaného uživatele > **Zařízení**. Poznamenejte si počet zařízení.

3. Pokud počet zaregistrovaných zařízení uživatele se už rovná počtu uvedenému v omezení limitu počtu zařízení, nemůže si daný uživatel žádná další zařízení zaregistrovat, dokud:
    - [nebudou odebrána existující zařízení](devices-wipe.md), nebo
    - nezvýšíte limit počtu zařízení [nastavením omezení zařízení](enrollment-restrictions-set.md#set-device-limit-restrictions).

Pokud se chcete vyhnout dosažení limitu počtu zařízení, nezapomínejte odebírat zastaralá zařízení.

> [!NOTE]
> 
> Limitu registrace zařízení se můžete vyhnout tak, že použijete účet správce registrace zařízení, jak je popsáno v tématu [Registrace firemních zařízení pomocí správce registrace zařízení v Microsoft Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
> 
> Pokud se pro přihlašovací údaje uživatele, jehož účet přidáte do účtu správců registrace zařízení, vynucuje zásada podmíněného přístupu, nebude možné dokončit registraci.

### <a name="company-portal-temporarily-unavailable"></a>Portál společnosti není dočasně k dispozici
**Problém:** Uživateli se na zařízení zobrazí chyba **Portál společnosti není dočasně k dispozici**.

**Řešení:**

1.  Odeberte ze zařízení aplikaci Portál společnosti Intune.

2.  Otevřete v zařízení prohlížeč, přejděte na adresu [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) a pokuste se přihlásit uživatele.

3.  Pokud se uživateli nepodaří přihlásit se, měl by zkusit jinou síť.

4.  Pokud to nepomůže, zkontrolujte, jestli správně proběhla synchronizace přihlašovacích údajů uživatele se službou Azure Active Directory.

5.  Pokud se uživatel úspěšně přihlásí, zařízení se systémem iOS zobrazí výzvu k instalaci aplikace Portál společnosti Intune a k registraci. V zařízení s Androidem budete muset aplikaci Portál společnosti Intune nainstalovat ručně. Potom se můžete zkusit znovu zaregistrovat.

### <a name="mdm-authority-not-defined"></a>Není definována autorita MDM
**Problém:** Zobrazí se chyba **Není definována autorita MDM**.

**Řešení:**

1.  Ověřte, že je [správně nastavená](mdm-authority-set.md) autorita MDM.
    
2.  Ověřte správnou synchronizaci přihlašovacích údajů uživatele se službou Azure Active Directory tím, že zkontrolujete, jestli hlavní název uživatele (UPN) odpovídá údajům služby Active Directory na portálu Office 365.
    Pokud hlavní název uživatele neodpovídá údajům služby Active Directory:

    1.  Vypněte na místním serveru službu DirSync.

    2.  Odstraňte neodpovídajícího uživatele ze seznamu uživatelů na **portálu účtů Intune** .

    3.  Počkejte zhruba hodinu, aby měla služba Azure dost času odebrat nesprávná data.

    4.  Znovu zapněte službu DirSync a zkontrolujte, jestli je teď uživatel správně synchronizovaný.

3.  Pokud používáte nástroj System Center Configuration Manager se službou Intune, zkontrolujte, jestli má uživatel platné ID uživatele cloudu:

    1.  Otevřete nástroj SQL Management Studio.

    2.  Připojte se k příslušné databázi.

    3.  Otevřete složku databází a vyberte a otevřete složku **CM_název_db**, kde název_db odpovídá názvu databáze zákazníka.

    4.  Nahoře zvolte **Nový dotaz** a spusťte tyto dotazy:

        -   Zobrazení všech uživatelů: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Pokud chcete zobrazit konkrétní uživatele, použijte tento dotaz, kde %testuser1% představuje adresu username@domain.com pro uživatele, kterého chcete vyhledat: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Po napsání dotazu zvolte **!Execute**.
        Když se vrátí výsledky, vyhledejte ID uživatele cloudu.  Pokud se žádné ID nenajde, nemá daný uživatel licenci pro používání služby Intune.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Pokud název společnosti obsahuje speciální znaky, není možné vytvořit zásadu ani registrovat zařízení
**Problém:** Nemůžete vytvořit zásadu nebo zaregistrovat zařízení.

**Řešení:** V [Centru pro správu Office 365](https://portal.office.com/) odeberte zvláštní znaky z názvu společnosti a uložte informace o společnosti.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Pokud máte více ověřených domén, není možné se přihlásit nebo zaregistrovat zařízení
**Problém:** Pokud do AD FS přidáte druhou ověřenou doménu, nemusí být uživatelé s příponou hlavního názvu uživatele (UPN) druhé domény schopni se přihlásit na portály nebo zaregistrovat zařízení.


<strong>Řešení:</strong> Zákazníci s předplatným Microsoft Office 365, kteří používají jednotné přihlašování (SSO) prostřednictvím služby AD FS 2.0 a mají pro přípony UPN uživatelů v rámci své organizace více domén nejvyšší úrovně (například @contoso.com nebo @fabrikam.com), musí pro každou příponu nasadit samostatnou instanci federační služby AD FS 2.0. K dispozici je teď [kumulativní aktualizace pro službu AD FS 2.0](http://support.microsoft.com/kb/2607496), která ve spojení s přepínačem <strong>SupportMultipleDomain</strong> umožňuje zajistit, aby AD FS server tento scénář podporoval bez vyžadování dalších serverů služby AD FS 2.0. Další informace najdete na [tomto blogu](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Problémy na zařízeních s Androidem

### <a name="android-enrollment-errors"></a>Chyby registrace zařízení s Androidem

Následující tabulka obsahuje chyby, které se můžou koncovým uživatelům zobrazit při registraci zařízení s Androidem v Intune.

|Chybová zpráva|Problém|Řešení|
|---|---|---|
|**Správce IT musí přiřadit licence pro přístup**<br>Váš správce IT vám neudělil přístup k této aplikaci. Požádejte ho o pomoc nebo to zkuste znovu později.|Zařízení není možné zaregistrovat, protože účet uživatele nemá potřebnou licenci.|Aby si mohli uživatelé zaregistrovat svoje zařízení, musí mít přiřazenou potřebnou licenci. Tato zpráva znamená, že má uživatel špatný typ licence pro určenou autoritu pro správu mobilních zařízení. Pokud je třeba určenou autoritou pro správu mobilních zařízení Intune a uživatel používá licenci nástroje System Center 2012 R2 Configuration Manager, zobrazí se tato chyba.<br><br>Přečtěte si informace o tom, jak [přiřadit licence Intune k uživatelským účtům](/intune/licenses-assign).
|**Správce IT musí nastavit autoritu MDM**<br>Zdá se, že váš správce IT nenastavil autoritu MDM. Požádejte ho o pomoc nebo to zkuste znovu později.|Autorita pro správu mobilních zařízení není definovaná.|Autorita pro správu mobilních zařízení není určená v Intune. Přečtěte si, jak [nastavit autoritu pro správu mobilních zařízení](/intune/mdm-authority-set).|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Zařízení se nepodařilo registrovat ve službě Intune a jeho stav v konzole pro správu se zobrazuje jako Není v pořádku
**Problém:** Některá zařízení Samsung s Androidem verze 4.4.x a 5.x můžou ukončit registraci ve službě Intune. Pokud se zařízení nezaregistrují, platí pro ně tyto podmínky:

- Nemůžou přijímat zásady, aplikace a vzdálené příkazy ze služby Intune.
- V konzole pro správu se jako stav správy zobrazuje **Není v pořádku**.
- Uživatelé chránění zásadami podmíněného přístupu můžou ztratit přístup k podnikovým prostředkům.

Společnost Samsung potvrdila, že software Samsung Smart Manager dodávaný s některými zařízeními Samsung může deaktivovat Portál společnosti Intune a jeho součásti. Když je Portál společnosti v neaktivním stavu, nemůže běžet na pozadí a v důsledku toho ani kontaktovat službu Intune.

**Řešení 1:**

Řekněte uživatelům, aby aplikaci Portál společnosti spouštěli ručně. Po restartování aplikace se zařízení zaregistruje pomocí služby Intune.

> [!IMPORTANT]
> Ruční spuštění aplikace Portál společnosti je dočasné řešení, protože Samsung Smart Manager může aplikaci Portál společnosti znovu deaktivovat.

**Řešení 2:**

Řekněte uživatelům, aby se pokusili upgradovat na Android 6.0. Problém s deaktivací neplatí pro zařízení s Androidem 6.0. Pokud chcete zkontrolovat, jestli je k dispozici aktualizace, můžete přejít na **Settings (Nastavení)** > **About device (O zařízení)** > **Download updates manually (Stáhnout aktualizace ručně)** a dále postupovat podle výzev zařízení.

**Řešení 3:**

Pokud řešení 2 nefunguje, nechte uživatele provést následující postup, aby Smart Manager vyloučil aplikaci Portál společnosti:

1. Na zařízení spusťte aplikaci Smart Manager.

   ![Výběr ikony Smart Manager na zařízení](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Zvolte dlaždici **Battery** (Baterie).

   ![Výběr dlaždice Battery](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. V části **App power saving** (Úspora energie aplikace) nebo **App optimization** (Optimalizace aplikace) vyberte **Detail** (Podrobnosti).

   ![Výběr možnosti Detail (Podrobnosti) v části App power saving (Úspora energie aplikace) nebo App optimization (Optimalizace aplikace)](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. V seznamu aplikací vyberte **Portál společnosti**.

   ![Výběr aplikace Portál společnosti ze seznamu aplikací](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Zvolte **Turned off** (Vypnuto).

   ![Výběr možnosti Turned off (Vypnuto) v dialogovém okně App optimization (Optimalizace aplikace)](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. V části **App power saving** (Snížení spotřeby aplikace) nebo **App optimization** (Optimalizace aplikace) ověřte, že je Portál společnosti vypnutý.

   ![Ověření, že je Portál společnosti vypnutý](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Neúspěch instalace profilu
**Problém:** Na zařízení s Androidem se zobrazí chybová zpráva **Instalace profilu se nezdařila**.

**Řešení:**

1.  Zkontrolujte, jestli má uživatel přiřazenou příslušnou licenci pro verzi služby Intune, kterou používáte.

2.  Zkontrolujte, jestli už není zařízení zaregistrované pomocí jiného poskytovatele správy mobilních zařízení (MDM) a jestli už v něm není nainstalovaný profil správy.

3.  Potvrďte, že Chrome pro Android je výchozím prohlížečem a že jsou povolené soubory cookie.

### <a name="android-certificate-issues"></a>Problémy s certifikáty Androidu

**Problém:** Uživatelům se na zařízení zobrazí následující zpráva: *Nemůžete se přihlásit, protože vašemu zařízení chybí požadovaný certifikát.*

**Řešení 1**:

Uživatel možná bude moct načíst chybějící certifikát podle pokynů v tématu [Zařízení nemá požadovaný certifikát](/intune-user-help/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator). Pokud chyba přetrvává, vyzkoušejte Řešení 2.

**Řešení 2**:

Pokud se uživatelům stále zobrazuje chyba chybějícího certifikátu po tom, co zadali svoje podnikové přihlašovací údaje a byli přesměrováni na federované přihlašování, možná na vašem serveru Active Directory Federation Services (AD FS) chybí zprostředkující certifikát.

Příčinou chyby certifikátu je, že zařízení s Androidem vyžadují zahrnutí zprostředkujících certifikátů do odpovědi [SSL Server hello](https://technet.microsoft.com/library/cc783349.aspx). Momentálně výchozí instalace serveru AD FS nebo proxy serveru WAP – AD FS odesílá v odpovědi SSL Server hello na zprávu SSL Client hello jenom certifikát SSL služby AD FS.

Pokud chcete problém vyřešit, naimportujte certifikáty do osobních certifikátů počítačů na serveru nebo proxy serverech AD FS následujícím způsobem:

1.  Na serveru ADFS a proxy serveru klikněte pravým tlačítkem myši na **Start** > **Spustit** > **certlm.msc** a spusťte konzolu pro správu certifikátů místního počítače.
2.  Rozbalte **Osobní** a zvolte **Certifikáty**.
3.  Najděte certifikát pro vaši komunikaci služby AD FS (veřejně podepsaný certifikát) a poklikáním zobrazte jeho vlastnosti.
4.  Zvolte kartu **Cesta k certifikátu**, kde uvidíte nadřazené certifikáty certifikátu.
5.  U každého nadřazeného certifikátu zvolte **Zobrazit certifikát**.
6.  Zvolte **Podrobnosti** > **Kopírovat do souboru**.
7.  Postupujte podle pokynů průvodce a vyexportujte nebo uložte veřejný klíč nadřazeného certifikátu do požadovaného umístění souborů.
8.  Klikněte pravým tlačítkem myši na **Certifikáty** > **Všechny úkoly** > **Importovat**.
9.  Postupujte podle pokynů průvodce a naimportujte nadřazené certifikáty do **Místní počítač\Osobní\Certifikáty**.
10. Restartujte servery AD FS.
11. Výše uvedené kroky zopakujte na všech serverech a proxy serverech AD FS.

K ověření správné instalace certifikátu můžete použít diagnostický nástroj, který je dostupný na [https://www.digicert.com/help/](https://www.digicert.com/help/). Do pole **Server Address** (Adresa serveru) zadejte plně kvalifikovaný název domény serveru AD FS (například sts.contso.com) a klikněte na **Check Server** (Zkontrolovat server).

**Pokud chcete ověřit, jestli se certifikát správně nainstaloval**:

Následující kroky popisují jednom jeden z mnoha způsobů a nástrojů, pomocí kterých můžete ověřit, jestli se certifikát správně nainstaloval.

1. Přejděte na [bezplatný nástroj Digicert](ttps://www.digicert.com/help/).
2. Zadejte plně kvalifikovaný název domény serveru AD FS (například sts.contoso.com) a vyberte **CHECK SERVER** (Zkontrolovat server).

Pokud je certifikát serveru správně nainstalovaný, uvidíte ve výsledcích všechny značky zaškrtnutí. Pokud výše popsaný problém přetrvává, zobrazí se v sekcích výsledné sestavy „Certificate name matches“ (Název certifikátu odpovídá) a „SSL Certificate is correctly Installed“ (Certifikát SSL je správně nainstalovaný) červený symbol X.


## <a name="ios-issues"></a>Problémy na zařízeních s iOSem

### <a name="ios-enrollment-errors"></a>Chyby registrace zařízení se systémem iOS
Následující tabulka obsahuje chyby, které se můžou koncovým uživatelům zobrazit při registraci zařízení s iOsem v Intune.

|Chybová zpráva|Problém|Řešení|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Nepovedlo se najít žádné zásady registrace|Zkontrolujte, že jsou nastavené všechny požadavky registrace, například certifikát služby APNs (Apple Push Notification Service), a že je povolené nastavení „iOS jako platforma“. Pokyny najdete v tématu [Nastavení správy zařízení s iOSem a MacOS](ios-enroll.md).|
|DeviceCapReached|Už máte příliš mnoho registrovaných mobilních zařízení.|Než bude moct uživatel zaregistrovat další mobilní zařízení, musí odebrat jedno ze svých aktuálně zaregistrovaných mobilních zařízení z Portálu společnosti. Přečtěte si pokyny pro typ zařízení, který používáte: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios) nebo [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Došlo k potížím s certifikátem, který umožňuje komunikaci mobilního zařízení s podnikovou sítí.<br /><br />|Služba APNs (Apple Push Notification Service) poskytuje kanál umožňující registraci zařízení s iOSem. Pokud jste neprovedli kroky k získání certifikátu APNs nebo vypršela jeho platnost, pak budou pokusy o registraci neúspěšné a zobrazí se tato zpráva.<br /><br />Přečtěte si informace o nastavení uživatelů v tématu [Synchronizace služby Active Directory a přidání uživatelů do Intune](users-add.md) a článku o [uspořádání uživatelů a zařízení](groups-add.md).|
|AccountNotOnboarded|Došlo k potížím s certifikátem, který umožňuje komunikaci mobilního zařízení s podnikovou sítí.<br /><br />|Služba APNs (Apple Push Notification Service) poskytuje kanál umožňující registraci zařízení s iOSem. Pokud jste neprovedli kroky k získání certifikátu APNs nebo vypršela jeho platnost, pak budou pokusy o registraci neúspěšné a zobrazí se tato zpráva.<br /><br />Další informace najdete v tématu [Nastavení správy iOS a Mac s Microsoft Intune](ios-enroll.md).|
|DeviceTypeNotSupported|Uživatel se možná pokusil o registraci zařízení s jiným systémem než iOS. Typ mobilního zařízení, které se pokoušíte registrovat, není podporovaný.<br /><br />Potvrďte, že na zařízení běží systém iOS verze 8.0 nebo novější.<br /><br />|Zkontrolujte, jestli na zařízení uživatele běží systém iOS verze 8.0 nebo novější.|
|UserLicenseTypeInvalid|Zařízení nemůžete zaregistrovat, protože uživatelský účet ještě není členem požadované skupiny uživatelů.<br /><br />|Uživatelé můžou svoje zařízení registrovat až potom, co se stanou členy správné skupiny uživatelů. Tato zpráva znamená, že má uživatel špatný typ licence pro určenou autoritu pro správu mobilních zařízení. Pokud je třeba určenou autoritou pro správu mobilních zařízení Intune a uživatel používá licenci nástroje System Center 2012 R2 Configuration Manager, zobrazí se tato chyba.<br /><br />Další informace najdete v následujících článcích:<br /><br />Přečtěte si článek [Nastavení správy iOS a Mac pomocí Microsoft Intune](ios-enroll.md) a informace, jak nastavit uživatele, v článku [Synchronizace služby Active Directory a přidání uživatelů do Intune](users-add.md) a článku o [uspořádání uživatelů a zařízení](groups-add.md).|
|MdmAuthorityNotDefined|Autorita pro správu mobilních zařízení není definovaná.<br /><br />|Autorita pro správu mobilních zařízení není určená v Intune.<br /><br />Projděte si položku č. 1 v části „Krok 6: Registrace mobilních zařízení a instalace aplikace“ v tématu [Začínáme s 30denní zkušební verzí Microsoft Intune](free-trial-sign-up.md).|

### <a name="devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Zařízení nejsou aktivní nebo s nimi nemůže konzola správce komunikovat
**Problém:** Zařízení s iOSem se neregistrují ve službě Intune. Zařízení se musí pravidelně registrovat ve službě, aby si zachovala přístup ke chráněným podnikovým prostředkům. Pokud se zařízení nezaregistrují, platí pro ně tyto podmínky:

- Nemůžou přijímat zásady, aplikace a vzdálené příkazy ze služby Intune.
- V konzole pro správu se jako stav správy zobrazuje **Není v pořádku**.
- Uživatelé chránění zásadami podmíněného přístupu můžou ztratit přístup k podnikovým prostředkům.

**Řešení:** Podělte se s koncovými uživateli o následující řešení, která jim pomůžou znovu získat přístup k podnikovým prostředkům.

Když uživatel spustí aplikaci Portál společnosti v iOSu, aplikace mu sdělí, jestli zařízení ztratilo kontakt s Intune. Pokud aplikace zjistí, že zařízení nemá kontakt, pokusí se automaticky synchronizovat s Intune a znovu se připojit. Uživateli se zobrazí vložené oznámení **Probíhá pokus o synchronizaci...** .

  ![Oznámení Probíhá pokus o synchronizaci](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Pokud se synchronizace zdaří, zobrazí se v aplikaci Portál společnosti v iOSu vložené oznámení **Úspěšná synchronizace**, které označuje, že zařízení je v pořádku.

  ![Oznámení Úspěšná synchronizace](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Pokud se synchronizace nezdaří, uživatelům se v aplikaci Portál společnosti v iOSu zobrazí vložené oznámení **Nelze synchronizovat**.

  ![Oznámení Nelze synchronizovat](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

Pokud chcete problém opravit, musíte vybrat tlačítko **Nastavit**, které se nachází vpravo od oznámení **Nelze synchronizovat**. Po výběru tlačítka Nastavit se zobrazí obrazovka pro nastavení firemního přístupu, kde můžete podle zobrazovaných pokynů zaregistrovat zařízení.

  ![Obrazovka Nastavení firemního přístupu](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

Po registraci se zařízení vrátí do stavu správné funkce a znovu získá přístup k podnikovým prostředkům.

### <a name="verify-ws-trust-13-is-enabled"></a>Ověření, že koncový bod WS-Trust 1.3 je povolený
**Problém:** Zařízení s iOSem a programem registrace zařízení (DEP) není možné přihlásit.

Přihlášení zařízení s programem registrace zařízení s přidružením uživatele vyžaduje aktivaci uživatelského jména / smíšeného koncového bodu WS-Trust 1.3, aby bylo možné požádat o tokeny uživatele. Active Directory má tento koncový bod ve výchozím nastavení povolený. Seznam povolených koncových bodů získáte použitím rutiny prostředí PowerShell Get-AdfsEndpoint a vyhledáním koncového bodu trust/13/UsernameMixed. Příklad:

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Další informace najdete v [dokumentaci k rutině Get-AdfsEndpoint](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Další informace najdete v tématu [Doporučené postupy zabezpečení služby AD FS](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Pokud potřebujete další pomoc při určování, zda máte koncový bod WS-Trust 1.3 Username/Mixed ve svém zprostředkovateli identity federace povolený a používáte službu ADFS nebo vlastního poskytovatele identity třetí strany, obraťte se na podporu Microsoftu.


### <a name="profile-installation-failed"></a>Neúspěch instalace profilu
**Problém:** V zařízení s iOSem se zobrazí chyba **Instalace profilu se nezdařila**.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Postup řešení potíží při neúspěšné instalaci profilu

1.  Zkontrolujte, jestli má uživatel přiřazenou příslušnou licenci pro verzi služby Intune, kterou používáte.

2.  Zkontrolujte, jestli už není zařízení zaregistrované pomocí jiného poskytovatele správy mobilních zařízení (MDM) a jestli už v něm není nainstalovaný profil správy.

3.  Přejděte na [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) a po zobrazení výzvy zkuste profil nainstalovat.

4.  Potvrďte nastavení výchozích prohlížečů Safari (pro iOS) a povolení souborů cookie.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Zaregistrovaná zařízení s iOSem se při používání nástroje System Center Configuration Manager se službou Intune nezobrazí v konzole
**Problém:** Uživatel registruje zařízení s iOSem, to se ale nezobrazí v konzole pro správu nástroje Configuration Manager. Zařízení neindikuje, že je zaregistrované. Možné příčiny:

- Konektor služby Microsoft Intune v lokalitě nástroje Configuration Manager nekomunikuje se službou Intune.
- Součást Data Discovery Manager (ddm) nebo State Manager (statmgr) nezpracovává zprávy ze služby Intune.
- Mohli jste si stáhnout certifikát MDM z jednoho účtu a použít ho na jiný účet.


**Řešení:** Vyhledejte možné chyby v následujících souborech protokolu:

- dmpdownloader.log
- ddm.log
- statmgr.log

Příklady toho, co máte v těchto souborech protokolu hledat, budou brzy přidány.


## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Problémy při použití nástroje System Center Configuration Manager se službou Intune
### <a name="mobile-devices-disappear"></a>Mobilní zařízení zmizí
**Problém:** Po úspěšné registraci mobilního zařízení do Configuration Manageru dané zařízení zmizí z kolekce mobilních zařízení, ale pořád má profil pro správu a je uvedené v bráně CSS.

**Řešení:** K této situaci může dojít, protože máte vlastní proces, který odebírá zařízení nepřipojená k doméně, nebo protože uživatel vyřadil zařízení z předplatného. Pokud chcete ověřit a zkontrolovat, který proces nebo uživatelský účet odebral zařízení z konzoly nástroje Configuration Manager, postupujte podle následujících kroků.

#### <a name="check-how-device-was-removed"></a>Zjištění způsobu odebrání zařízení

1.  V konzole pro správu nástroje Configuration Manager vyberte **Monitorování** &gt;  **Stav systému** &gt; **Dotazy stavových zpráv**.

2.  Klikněte pravým tlačítkem na **Manuálně odstraněné prostředky členů kolekce** a vyberte **Zobrazit zprávy**.

3.  Vyberte příslušný čas/datum nebo období posledních 12 hodin.

4.  Najděte příslušné zařízení a podívejte se, jak došlo k jeho odebrání. Následující příklad ukazuje, že zařízení odebral účet SCCMInstall prostřednictvím neznámé aplikace.

    ![Snímek obrazovky pro diagnostiku odstranění zařízení](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Zkontrolujte, jestli nemá Configuration Manager naplánovanou úlohu, skript nebo jiný proces, který by mohl automaticky odstraňovat zařízení nepřipojená k doméně, mobilní zařízení nebo související zařízení.




### <a name="other-ios-enrollment-errors"></a>Další chyby registrace zařízení s iOSem
Seznam chyb registrace zařízení s iOSem najdete v dokumentaci v části [Řešení potíží s registrací zařízení s iOSem v Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune).

## <a name="pc-issues"></a>Problémy na počítači


|Chybová zpráva|Problém|Řešení|
|---|---|---|
|**Správce IT musí přiřadit licence pro přístup**<br>Váš správce IT vám neudělil přístup k této aplikaci. Požádejte ho o pomoc nebo to zkuste znovu později.|Zařízení není možné zaregistrovat, protože účet uživatele nemá potřebnou licenci.|Aby si mohli uživatelé zaregistrovat svoje zařízení, musí mít přiřazenou potřebnou licenci. Tato zpráva znamená, že má uživatel špatný typ licence pro určenou autoritu pro správu mobilních zařízení. Pokud je třeba určenou autoritou pro správu mobilních zařízení Intune a uživatel používá licenci nástroje System Center 2012 R2 Configuration Manager, zobrazí se tato chyba.<br>Přečtěte si informace o tom, jak [přiřadit licence Intune k uživatelským účtům](https://docs.microsoft.com/intune/licenses-assign).|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>Počítač už je zaregistrovaný – chyba hr 0x8007064c
**Problém:** Registrace selže s chybou **Počítač už je zaregistrovaný**. V protokolu registrace se zobrazuje chyba **hr 0x8007064c**.

Důvodem může být to, že již byl počítač zaregistrován dříve nebo je na něm klonovaná image počítače, který už je zaregistrovaný. Na počítači se stále nachází certifikát předchozího účtu.



**Řešení:**

1. V nabídce **Start** zadejte **Spustit** -> **MMC**.
1. Zvolte **Soubor** > **Přidat nebo odebrat moduly snap-in**.
1. Poklikejte na **Certifikáty**, zvolte **Účet počítače** > **Další** a vyberte **Místní počítač**.
1. Poklikejte na **Certifikáty (místní počítač)** a zvolte **Osobní/Certifikáty**.
1. Vyhledejte certifikát Intune, který vystavila certifikační autorita Sc_Online_Issuing. Pokud existuje, odstraňte ho.
1. Pokud existuje klíč registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey**, odstraňte ho a s ním i všechny podklíče.
1. Zkuste se znovu zaregistrovat.
1. Pokud ani tak není možné počítač zaregistrovat, vyhledejte a odstraňte klíč **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**, pokud existuje.
1. Zkuste se znovu zaregistrovat.

    > [!IMPORTANT]
    > Tato část, metoda nebo úloha obsahují kroky, které vám pomohou s úpravou registru. Pokud ale budete měnit registr a uděláte tam něco špatně, můžete mít velké problémy s počítačem. Proto je důležité, abyste pečlivě postupovali podle těchto kroků. Než začnete registr měnit, pro jistotu si ho zazálohujte. Pak budete moct v případě problémů registr obnovit.
    > Další informace o tom, jak zálohovat a obnovovat registr, najdete v tématu [Postup zálohování a obnovení registru v systému Windows](https://support.microsoft.com/kb/322756).

## <a name="general-enrollment-error-codes"></a>Obecné kódy chyb registrace

|Kód chyby|Možný problém|Navržené řešení|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |Na hodinách klientského počítače není nastavený správný čas.|Zkontrolujte, jestli jsou na klientském počítači správně nastavené hodiny a časové pásmo.|
|0x80240438, 0x80CF0438, 0x80CF402C|Nedá se připojit ke službě Intune. Zkontrolujte nastavení proxy serveru klienta.|Ověřte, že Intune konfiguraci proxy serveru na klientském počítači podporuje a že má klientský počítač přístup na internet.|
|0x80240438, 0x80CF0438|Není nakonfigurované nastavení proxy serveru v Internet Exploreru a v místním systému.|Nedá se připojit ke službě Intune. Zkontrolujte nastavení proxy serveru klienta a ověřte, že Intune konfiguraci proxy serveru na klientském počítači podporuje a že má klientský počítač přístup na internet.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Registrační balíček je zastaralý.|Z pracovního prostoru Správa si stáhněte aktuální balíček klientského softwaru a nainstalujte ho.|
|0x80043002, 0x80CF3002|Účet je v režimu údržby.|Když je účet v režimu údržby, nemůžete registrovat nové klientské počítače. Pokud si chcete prohlédnout nastavení svého účtu, přihlaste se k němu.|
|0x80043003, 0x80CF3003|Účet je odstraněný.|Ověřte, že je váš účet a předplatné Intune pořád aktivní. Pokud si chcete prohlédnout nastavení svého účtu, přihlaste se k němu.|
|0x80043005, 0x80CF3005|Klientský počítač byl vyřazen z provozu.|Pár hodin počkejte, odeberte z počítače všechny starší verze klientského softwaru s pak zkuste nainstalovat klientský software znova.|
|0x80043006, 0x80CF3006|Bylo dosaženo maximálního počtu licencí povolených pro účet.|Abyste mohli ve službě zaregistrovat víc klientských počítačů, musí si vaše organizace koupit další licence.|
|0x80043007, 0x80CF3007|Ve složce s instalačním programem se nenašel soubor certifikátu.|Než začnete s instalací, extrahujte všechny soubory. Žádné extrahované soubory nepřejmenovávejte ani nepřemísťujte: všechny soubory musí být ve stejné složce, jinak se instalace nepovede.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|Software nejde nainstalovat, protože se čeká na restartování klientského počítače.|Restartujte počítač a pak zkuste nainstalovat klientský software znova.|
|0x80070032|Na klientském počítači se nenašel minimálně jeden softwarový produkt, který je podmínkou pro instalaci klientského softwaru.|Ujistěte se, že jsou na klientském počítači nainstalované všechny požadované aktualizace, a pak zkuste nainstalovat klientský software znova.|
|0x80043008, 0x80CF3008|Nepodařilo se spustit službu Microsoft Online Management Updates.|Kontaktujte podporu podle pokynů v tématu [Jak získat podporu pro Microsoft Intune](get-support.md).|
|0x80043009, 0x80CF3009|Klientský počítač je ve službě už zaregistrovaný.|Abyste mohli klientský počítač ve službě zaregistrovat znovu, musíte ho nejdřív vyřadit.|
|0x8004300B, 0x80CF300B|Instalační balíček klientského softwaru nejde spustit, protože verze Windows, která běží na klientovi, není podporovaná.|Intune nepodporuje verzi Windows, která běží na klientském počítači.|
|0xAB2|Instalační služba systému Windows nemohla získat přístup k modulu VBScript runtime pro vlastní akci.|Tato chyba je způsobená nějakou vlastní akcí založenou na dynamických knihovnách DLL (Dynamic-Link Library). Při odstraňování problémů s knihovnou DLL budete nejspíš muset použít nástroje popsané v [článku 198038 znalostní báze podpory Microsoftu: Užitečné nástroje při problémech s balíčky a nasazením](https://support.microsoft.com/kb/198038).|
|0x80cf0440|Připojení ke koncovému bodu služby bylo ukončeno.|Zkušební nebo placený účet je pozastaven. Vytvořte nový zkušební nebo placený účet a pak opakujte pokus o registraci.|




### <a name="next-steps"></a>Další kroky
Pokud vám tyto informace o řešení potíží nepomohly, obraťte se na podporu společnosti Microsoft podle pokynů v tématu [Jak získat podporu pro Microsoft Intune](get-support.md).