---
title: Sestava šifrování pro zašifrovaná zařízení v Microsoft Intune
titleSuffix: Microsoft Intune
description: Zobrazte si sestavu o stavu šifrování zařízení s iOS nebo Windows a získejte přístup k trezoru a klíčům obnovení BitLockeru z portálu Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4d53179ed43697769ec7142ace6b62c08a67f31a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502345"
---
# <a name="monitor-device-encryption-with-intune"></a>Monitorování šifrování zařízení pomocí Intune   

Sestava Microsoft Intuneho šifrování je centralizované umístění pro zobrazení podrobností o stavu šifrování zařízení a možnosti hledání pro správu klíčů pro obnovení zařízení. Možnosti obnovovacího klíče, které jsou k dispozici, závisí na typu zařízení, které si prohlížíte.  

Pokud chcete sestavu najít, přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) a pokračujte na **Konfigurace zařízení**a potom v části *monitorování*vyberte **Sestava šifrování**.  

## <a name="view-encryption-details"></a>Zobrazit podrobnosti o šifrování  

Sestava šifrování zobrazuje společné podrobnosti napříč podporovanými zařízeními, která spravujete. Následující části obsahují podrobné informace o informacích, které Intune prezentuje v sestavě.  
 
### <a name="prerequisites"></a>Požadavky:  

Sestava šifrování podporuje vytváření sestav na zařízeních, na kterých běží následující verze operačního systému:  
- macOS 10,13 nebo novější  
- Windows verze 1607 nebo novější  

### <a name="report-details"></a>Podrobnosti sestavy  

