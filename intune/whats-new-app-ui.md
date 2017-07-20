---
title: "Aktualizace uživatelského rozhraní pro aplikace Intune pro koncové uživatele"
description: "Zjistěte, co se změnilo v uživatelském rozhraní aplikací, které fungují s Intune na zařízeních pro koncové uživatele."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e2e1eb6da9114c689aae5eb06f7d7c780f35817
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Aktualizace uživatelského rozhraní pro aplikace Intune pro koncové uživatele
Zjistěte, jaké jsme v uživatelském rozhraní aplikací udělali změny, které koncoví uživatelé uvidí v této verzi Microsoft Intune. Pomůže vám to při komunikaci s uživateli a aktualizaci vlastní dokumentace, kterou jste vytvořili za účelem podpory vašeho nasazení. Můžete také zjistit, jak lépe řešit problémy uživatelů, když požádají helpdesk o podporu pomocí Portálu společnosti.

## <a name="week-of-june-12-2017"></a>Týden 12. června 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Aplikace Portál společnosti pro Android má teď novou činnost koncového uživatele pro zásady ochrany aplikací <!--1305217-->
Na základě zpětné vazby od zákazníků jsme aplikaci Portál společnosti pro Android upravili tak, aby zobrazovala tlačítko **Přístup k obsahu společnosti**. Naším záměrem je předejít zbytečné registraci koncových uživatelů, když pouze potřebují přístup k aplikacím s podporou zásad ochrany aplikací – funkce správy mobilních aplikací Intune.

Uživatel místo zahájení registrace zařízení klepne na tlačítko **Přístup k obsahu společnosti**.

![Obrázek aplikace Portálu společnosti pro Android, kde je místo standardní nabídky možností registrace uprostřed velkým písmem napsáno Přístup k obsahu společnosti](./media/and_access_company_content_after_1706.png)

Uživatel je následně přesměrován na webovou stránku Portálu společnosti, aby autorizoval použití aplikace na svém zařízení. Web Portálu společnosti ověří jeho přihlašovací údaje.

![Obrázek webu Portálu společnosti s potvrzením přihlášení.](./media/and_iwp_sign_in_auth_page_after_1706.png)

Zařízení je stále možné zaregistrovat do plné správy klepnutím na nabídku **akce**.

