---
title: Časté otázky ke správě mobilních aplikací (MAM) a ochraně aplikací
description: Tento článek poskytuje odpovědi na některé časté otázky ke správě mobilních aplikací (MAM) Intune a ochraně aplikací Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0ab616c373482109ccd402199f7b0de69fe27348
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Časté otázky ke správě mobilních aplikací (MAM) a ochraně aplikací

Tento článek poskytuje odpovědi na některé časté otázky ke správě mobilních aplikací (MAM) Intune a ochraně aplikací Intune.

## <a name="mam-basics"></a>Základní informace o MAM


**Co je MAM?** [Správa mobilních aplikací (MAM) Intune](/intune/app-lifecycle) představuje sadu funkcí Intune pro správu, s kterými můžete publikovat, doručovat, konfigurovat, zabezpečovat, monitorovat a aktualizovat mobilní aplikace pro uživatele.

**Jaké jsou výhody ochrany aplikací pomocí MAM?** MAM chrání data organizace v rámci aplikace. Díky funkci MAM bez registrace zařízení (MAM-WE) jde pracovní nebo školní aplikaci, která obsahuje citlivá data, spravovat prakticky na jakémkoliv zařízení, včetně osobních zařízení, která uživatelé používají pracovně (BYOD, bring-your-own-device). Mnoho kancelářských aplikací, jako jsou například aplikace Microsoft Office, jde spravovat přes Intune MAM. Podívejte se do oficiálního seznamu [aplikací spravovaných přes Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), který je veřejně přístupný.

**Jaké konfigurace zařízení MAM podporuje?** Intune MAM podporuje dvě konfigurace:
- **MDM+MAM Intune**: Správci IT můžou spravovat aplikace pomocí MAM a zásad ochrany aplikací jenom na zařízeních, která jsou zaregistrovaná ve správě mobilních zařízení (MDM) Intune. Pokud zákazníci chtějí spravovat aplikace pomocí MDM + MAM, měli by používat konzolu Intune na portálu Azure Portal na https://portal.azure.com.

- **MAM bez registrace zařízení:** MAM bez registrace zařízení, neboli MAM-WE, umožňuje správcům IT spravovat aplikace pomocí MAM a zásad ochrany aplikací na zařízeních, která nejsou zaregistrovaná ve správě mobilních zařízení Intune. To znamená, že aplikace je možné spravovat pomocí Intune na zařízeních, která jsou zaregistrovaná u jiných poskytovatelů EMM. Pokud zákazníci chtějí spravovat aplikace pomocí MAM-WE, měli by používat konzolu Intune na portálu Azure Portal na http://portal.azure.com. Aplikace je také možné spravovat pomocí Intune na zařízeních zaregistrovaných pomocí jiných poskytovatelů správy firemních mobilních zařízení (Enterprise Mobility Management (EMM)) nebo na zařízeních vůbec v MDM nezaregistrovaných.


## <a name="app-protection-policies"></a>Zásady ochrany aplikace

**Co jsou zásady ochrany aplikací**? Zásady ochrany aplikací jsou pravidla, která zajistí, že data organizace budou zabezpečená nebo vázaná ve spravované aplikaci. Zásada může být pravidlo, které je vynuceno, když se uživatel pokusí pracovat s firemními daty nebo je přesunout, nebo sada akcí, které jsou zakázané nebo monitorované, pokud je uživatel uvnitř aplikace.