Podokno sestava šifrování zobrazuje seznam zařízení, která spravujete, s podrobnými podrobnostmi o těchto zařízeních. Můžete vybrat zařízení ze seznamu a přejít k němu a zobrazit další podrobnosti v podokně [stav šifrování zařízení](#device-encryption-status) zařízení.  

- **Název zařízení** – název zařízení.  
- **OS** – platforma zařízení, například Windows nebo MacOS.  
- **Verze operačního systému** – verze Windows nebo MacOS na zařízení.  
- **Verze TPM** *(platí jenom pro Windows 10)* – verze čipu TPM (Trusted Platform Module) na zařízení s Windows 10.  
- **Připravenost na šifrování** – vyhodnocení připravenosti na zařízení pro podporu vhodné šifrovací technologie, jako je například BitLocker nebo šifrování trezoru. Zařízení jsou označena jako:  
  - **Připraveno**: zařízení se dá zašifrovat pomocí zásad MDM, což vyžaduje, aby zařízení splňovalo následující požadavky:  
    
    **Pro zařízení MacOS**:  
    - MacOS verze 10,13 nebo novější  
    
    **Pro zařízení s Windows 10**:  
    - Verze 1703 nebo novější, *obchodní*, *podnikové*, *vzdělávací*nebo verze 1809 nebo novější *pro*  
    - Zařízení musí mít čip TPM.  
    
    Další informace najdete v dokumentaci k Windows v dokumentaci k [poskytovateli služby BitLocker Configuration Service Provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) .  

  - **Nepřipraveno**: zařízení nemá úplné možnosti šifrování, ale pořád podporuje šifrování. Například zařízení s Windows může být zašifrováno ručně uživatelem nebo prostřednictvím Zásady skupiny, které lze nastavit tak, aby povolovalo šifrování bez čipu TPM.
  - **Nelze použít**: pro klasifikaci tohoto zařízení není k dispozici dostatek informací.  

- **Stav šifrování** – určuje, jestli je jednotka operačního systému zašifrovaná.  

- **Hlavní název uživatele** – primární uživatel zařízení.  

### <a name="device-encryption-status"></a>Stav šifrování zařízení  

Když vyberete zařízení ze sestavy šifrování, Intune zobrazí podokno **stav šifrování zařízení** . V tomto podokně jsou k dispozici následující podrobnosti:  

- **Název zařízení** – název zařízení, které si prohlížíte.  

- **Připravenost na šifrování** – vyhodnocení připravenosti na zařízení pro podporu šifrování prostřednictvím zásad MDM.  
  
  Příklad: Pokud má zařízení s Windows 10 připravenosti *Nepřipraveno*, může i nadále podporovat šifrování. Aby bylo možné označení *připravit* , musí mít zařízení s Windows 10 čip TPM. Čipy TPM nejsou nutné k podpoře šifrování. (Další informace najdete v tématu *připravenost na šifrování* v předchozí části.)  

- **Stav šifrování** – určuje, jestli je jednotka operačního systému zašifrovaná. Může trvat až 24 hodin, než Intune nahlásí stav šifrování zařízení nebo změní stav. Tato doba zahrnuje dobu, po kterou má operační systém zašifrování, a čas, kdy se má zařízení nahlásit zpátky do Intune.  

  Pokud chcete zrychlit hlášení stavu šifrování trezoru služby, než se zařízení normálně objevuje, uživatelé budou po dokončení šifrování synchronizovat svá zařízení.  

- **Profily** – seznam profilů *Konfigurace zařízení* , které se vztahují k tomuto zařízení a jsou nakonfigurované s následujícími hodnotami:  

  - MacOS
    - Typ profilu = *Endpoint Protection*  
    - Nastavení > trezoru úložiště > trezor = *Enable*

  - Windows 10:
    - Typ profilu = *Endpoint Protection*  
    - Nastavení > šifrování Windows > šifrovat zařízení = *vyžadovat*  

  Seznam profilů můžete použít k identifikaci jednotlivých zásad pro kontrolu, aby *souhrn stavu profilu* označoval problémy.  

- **Shrnutí stavu profilu** – souhrn profilů, které se vztahují k tomuto zařízení. Souhrn představuje nejmenší příznivou podmínku v rámci platných profilů. Pokud například výsledkem pouze jednoho z několika použitelných profilů je chyba, zobrazí se v *souhrnu stavu profilu* *Chyba*.  
  
  Pokud chcete zobrazit podrobnosti o stavu, přečtěte si v **Intune** > **Konfigurace zařízení** > **profily**a vyberte profil. Volitelně můžete vybrat možnost **stav zařízení** a pak vybrat zařízení.  

- **Podrobnosti o stavu** – rozšířené informace o stavu šifrování zařízení.  

  > [!IMPORTANT]  
  > V případě zařízení s Windows 10 Intune zobrazí *Podrobnosti o stavu* jenom pro zařízení s *Windows 10 duben 2019 Update* nebo novějším.  
  
  V tomto poli se zobrazují informace o každé příslušné chybě, kterou je možné zjistit. Pomocí těchto informací můžete pochopit, proč nemusí být zařízení připravené k šifrování.  

  Následují příklady podrobností o stavu, které může Intune hlásit:  
  
  **MacOS**:
  - Obnovovací klíč nebyl dosud načten a uložen. Pravděpodobně zařízení není odemknuté nebo nebylo vráceno se změnami.  
 
    *Vezměte v úvahu: Tento výsledek nemusí nutně představovat chybový stav, ale dočasný stav, který může být z důvodu časování na zařízení, kde v úschově pro obnovovací klíče musí být nastavené před odesláním požadavku na šifrování do zařízení. Tento stav může také indikovat, že zařízení zůstává uzamčené nebo se v nedávné době nevrátilo s Intune. Vzhledem k tomu, že šifrování trezoru se nespustí, dokud není zařízení zapojené do elektrické sítě (zpoplatněné), může uživatel obdržet obnovovací klíč pro zařízení, které ještě není zašifrované*.  

  - Uživatel odvozuje šifrování nebo právě probíhá šifrování.  
 
    *Vezměte v úvahu: uživatel se ještě odhlásil po přijetí požadavku na šifrování, který je nutný k tomu, aby mohl trezor zařízení zašifrovat zařízení, nebo jestli uživatel zařízení ručně dešifroval. Intune nemůže zabránit uživateli v dešifrování svého zařízení.*  

  - Zařízení je už zašifrované. Aby bylo možné pokračovat, musí uživatel zařízení zařízení dešifrovat.  
 
    *Vezměte v úvahu: Intune nemůže na zařízení, které je už zašifrované, nastavit trezor. Místo toho musí uživatel ručně dešifrovat svoje zařízení, aby ho bylo možné spravovat pomocí zásad konfigurace zařízení a Intune*. 
 
  - Trezor úložiště potřebuje, aby uživatel schválil svůj profil pro správu v MacOS Catalina a vyšších.  
 
    *Zvažte: počínaje verzí MacOS 10,15 (Catalina) může nastavení registrace schválená uživatelem způsobit požadavek, aby uživatelé ručně schválili šifrování trezoru. Další informace najdete v dokumentaci k [registraci schválené uživatelem](../enrollment/macos-enroll.md) v dokumentaci k Intune*.  

  - Neznámý.  

    *Vezměte v úvahu: možnou příčinou neznámého stavu je to, že zařízení je uzamčené a Intune nemůže spustit v úschově nebo proces šifrování. Po odemknutí zařízení může pokračovat průběh*.  

  **Windows 10**:  
  - Zásada BitLockeru vyžaduje souhlas uživatele, aby mohl spustit Průvodce nástroj BitLocker Drive Encryption pro spuštění šifrování svazku s operačním systémem, ale uživatel nesouhlasí.  
  
  - Metoda šifrování svazku operačního systému neodpovídá zásadám BitLockeru.  
  
  - Zásada BitLockeru pro ochranu svazku operačního systému vyžaduje ochranu čipem TPM, ale čip TPM se nepoužívá.  
  
  - Zásady BitLockeru vyžadují pro svazek operačního systému ochranu jenom čipem TPM, ale ochrana TPM se nepoužívá.  
  
  - Zásady BitLockeru vyžadují ochranu pomocí TPM a PIN kódu pro svazek operačního systému, ale ochrana pomocí čipu TPM a PIN kódu se nepoužívá.  
  
  - Zásady BitLockeru vyžadují ochranu pomocí čipu TPM a spouštěcího klíče pro svazek operačního systému, ale ochrana pomocí čipu TPM a spouštěcího klíče se nepoužívá.  
  
  - Zásady BitLockeru vyžadují pro svazek s operačním systémem ochranu pomocí čipu TPM + PIN a spouštěcího klíče, ale nepoužije se ochrana pomocí čipu TPM + PIN a spouštěcího klíče.  
  
  - Svazek s operačním systémem není chráněn.  
  
  - Nepovedlo se zálohovat klíč obnovení.  
  
  - Pevná jednotka není chráněná.  
  
  - Metoda šifrování pevné jednotky neodpovídá zásadám BitLockeru.  
  
  - Pro šifrování jednotek vyžaduje zásada BitLockeru, aby se uživatel přihlásil jako správce, nebo pokud je zařízení připojené ke službě Azure AD, musí být zásada AllowStandardUserEncryption nastavená na hodnotu 1.  
  
  - Prostředí Windows Recovery Environment (WinRE) není nakonfigurováno.  
  
  - ČIP TPM není k dispozici pro BitLocker, protože není k dispozici, je v registru nedostupný, nebo je operační systém na vyměnitelném disku.  
  
  - ČIP TPM není připravený na BitLocker.  
  
  - Síť není k dispozici, což je vyžadováno pro zálohování klíče obnovení.  

## <a name="export-report-details"></a>Exportovat podrobnosti sestavy 
Při prohlížení podokna sestavy šifrování můžete vybrat **exportovat** a vytvořit soubor *. csv* stažení podrobností sestavy.  Tato sestava obsahuje podrobné informace o podrobnostech z podokna *sestavy šifrování* a podrobností o *stavu šifrování zařízení* pro každé zařízení, které spravujete.   
 
  
![Exportovat podrobnosti](./media/encryption-monitor/export.png) 
 
Tato sestava může být používána při identifikaci problémů pro skupiny zařízení. Můžete například použít sestavu k identifikaci seznamu zařízení macOS, která *je už povolená uživatelem*, což znamená, že zařízení, která se musí ručně dešifrovat, než může Intune spravovat jeho nastavení trezoru.  
 
## <a name="filevault-recovery-keys"></a>Klíče obnovení trezoru úložišť   
Když Intune nejdřív zašifruje zařízení macOS s trezorem, vytvoří se osobní obnovovací klíč. Po zašifrování zařízení zobrazí pro koncového uživatele Tento osobní klíč jednou.  
 
U spravovaných zařízení může Intune v úschově kopii osobního obnovovacího klíče. V úschově klíčů umožňuje správcům Intune otáčet klíče, aby lépe chránily zařízení a uživatelé obnovili ztracený nebo otočený osobní obnovovací klíč.  
 
Intune podporuje několik možností, jak můžete otáčet a obnovovat osobní klíče pro obnovení. Jedním z důvodů, jak klíč otočit, je, že aktuální osobní klíč je ztracený nebo je pravděpodobně ohrožen.  
 
> [!IMPORTANT]  
>  Zařízení, která jsou zašifrovaná uživateli, a ne Intune, se nedají spravovat přes Intune. To znamená, že Intune nemůže v úschově osobní obnovení těchto zařízení ani spravovat rotaci obnovovacího klíče.  Aby mohla Intune spravovat trezory a obnovovací klíče pro zařízení, musí si uživatel dešifrovat svoje zařízení a pak nechat Intune šifrování zařízení.  

### <a name="rotate-recovery-keys"></a>Otočení obnovovacích klíčů  

- **Automatické otočení**: jako správce můžete nakonfigurovat nastavení trezoru klíčů pro automatické vygenerování nového klíče pro obnovení.  Když se pro zařízení vygeneruje nový klíč, klíč se uživateli nezobrazí. Místo toho musí uživatel získat klíč buď od správce, nebo pomocí aplikace Portál společnosti.  

- **Ruční rotace**: jako správce můžete zobrazit informace o zařízení, které spravujete v Intune a které je zašifrované pomocí trezoru. Pak můžete zvolit ruční otočení obnovovacího klíče pro podniková zařízení. Obnovovací klíče pro osobní zařízení nemůžete otočit.  

  Otočení obnovovacího klíče: 
  1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), klikněte na **zařízení** and a potom v části Spravovat vyberte **všechna zařízení**.  
  2. V seznamu zařízení vyberte zařízení, které je šifrované a pro které chcete otočit jeho klíč. Pak v části monitorování vyberte **klíče pro obnovení**.  
  3. V podokně klíče pro obnovení vyberte **otočit obnovovací klíč trezoru**.  
  
     Až se zařízení příště vrátí se službou Intune, osobní klíč se otočí. V případě potřeby může koncový uživatel získat nový klíč prostřednictvím portálu společnosti. 