![Obrázek aplikace Portál společnosti pro Android se zobrazenou nabídkou v horním pravém rohu obrazovky, kde je stále k dispozici možnost registrace zařízení.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Vylepšení synchronizace aplikace s Windows 10 Creators Update <!--676505-->

Aplikace Portál společnosti pro Windows 10 teď automaticky zahájí synchronizaci pro požadavky na instalaci zařízení s Windows 10 Creators Update (verze 1703). Omezí se tím potíže s pozastavením instalací aplikace ve stavu čekající synchronizace. Uživatelé navíc budou moct synchronizaci zahájit ručně uvnitř aplikace.

![Obrázek aplikace Portál společnosti pro Windows 10, kde se právě čeká na spuštění stahování Microsoft Wordu z obchodu s aplikacemi na Portálu společnosti.](./media/w10_download_pending_after_1706.png)

![Obrázek aplikace Portál společnosti pro Windows 10 v nově zavedeném stavu automatické synchronizace a se zobrazenou stavovou zprávou o tom, že probíhá synchronizace zařízení a pokus o stažení aplikace.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nové prostředí s asistencí pro portál společnosti s Windows 10 <!---1058938--->
Aplikace Portál společnosti pro Windows 10 bude obsahovat návod s pokyny Intune pro zařízení, která nejsou identifikovaná nebo zaregistrovaná. Nové prostředí obsahuje podrobné pokyny, které provedou uživatele registrací do Azure Active Directory (která je nutná pro funkce podmíněného přístupu), a zápis do MDM (který je nutný pro funkce správy zařízení). Prostředí s asistencí bude přístupné z domovské stránky portálu společnosti. Uživatelé můžou aplikaci dál používat, i když registraci a zápis neprovedou, ale budou mít k dispozici omezené funkce.

Tato aktualizace se zobrazí pouze na zařízení s Windows 10 Anniversary Update (build 1607) a novějšími verzemi.

![Obrázek vstupní stránky aplikace Portálu společnosti pro Windows 10, kde je uprostřed v seznamu zařízení zobrazena stavová zpráva s hlášením, že právě používané zařízení ještě není nastavené pro podnikové použití a že by měl uživatel vybrat zprávu a spustit nastavení.](./media/win10_guided_enroll_select_setup_after_1706.png)

![Obrázek stránky nastavení aplikace Portálu společnosti pro Windows 10, která upozorňuje uživatele, že k zařízení musí přidat podnikový účet a potom ho můžou zaregistrovat do správy.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Obrázek stránky s výzvou k přidání podnikového účtu do zařízení v aplikaci Portál společnosti pro Windows 10, která sděluje uživateli, že musí přejít do aplikace Nastavení a vybrat možnost Připojit, aby bylo možné registraci dokončit. Obrazovka uživateli také říká, že se potom bude muset v rámci dokončení registrace vrátit do aplikace Portál společnosti.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Obrázek stránky s registrací do správy v aplikaci Portál společnosti pro Windows 10, kde je zobrazená stavová zpráva o dokončení, ve které stojí, že zařízení uživatele je teď zaregistrované a že má pokračovat klepnutím na tlačítko Další.](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Obrázek obrazovky s dokončením nastavení v aplikaci Portál společnosti pro Windows 10, která uživateli sděluje, že je všechno nastavené a že zařízení je zaregistrované a je k němu správně přidaný podnikový účet.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nová akce nabídky ke snadnému odebrání Portálu společnosti <!--1164569-->
Na základě zpětné vazby od uživatelů jsme do aplikace Portál společnosti pro Android přidali novou akci nabídky k zahájení odebrání Portálu společnosti ze zařízení. Tato akce odebere zařízení ze správy Intune, aby uživatel mohl aplikaci ze zařízení odebrat.

![Obrázek aplikace Portál společnosti pro Android s otevřenou nabídkou akcí v pravém horním rohu. Nová možnost Odebrat Portál společnosti je k dispozici jako třetí pod možnostmi Můj profil a Nastavení a nad možnostmi Podmínky, Nápověda a váš názor a O produktu.](./media/android_remove_cp_menu_action_after_1705.png)

![Obrázek potvrzovacího okna, které se otevře, když v nabídce akcí vyberete možnost Odebrat Portál společnosti. V dialogovém okně se uživateli zobrazí následující informace: „Pokud odeberete Portál společnosti, váš správce IT už nebude vaše zařízení spravovat a může odebrat přístup k podnikovým datům, aplikacím a e-mailu.“ Pak uživatele vyzve, aby potvrdil, že chce aplikaci Portál společnosti skutečně odebrat. Pokud ji uživatel chce odebrat, vybere Ano.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>Týden 5. června 2017

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Vylepšení dlaždic aplikací v aplikaci Portál společnosti pro iOS
Aktualizovali jsme vzhled dlaždic aplikací na domovské stránce tak, aby odrážely barvu brandingu nastavenou v Portálu společnosti.

**Dříve**

![Obrázek aplikace Portál společnosti pro iOS z doby před aktualizací, která zobrazovala přednastavené obrázky s výplní pro Všechny aplikace, Vybrané aplikace a Kategorie.](./media/cp_ios_homepage_before_1705.png)

**Nyní**

![Obrázek aplikace Portál společnosti pro iOS po aktualizaci, která teď odráží možnost vybrat libovolné barvy relevantní pro vaši organizaci.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Pro aplikaci Portál společnosti pro iOS je teď dostupný výběr účtu
Pokud uživatelé na zařízení s iOSem použili svůj pracovní nebo školní účet k přihlášení do jiných aplikací Microsoftu, při prvním přihlášení k Portálu společnosti se jim může zobrazit náš nový výběr účtu.

![Obrázek výběru účtu, který ukazuje příklad uživatelky jménem Robin Swanson vybírající ze svých dvou e-mailových adres. Pod oběma adresami je tlačítko, které uživatelům umožňuje přihlásit se pomocí jiného účtu.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>Duben 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nové ikony pro Managed Browser a Portál společnosti <!--918433, 918431-->

Managed Browser dostal aktualizované ikony pro verze aplikace pro Android i iOS. Nová ikona bude obsahovat aktualizovaný odznak Intune, aby byla konzistentnější s ostatními aplikacemi v Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

Portál společnosti také dostal aktualizované ikony pro verze aplikace pro Android, iOS i Windows, aby byly konzistentnější s ostatními aplikacemi v EM+S. Tyto ikony se budou postupně vydávat pro všechny platformy od dubna do konce května.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Ukazatel průběhu přihlášení v Portálu společnosti pro Android <!--953374-->

Aktualizace aplikace Portál společnosti pro Android zobrazuje indikátor průběhu přihlášení, když uživatel aplikaci spustí nebo pokračuje v jejím používání. Než uživatel získá přístup k aplikaci, indikátor postupně zobrazuje nové stavy od „Připojování...“ přes „Přihlašování...“ po „Kontrolují se požadavky na zabezpečení...“.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Vylepšený stav instalace aplikace pro aplikaci Portál společnosti ve Windows 10 <!--676495-->
Na stránce podrobností aplikace v aplikaci Portál společnosti ve Windows 10 se teď zobrazuje indikátor průběhu instalace. To platí pro moderní aplikace na zařízeních s Windows 10 Anniversary Update a novějšími verzemi.

__Před__ ![Obrázek předchozí verze načítací obrazovky, na které se jako stav zobrazovalo jen oznámení o tom, že probíhá instalace.](./media/cp_win10_install_status_before_1704.png)

__Po__ ![Obrázek aktualizované verze načítací obrazovky, na které se teď zobrazuje indikátor průběhu instalace.](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>Únor 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Nové uživatelské prostředí aplikace Portál společnosti pro Android <!--621622, announced 1702-->
Od března bude aplikace Portál společnosti pro Android odpovídat [specifikacím Material Design](https://material.io/guidelines/material-design/introduction.html) a získá tak modernější vzhled a chování. Toto vylepšené uživatelské prostředí zahrnuje:

* __Barvy__: Záhlaví karet můžou mít barvy podle vaší vlastní palety barev.

![Nalevo je obrázek aplikace Portál společnosti pro Android před aktualizací. Napravo je obrázek aplikace Portál společnosti pro Android po aktualizaci. Na obou obrázcích je karta Zařízení jako vybraná karta ze tří dostupných karet Aplikace, Zařízení a Kontaktovat oddělení IT.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Rozhraní__: Jsou aktualizovaná tlačítka __Vybrané aplikace__ a __Všechny aplikace__ na kartě __Aplikace__. Tlačítko __Hledat__ je teď plovoucí tlačítko akce.

![Nalevo je obrázek aplikace Portál společnosti pro Android před aktualizací. Napravo je obrázek aplikace Portál společnosti pro Android po aktualizaci. Na obou obrázcích je karta Aplikace jako vybraná karta ze tří dostupných karet Aplikace, Zařízení a Kontaktovat oddělení IT.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navigace__: V části Všechny aplikace se teď zobrazují karty __Doporučené__, __Vše__ a __Kategorie__, které zjednodušují navigaci. __Kontaktovat oddělení IT__ je teď jednodušší a s vylepšenou čitelností.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Leden 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernizace webu Portál společnosti <!--753980, announced 1701-->
Od února bude web Portál společnosti podporovat aplikace zaměřené na uživatele, kteří nemají spravovaná zařízení. Tento web bude podobně jako ostatní produkty a služby Microsoftu používat nové kontrastní barevné schéma, dynamické ilustrace a „hamburgerovou“ nabídku ![Obrázek hamburgerové nabídky, která je teď přidaná v levém horním rohu webu Portál společnosti](./media/CP_hamburger_menu.png) , která bude obsahovat kontaktní údaje helpdesku a informace o existujících spravovaných zařízeních. Cílová stránka bude mít nové uspořádání, které zdůrazní aplikace dostupné uživatelům – s karusely pro Vybrané a Nedávno aktualizované aplikace.

![Vlevo je obrázek současné verze webu Portál společnosti s předchozí verzí zobrazení Aplikace, Moje zařízení, Doporučené a Kategorie. Vpravo je obrázek aktualizované verze webu Portál společnosti s novým karuselem aplikací, seznamem Nedávno publikované aplikace a aktualizovaným zobrazením Kategorie.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Již brzy v uživatelském rozhraní
Zde najdete plánované aktualizace našeho uživatelského rozhraní, které vylepší uživatelské prostředí.

> [!Note]
> Upozorňujeme, že následující obrázky mohou být náhledy a avizovaný produkt se od prezentovaných verzí může lišit.

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Vylepšené přihlašování k aplikacím Portál společnosti na všech platformách <!--User Story 1132123-->

Avizujeme změnu, kterou uvedeme během několika nadcházejících měsíců a která vylepší přihlašování k aplikacím Portál společnosti Intune v systémech Android, iOS a Windows. Nové uživatelské prostředí se automaticky zobrazí na všech platformách pro aplikaci Portál společnosti, až Azure AD tuto změnu provede. Kromě toho se teď uživatelé můžou k Portálu společnosti přihlašovat z jiného zařízení pomocí vygenerovaného kódu na jedno použití. To se hodí hlavně v případech, kdy se uživatelé potřebují přihlásit bez přihlašovacích údajů.  

Níže můžete vidět předchozí způsob přihlašování, nový způsob přihlašování pomocí přihlašovacích údajů a nový způsobu přihlašování z jiného zařízení.

__Předchozí způsob přihlašování__

![Přihlašovací stránka Portálu společnosti s ikonou osoby před grafickým znázorněním webu. Pod tím je tlačítko „Přihlásit se“. Odkaz dole vede na informace Microsoftu o ochraně osobních údajů a souborech cookie.](./media/cp_ios_aad_signin_before_1704_001.png)

![Po klepnutí na Přihlásit se uživatel zadá své přihlašovací údaje na této stránce, která požádá o uživatelův e-mail a heslo a současně nabídne způsoby, jak vyřešit problémy s heslem.](./media/cp_ios_aad_signin_before_1704_002.png)

![Po zadání hesla aplikace Portál společnosti zobrazí pruh načítání a přihlásí se.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nový způsob přihlašování__

![Přihlašovací stránka Portálu společnosti s ikonou osoby před grafickým znázorněním webu. Pod tím je tlačítko „Přihlásit se“. Odkaz dole vede na informace Microsoftu o ochraně osobních údajů a souborech cookie.](./media/cp_ios_aad_signin_after_1704_001.png)

![Uživatel je vyzván, aby zadal jenom e-mailovou adresu místo zadání e-mailu a hesla na stejné obrazovce.](./media/cp_ios_aad_signin_after_1704_002.png)

![Po přijetí e-mailové adresy je uživatel vyzván k zadání hesla.](./media/cp_ios_aad_signin_after_1704_003.png)

![Po absolvování procesu ověřování aplikace Portál společnosti zobrazí pruh načítání a přihlásí se.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Nový způsob přihlášení při přihlašování z jiného zařízení__

![Přihlašovací stránka Portálu společnosti s ikonou osoby před grafickým znázorněním webu. Pod tím je tlačítko „Přihlásit se“. Odkaz dole vede na informace Microsoftu o ochraně osobních údajů a souborech cookie.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Klepněte na odkaz __Přihlásit z jiného zařízení__.

![Zobrazí se pokyny, abyste ze svého pracovního počítače přešli na stránku aka.ms/devicelogin s jedinečným přístupovým kódem a pak kód použili k přihlášení.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Spusťte prohlížeč a přejděte na [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Obrázek uživatelova prohlížeče na pracovním počítači místo aplikace Portál společnosti. Zobrazená stránka „Přihlášení na zařízení“ uživatele vyzve k zadání kódu, který dostal v aplikaci Portál společnosti.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Zadejte kód, který se vám zobrazil v aplikaci Portál společnosti. Když vyberete __Pokračovat__, budete moct provést ověření pomocí libovolné metody, kterou vaše společnost podporuje, například pomocí čipové karty.

![Uživatel zadal svůj jedinečný kód do pole a web „Přihlášení na zařízení“ požádal o potvrzení, že je Portál společnosti Intune správnou aplikací, která má získat ověření pro přihlášení.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Potvrzovací stránka, která uvádí, že se uživatel na svém zařízení přihlásil k aplikaci Portál společnosti a že tuto stránku může zavřít.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

Aplikace Portál společnosti se začne přihlašovat.

![Po absolvování procesu ověřování aplikace Portál společnosti zobrazí pruh načítání a přihlásí se.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)
### <a name="see-also"></a>Viz taky
* [Blog Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Plán cloudové platformy](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Co je nového v Intune](https://docs.microsoft.com/intune/whats-new)