**Jaké jsou příklady zásad ochrany aplikací?** Podrobné informace o každém nastavení zásad ochrany aplikací najdete v tématech [Nastavení zásad ochrany aplikací pro Android](app-protection-policy-settings-android.md) a [Nastavení zásad ochrany aplikací pro iOS](app-protection-policy-settings-ios.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplikace, které se dají spravovat pomocí zásad ochrany aplikací

**Které aplikace se dají spravovat pomocí zásad ochrany aplikací?** Zásadami ochrany aplikací Intune se dá spravovat každá aplikace integrovaná sadou [Intune App SDK](/intune/app-sdk) nebo zabalená nástrojem [Intune App Wrapping](/intune/apps-prepare-mobile-application-management). Podívejte se do oficiálního seznamu [aplikací spravovaných přes Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps), který je veřejně přístupný.

**Jaké jsou základní požadavky na používání zásad ochrany aplikací v aplikaci spravované přes Intune?**
- Koncový uživatel musí mít účet Azure Active Directory (AAD). Pokud se chcete dozvědět, jak se vytvářejí uživatelé Intune v Azure Active Directory, přečtěte si [Přidání uživatelů a udělení oprávnění pro správu v Intune](/intune/users-permissions-add).

- Koncový uživatel musí mít ke svému účtu Azure Active Directory přiřazenou licenci pro Microsoft Intune. Informace o tom, jak se přiřazují licence Intune koncovým uživatelům, najdete v článku [Správa licencí Intune](/intune/licenses-assign).

- Koncový uživatel musí patřit do skupiny zabezpečení, která je cílem zásady ochrany aplikace. Stejná zásada ochrany aplikace musí mít za cíl konkrétní používanou aplikaci. Zásady ochrany aplikací se dají vytvářet a nasazovat v konzole Intune na [portálu Azure](http://portal.azure.com). Skupiny zabezpečení se aktuálně dají vytvářet na [portálu Office](http://portal.office.com).

- Koncový uživatel se musí do aplikace přihlásit pomocí svého účtu AAD.

**Jaké jsou další požadavky na používání [mobilní aplikace Outlook](https://products.office.com/outlook)?**

- Koncový uživatel musí mít v zařízení nainstalovanou mobilní aplikaci Outlook.

- Koncový uživatel musí mít poštovní schránku [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) a licenci propojenou se svým účtem Azure Active Directory.

  >[!NOTE]
  > Mobilní aplikace Outlook aktuálně podporuje jenom Microsoft Exchange Online a nepodporuje místní Exchange nebo Exchange v Office 365 Dedicated.

**Jaké jsou další požadavky na používání aplikací [Word, Excel a PowerPoint](https://products.office.com/business/office)?**

- Koncový uživatel musí mít licenci pro [Office 365 Business nebo Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) propojenou se svým účtem Azure Active Directory. Předplatné musí obsahovat aplikace Office na mobilních zařízeních a může obsahovat účet pro ukládání do cloudu přes [OneDrive pro firmy](https://onedrive.live.com/about/business/). Licence na Office 365 se dají přiřadit na [portálu Office](http://portal.office.com) podle těchto [pokynů](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- Koncový uživatel musí mít spravované umístění nakonfigurované pomocí podrobné funkce Uložit jako v nastavení zásad ochrany aplikace Zakázat možnost Uložit jako. Pokud je spravovaným umístěním třeba OneDrive, musí být v aplikaci Word, Excel nebo PowerPoint koncového uživatele nakonfigurovaná aplikace [OneDrive](https://onedrive.live.com/about/).

- Pokud je spravovaným umístěním OneDrive, musí být aplikace cílem pro zásadu ochrany aplikace nasazenou pro koncového uživatele.

  >[!NOTE]
  > Mobilní aplikace Office aktuálně podporují jenom SharePoint Online a ne místní SharePoint.

**Proč je pro Office potřeba spravované umístění (jako OneDrive)?** Intune označuje veškerá data v aplikaci jako podniková (firemní) nebo osobní. Data se považují za podniková, když pocházejí z firemního umístění. U aplikací Office považuje Intune za firemní následující umístění: e-mail (Exchange) nebo cloudové úložiště (aplikace OneDrive s účtem OneDrive pro firmy).

**Jaké jsou další požadavky na používání Skypu pro firmy?** Viz licenční požadavky [Skypu pro firmy](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > Mobilní aplikace Skype pro firmy aktuálně podporuje jenom Online Skype pro firmy.

## <a name="app-protection-features"></a>Funkce ochrany aplikací

**Co je podpora více identit?** Podpora více identit je schopnost sady Intune App SDK použít zásady ochrany aplikací jenom na pracovní nebo školní účet přihlášený k aplikaci. Pokud se k aplikaci přihlásí osobní účet, zůstanou data nedotčená.

**Co je účelem podpory více identit?** Podpora více identit umožňuje, aby se aplikace pro podnikové i běžné zákazníky (tj. aplikace Office) vydávaly veřejně s funkcemi ochrany aplikací Intune pro podnikové účty.

**Jak je na tom aplikace Outlook s více identitami?** Outlook má kombinované zobrazení osobních a podnikových e-mailů, proto při spuštění zobrazí výzvu k zadání PINu Intune.

**Co je PIN aplikace Intune?** Osobní identifikační číslo (PIN) je heslo, kterým se ověřuje, že s daty organizace pracuje v aplikaci správný uživatel.

- **Když je uživatel vyzván k zadání PINu?** Intune vyzve uživatele k zadání PINu aplikace, když se uživatel chystá pracovat s podnikovými daty. V aplikacích s více identitami, jako Word, Excel a PowerPoint, bude uživatel vyzván k zadání PINu při pokusu o otevření podnikového souboru nebo dokumentu. V aplikacích s jednou identitou, například obchodní aplikace spravované přes nástroj Intune App Wrapping, se PIN vyžaduje při spuštění, protože sada Intune App SDK ví, že prostředí uživatele v aplikaci bude vždy podnikové.

- **Jak často se uživateli zobrazí výzva k zadání kódu PIN Intune?**
  Správce IT může v konzole pro správu Intune definovat nastavení zásad ochrany aplikací Překontrolovat požadavky na přístup za (minuty). Toto nastavení určuje dobu, než se v zařízení zkontrolují požadavky na přístup a znovu se zobrazí obrazovka pro kód PIN aplikace. Četnost, s jakou se budou uživateli zobrazovat výzvy, ale ovlivňují důležité detaily týkající se kódu PIN: 

    - **Kvůli větší použitelnosti se kód PIN sdílí mezi aplikacemi stejného vydavatele:** V iOSu se kód PIN jedné aplikace sdílí mezi všemi aplikacemi **stejného vydavatele**. V Androidu se kód PIN jedné aplikace sdílí mezi všemi aplikacemi.
    - **Kolísavost časovače přidruženého ke kódu PIN:** Když po zadání kódu PIN pro přístup k nějaké aplikaci (aplikace A) se tato aplikace v zařízení přestane zobrazovat na popředí (hlavní fokus), vynuluje se časovač tohoto kódu PIN. Jakákoli aplikace (aplikace B), která tento kód PIN sdílí, nevyzve uživatele k jeho zadání, protože časovač se vynuloval. Tato výzva se zobrazí znovu, jakmile je opět splněna hodnota nastavení Překontrolovat požadavky na přístup za (minuty). 

      >[!NOTE] 
      > Kvůli častějšímu ověřování požadavků na přístup uživatele (například výzvy k zadání PINu) doporučujeme zmenšit hodnotu nastavení Překontrolovat požadavky na přístup za (minuty), a to především u často používaných aplikací. 

- **Je PIN bezpečný?** PIN slouží k tomu, aby v aplikaci povolil pracovat s daty organizace jenom správnému uživateli. Proto se koncový uživatel musí přihlásit s pracovním nebo školním účtem, aby si mohl nastavit nebo resetovat PIN pro aplikaci Intune. Toto ověření zpracovává Azure Active Directory prostřednictvím zabezpečené výměny tokenu a sada Intune App SDK do procesu nevidí. Z hlediska zabezpečení je nejlepší ochranou pracovních nebo školních dat jejich šifrování. Šifrování nesouvisí s PINem aplikace, ale jde o vlastní zásadu ochrany aplikace.

- **Jak Intune chrání PIN před útoky hrubou silou?** Jako součást zásady pro PIN aplikace může správce IT nastavit maximální počet pokusů, které uživatel má k ověření PINu před uzamčením aplikace. Po vyčerpání pokusů může sada Intune App SDK vymazat podniková data v aplikaci.
  
- **Proč musím v aplikacích od stejného vydavatele dvakrát zadávat PIN?**
  MAM (v iOSu) aktuálně umožňuje PIN na úrovni aplikace s alfanumerickými a speciálními znaky (nazývaný „heslo“), který vyžaduje zapojení aplikací (jako WXP, Outlook, Managed Browser, Yammer) k integraci sady Intune APP SDK pro iOS. Bez toho se nastavení hesla pro cílové aplikace správně nevynutí. Tato funkce byla vydána v Intune SDK pro iOS verze 7.1.12. <br><br> Aby mohla být tato funkce podporována a byla zajištěna zpětná kompatibilita s předchozími verzemi sady Intune SDK pro iOS, budou se všechny kódy PIN (číselné nebo v podobě hesla) od verze 7.1.12 zpracovávat odděleně od číselných kódů PIN používaných v předchozích verzích SDK. Pokud jsou v zařízení aplikace od stejného vydavatele, které používají sadu Intune SDK pro iOS ve verzích před 7.1.12 A SOUČASNĚ po 7.1.12, bude potřeba nastavit dva kódy PIN. <br><br> Tyto dva kódy PIN (pro každou aplikaci jeden) spolu nijak nesouvisejí, tzn. že musejí vyhovovat zásadám ochrany aplikace platným pro danou aplikaci. Uživatel smí nastavit stejný PIN dvakrát *jen tehdy*, když aplikace A a B používají stejné zásady (platné pro PIN). <br><br> Uvedené chování je specifické pro PIN aplikací pro iOS povolených ve správě mobilních aplikací v Intune. Jak si budou aplikace postupně osvojovat novější verze sady Intune SDK pro iOS, přestane být dvojí nastavování kódu PIN u aplikací od stejného vydavatele takový problém. V následující poznámce uvádíme příklad.

  >[!NOTE]
  > Pokud k vytvoření aplikace A byla použita verze před 7.1.12 a k vytvoření aplikace B od stejného vydavatele byla použita verze vyšší nebo rovna 7.1.12, musí koncový uživatel nastavit PIN zvlášť pro aplikaci A i B, pokud jsou na zařízení s iOSem nainstalované obě aplikace. <br><br> Pokud na toto zařízení nainstalujete aplikaci C se sadou SDK 7.1.9, bude mít stejný PIN jako aplikace A. <br><br> Aplikace D vytvořená s použitím verze 7.1.14 bude mít stejný PIN jako aplikace B. <br><br> Pokud na zařízení nainstalujete jenom aplikace A a C, stačí nastavit jenom jeden PIN. To samé platí, i pokud jsou na zařízení nainstalované aplikace B a D.

**A co šifrování?** Správci IT můžou nasadit zásadu ochrany aplikace, která vyžaduje šifrování dat aplikace. Jako součást této zásady může správce IT také určit, kdy se obsah bude šifrovat.

- **Jak Intune šifruje data?** Podrobné informace o nastavení zásady ochrany aplikace šifrováním najdete v tématech [Nastavení zásad ochrany aplikací pro Android](app-protection-policy-settings-android.md) a [Nastavení zásad ochrany aplikací pro iOS](app-protection-policy-settings-ios.md).

- **Co se šifruje?** Šifrují se jenom data označená jako podniková, a to podle zásady ochrany aplikace správce IT. Data se považují za podniková, když pocházejí z firemního umístění. U aplikací Office považuje Intune za firemní následující umístění: e-mail (Exchange) nebo cloudové úložiště (aplikace OneDrive s účtem OneDrive pro firmy). U obchodních aplikací spravovaných nástrojem Intune App Wrapping se za podniková považují všechna data aplikace.

**Jak může Intune vzdáleně smazat data?** Intune může data aplikace smazat třemi způsoby: úplným vymazáním zařízení, selektivním vymazáním pro MDM nebo selektivním vymazáním pro MAM. Další informace o vzdáleného vymazání pro správu mobilních zařízení (MDM) najdete v článku [Odebrání zařízení pomocí obnovení továrního nastavení nebo odebrání firemních dat](devices-wipe.md#factory-reset). Další informace o selektivním vymazání pomocí MAM najdete v části [Odebrání firemních dat](devices-wipe.md#remove-company-data) a v článku [Jak z aplikací vymazat jenom firemní data](apps-selective-wipe.md).

- **Co je obnovení továrního nastavení?** [Obnovení továrního nastavení](devices-wipe.md) odebere veškerá uživatelská data a nastavení ze **zařízení** pomocí obnovení výchozího továrního nastavení v zařízení. Zařízení se odebere ze služby Intune.
  >[!NOTE]
  > Tovární nastavení se dá obnovit jenom na zařízeních zaregistrovaných ve správě mobilních zařízení (MDM) Intune.

- **Co je selektivní vymazání pro MDM?** V článku [Odebrání zařízení – část Odebrání firemních dat](devices-wipe.md#remove-company-data) najdete informace o odebírání firemních dat.

- **Co je selektivní vymazání pro MAM?** Selektivní vymazání pro MAM jednoduše odebere data aplikace společnosti z aplikace. Žádost se inicializuje pomocí portálu Intune Azure Portal. Informace o zahájení žádosti o vymazání najdete v článku [Jak z aplikací vymazat jenom firemní data](apps-selective-wipe.md).

- **Jak rychle selektivní vymazání pro MAM proběhne?** Pokud uživatel používá aplikaci, když je zahájeno selektivní vymazání, sada Intune App SDK kontroluje každých 30 minut žádost o selektivní vymazání ze služby Intune MAM. Selektivní vymazání také kontroluje tehdy, když uživatel spustí aplikaci poprvé a přihlásí se pomocí pracovního nebo školního účtu.

**Proč místní služby nepracují s aplikacemi chráněnými službou Intune?** Ochrana aplikací Intune závisí na identitě uživatele, aby byla konzistentní mezi aplikací a sadou Intune App SDK. Jediná cesta, která to může zaručit, je moderní ověřování. Jsou situace, kdy aplikace můžou fungovat s místní konfigurací, ale nejsou konzistentní ani nic nezaručují.

**Existuje bezpečný způsob, jak otevírat webové odkazy ze spravovaných aplikací?** Ano. Správce IT může nasadit a nastavit zásadu ochrany aplikace pro [aplikaci Intune Managed Browser](app-configuration-managed-browser.md), což je webový prohlížeč vyvinutý týmem Microsoft Intune, který se dá snadno spravovat přes Intune. Správce IT může vyžadovat, aby se všechny webové odkazy v aplikacích spravovaných přes Intune otvíraly v aplikaci Managed Browser.

## <a name="app-experience-on-android"></a>Prostředí aplikací na Androidu

**Proč je potřeba aplikace Portál společnosti, aby ochrana aplikací Intune fungovala na zařízeních s Androidem?** Většina funkcí ochrany aplikací je integrovaná do aplikace Portál společnosti. I když aplikace Portál společnosti se vždycky vyžaduje, registrace zařízení se _nevyžaduje_. U správy mobilních aplikací bez registrace (MAM-WE) je jenom nutné, aby měl koncový uživatel aplikaci Portál společnosti na zařízení nainstalovanou.

**Jak na Androidu funguje více nastavení přístupu k ochraně aplikací Intune, která jsou nakonfigurovaná na stejnou sadu aplikací a uživatelů?** Zásady ochrany aplikací Intune pro přístup se na zařízení koncových uživatelů, která se pokusí o přístup k cílové aplikaci z firemního účtu, použijí v konkrétním pořadí. Obecně má přednost blokování, pak upozornění, které se dá zavřít. Například pokud se aplikuje na konkrétního uživatele nebo aplikaci, nastavení minimální verze opravy Androidu, které uživatele upozorňuje, aby provedl upgrade opravy, se použije po nastavení minimální verze opravy Androidu, které uživateli zablokuje přístup. Proto ve scénáři, kde správce IT nakonfiguruje minimální verzi opravy Androidu na 2018-03-01 a minimální verzi opravy Androidu (pouze upozornění) na 2018-02-01, zatímco zařízení pokoušející se o přístup k aplikaci má verzi opravy 2018-01-01, by byl koncový uživatel zablokován na základě přísnějšího nastavení pro minimální verzi opravy Androidu, která vede k zablokování přístupu. 

Při zpracování různých typů nastavení by měl přednost požadavek na verzi aplikace. Následoval by požadavek na verzi operačního systému Android a pak požadavek na verzi opravy Androidu. Pak se ve stejném pořadí kontrolují všechna upozornění pro všechny typy nastavení.

## <a name="app-experience-on-ios"></a>Prostředí aplikací v iOS

**Můžu pomocí rozšíření pro sdílení v iOS otevírat pracovní nebo školní data v nespravovaných aplikacích, i když je zásada přenosu dat nastavená na „jenom spravované aplikace“ nebo „žádné aplikace“. Nemůže při tom dojít k úniku dat?** Zásady ochrany aplikací pro Intune nemůžou ovládat rozšíření pro sdílení v iOS, když dané zařízení nespravují. Proto Intune _**podniková data před jejich sdílením mimo příslušnou aplikaci zašifruje**_. Můžete si to ověřit tak, že si zkusíte otevřít podnikový soubor mimo spravovanou aplikaci. Měl by být zašifrovaný a mimo spravovanou aplikaci by ho nemělo být možné otevřít.

**Jak v iOSu funguje více nastavení přístupu k ochraně aplikací Intune, která jsou nakonfigurovaná na stejnou sadu aplikací a uživatelů?** Zásady ochrany aplikací Intune pro přístup se na zařízení koncových uživatelů, která se pokusí o přístup k cílové aplikaci z firemního účtu, použijí v konkrétním pořadí. Obecně má přednost vymazání, pak blokování, a pak upozornění, které se dá zavřít. Například pokud se aplikuje na konkrétního uživatele nebo aplikaci, nastavení minimální verze operačního systému iOS, které uživatele upozorňuje, aby svou verzi iOSu aktualizoval, se použije po nastavení minimální verze operačního systému, které uživateli zablokuje přístup. Proto ve scénáři, kde správce IT nakonfiguruje minimální operační systém iOS na 11.0.0.0 a minimální operační systém iOS (pouze upozornění) na 11.1.0.0, zatímco zařízení pokoušející se o přístup k aplikaci má iOS 10, by byl koncový uživatel zablokován na základě přísnějšího nastavení pro minimální verzi operačního systému iOS, které vede k zablokování přístupu.

Při zpracování různých typů nastavení by měl přednost požadavek na verzi Intune App SDK. Následoval by požadavek na verzi aplikace a pak požadavek na verzi operačního systému iOS. Pak se ve stejném pořadí kontrolují všechna upozornění pro všechny typy nastavení. Doporučujeme nakonfigurovat verzi Intune App SDK jenom po pokynu od produktového týmu Intune pro základní scénáře blokování.

## <a name="see-also"></a>Viz taky
- [Implementace plánu Intune](planning-guide-onboarding.md)
- [Testování a ověřování Intune](planning-guide-test-validation.md)
- [Nastavení zásad správy mobilních aplikací pro Android v Microsoft Intune](app-protection-policy-settings-android.md)
- [Nastavení zásad správy mobilních aplikací pro iOS](app-protection-policy-settings-ios.md)
- [Ověření zásad ochrany aplikací](app-protection-policies-validate.md)
- [Přidání zásad konfigurace aplikací pro spravované aplikace bez registrace zařízení](app-configuration-policies-managed-app.md)
- [Jak získat podporu pro Microsoft Intune](get-support.md)