### <a name="recover-recovery-keys"></a>Obnovit obnovovací klíče  
- **Správce**: Správci nemohou zobrazit osobní klíče pro obnovení pro zařízení, která jsou zašifrovaná pomocí trezoru služby.  

- **Koncový uživatel**: koncoví uživatelé používají portál společnosti web z libovolného zařízení k zobrazení aktuálního osobního obnovovacího klíče pro kterékoli ze svých spravovaných zařízení. Nemůžete zobrazit obnovovací klíče z aplikace Portál společnosti.  

 
  Postup zobrazení obnovovacího klíče:  
  1. Přihlaste se k webu *portál společnosti Intune* z libovolného zařízení.  
  2. Na portálu klikněte na **zařízení** a vyberte zařízení MacOS, které je šifrované pomocí trezoru.  
  3. Vyberte **získat obnovovací klíč**. Zobrazí se aktuální obnovovací klíč.  
 

## <a name="bitlocker-recovery-keys"></a>Obnovovací klíče nástroje BitLocker  

Intune poskytuje přístup k oknu Azure AD pro BitLocker, takže můžete na portálu Intune zobrazit ID klíčů a obnovovací klíče BitLockeru pro zařízení s Windows 10.  Aby bylo možné získat přístup k zařízení, musí mít uloží klíče ke službě Azure AD. 
1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), klikněte na **zařízení** a potom v části *Spravovat*vyberte **všechna zařízení**.  

2. V seznamu vyberte zařízení a potom v části *monitorování*vyberte **klíče pro obnovení**.  
  
Pokud jsou ve službě Azure AD k dispozici klíče, jsou k dispozici tyto informace:
- ID klíče BitLockeru  
- Obnovovací klíč nástroje BitLocker  
- Typ jednotky  

Pokud klíče nejsou v Azure AD, zobrazí se v Intune *pro toto zařízení nenašel žádný klíč BitLockeru*.  

Informace pro BitLocker se získávají pomocí [poskytovatele služby BitLocker Configuration Service Provider](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP). CSP nástroje BitLocker podporuje Windows 10 verze 1703 a novější a pro Windows 10 pro verze 1809 a novější.  

## <a name="next-steps"></a>Další kroky  

Vytvořte zásady [dodržování předpisů pro zařízení](compliance-policy-create-windows.md) .