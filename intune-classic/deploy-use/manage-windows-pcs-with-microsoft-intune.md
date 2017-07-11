---
title: "Správa počítačů pomocí klientského softwaru"
description: "Spravujte počítače s Windows pomocí instalace klientského softwaru Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e217648c744d76d4cde6b8927137cd569b8d0a2e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Správa počítačů s Windows jako počítačů prostřednictvím softwarového klienta Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune poskytuje organizacím ucelené řešení pro správu mobilních zařízení. Pomocí moderních funkcí pro správu zařízení, které jsou součástí operačního systému Windows 10, dokáže Intune spravovat počítače s Windows 10 jako mobilní zařízení. Kvůli splnění potřeb správy vaší organizace dokáže Intune s využitím softwarového klienta Intune spravovat počítače s Windows také jako počítače. Tato metoda správy využívá tradiční funkce pro správu počítačů ve starších operačních systémech Windows.

Softwarový klient Intune je nejvhodnější pro počítače se staršími operačními systémy Windows (například Windows 7), které nelze spravovat jako mobilní zařízení. Ke správě počítačů z cloudu používá softwarový klient Intune funkce správy, jako jsou například Zásady skupiny.

S využitím tohoto softwarového klienta můžete přes Intune spravovat až 7 000 počítačů s Windows jako počítače. V rozsáhlejších nasazeních spravujte počítače s Windows 10 jako mobilní zařízení. Každá verze Intune a aktualizace Windows 10 obsahuje funkce pro správu založené na architektuře pro správu mobilních zařízení. Důrazně proto doporučujeme, aby vaše organizace přešla na systém Windows 10, který se spravuje jako mobilní zařízení.


> [!NOTE]
> Zařízení s Windows 8.1 a novějšími systémy můžete spravovat jako počítače pomocí klientského softwaru Intune, nebo jako mobilní zařízení. Na jednom zařízení nelze použít obě metody. Pečlivě zvažte, než se rozhodnete počítače spravovat pomocí klientského softwaru Intune. Toto téma se týká jenom správy zařízení jako počítačů pomocí klientského softwaru Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Požadavky na správu počítačového klienta Intune

**Hardware**: Minimální požadavky na hardware pro instalaci klientského softwaru Intune:

|Požadavek|Další informace|
|---------------|--------------------|
|Síť|Klient vyžaduje, aby byl počítač připojený k Internetu.|
|Procesor a paměť|Viz požadavky na procesor a paměť RAM pro operační systém počítače.|
|Místo na disku|200 MB volného místa na disku před instalací klientského softwaru.|

**Software**: Požadavky na software pro instalaci klientského softwaru:

|Požadavek|Další informace|
|---------------|--------------------|
|Operační systém | Zařízení s Windows se systémem Windows Vista nebo novějším. </br></br>**Verze Home Edition nejsou podporovány.**|
|Oprávnění správce|Účet, který instaluje klientský software, musí mít oprávnění místního správce pro toto zařízení.|
|Instalační služba systému Windows verze 3.1|Na počítači musí být Instalační služba systému Windows minimálně verze 3.1.<br /><br />Pokud chcete zobrazit verzi Instalační služby systému Windows na počítači:<br /><br />  Na počítači klikněte pravým tlačítkem myši na **%windir%\System32\msiexec.exe** a potom klikněte na **Vlastnosti**.<br /><br />Nejnovější verzi Instalační služby systému Windows můžete stáhnout ze stránky [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) na webu Microsoft Developer Network.|
|Odebrání nekompatibilního klientského softwaru|Před instalací klientského softwaru Intune odinstalujte z počítače tento klientský software: Configuration Manager, Operations Manager, Operations Management Suite a Service Manager.|

## <a name="deploying-the-intune-software-client"></a>Nasazení softwarového klienta Intune
Jako správce Intune můžete softwarového klienta Intune zpřístupnit uživatelům různými způsoby. Pokyny najdete v článku [Instalace softwarového klienta Intune na počítače s Windows](install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Možnosti správy počítačů pomocí klientského softwaru Intune
Ve většině scénářů si svoje zařízení zaregistrujete v Microsoft Intune. Tato služba poskytuje větší sadu funkcí. Ke správě počítačů můžete ale také použít softwarového klienta Intune, který poskytuje následující funkce:

-   **[Správa aktualizací softwaru](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)** – Počítače můžete udržovat stále aktuální a můžete rozhodnout, kdy se mají aktualizace instalovat.

-   **[Zásady brány Windows Firewall](/intune-classic/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** – Tyto zásady pomáhají zajistit, že v žádném počítači používaném ve vaší společnosti není neaktivní nebo nesprávně nakonfigurovaná brána Windows Firewall.

-   **[Ochrana proti malwaru](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)** – Součástí Intune je služba Endpoint Protection, která pomáhá chránit počítače před malwarem.

-   **[Vzdálená pomoc](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** – Intune umožňuje uživatelům kontaktovat pracovníky technické podpory, kteří jim pak můžou pomoct prostřednictvím funkce vzdálené plochy, která je součástí Intune (vyžaduje software TeamViewer).

-   **[Správa licencí na software](/intune-classic/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** – Můžete sledovat, kolik licencí softwaru je dostupných a kolik z nich se právě používá.
-   **[Nasazení aplikací](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** – Do počítačů, které spravujete, můžete nasadit software. Pokud ke správě počítačů použijete softwarového klienta, některé funkce správy nejsou dostupné.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Zásady a nasazení aplikace pro klientský software Intune

I když klientský software Intune podporuje [možnosti správy, které pomáhají chránit počítače](policies-to-protect-windows-pcs-in-microsoft-intune.md) pomocí správy aktualizací softwaru, brány Windows Firewall a služby Endpoint Protection, nemůžou být na počítače spravované pomocí klientského softwaru Intune zacílené jiné zásady Intune, včetně nastavení zásad **Windows**, která jsou specifická pro správu mobilních zařízení.

Pokud ke správě počítačů s Windows používáte klientský software Intune, můžete používat jenom zásady, které jsou uvedené v části **Správa počítače**.

Intune spravuje počítače s Windows pomocí zásad, podobně jako to dělají objekty zásad skupiny (GPO) služby AD DS (Active Directory Domain Services) Windows Serveru. Pokud počítače připojené k doméně Active Directory spravujete pomocí Intune, [zajistěte, aby zásady Intune nekolidovaly s jinými objekty zásad skupiny](/intune-classic/deploy-use/resolve-gpo-and-microsoft-intune-policy-conflicts) používanými ve vaší organizaci. Další informace najdete v článku [Zásady skupiny pro začátečníky](https://technet.microsoft.com/library/hh147307.aspx).

  ![Výběr šablony pro nové zásady počítačů PC se systémem Windows](../media/select-template-for-pc-policy.png)

K nasazování aplikací můžete použít pouze Instalační službu systému Windows (.exe, .msi).

  ![Výběr platformy a umístění softwarových souborů klientského počítače](../media/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Běžné úlohy pro počítače s Windows

Konzolu správce Intune můžete použít k dalším běžným úlohám správy u počítačů s Windows s nainstalovaným klientem:
- [Zjednodušení správy počítačů pomocí zásad](use-policies-to-simplify-windows-pc-management.md) –Popisuje zásady **Správa počítače** v Intune a uvádí nastavení pro Microsoft Intune Center.

- [Zobrazení inventáře hardwaru a softwaru u počítačů s Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) – Vysvětluje, jak vytvořit sestavu s informacemi o hardwarových možnostech počítačů a o softwaru, který je na nich nainstalovaný. Vysvětluje také, jak obnovit inventář počítačů tak, aby byl aktuální.
- [Vyřazení počítače s Windows](retire-a-windows-pc-with-microsoft-intune.md) – Uvádí postup, jak vyřadit počítač s Windows, a popisuje, co se stane při vyřazení počítače.
- [Správa propojení uživatelů se zařízeními u počítačů s Windows](manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) – Vysvětluje, kdy a jak je nutné propojit uživatele s počítačem před nasazením softwaru uživateli.
- [Vyžádání a poskytnutí vzdálené pomoci na počítačích s Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) – Vysvětluje, jak můžete uživatelům počítačů s Intune poskytnout vzdálenou pomoc, a popisuje požadavky a instalaci softwaru TeamViewer.

Další informace o výše uvedených úkolech najdete v části, která se týká [běžných úloh správy počítače](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Omezení správy klientského softwaru Intune

Některé možnosti správy, které je možné použít ke správě počítačů PC jako mobilních zařízení, není možné použít u počítačů PC, které se spravují pomocí klientského softwaru Intune:

-   Úplné vymazání (selektivní vymazání je k dispozici)
-   podmíněný přístup

Uvědomte si také, že v konzole správce Intune se některé části, jako například **Aktualizace**, **Ochrana** a **Licence**, zobrazí jen v případě, že jsou vaše zařízení zaregistrovaná pomocí klientského softwaru Intune.

  ![Položky konzoly správce, které se zobrazují pouze pro počítačového klienta](../media/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Pomoc s odstraňováním problémů

Klientský software Intune obvykle běží tiše na pozadí a nevyžaduje skoro žádnou interakci ze strany uživatele ani řešení potíží. Pokud potřebujete vyřešit problémy týkající se správy počítačů PC, můžete si projít informace v protokolech. Klientský software Intune a odpovídající protokoly jsou nainstalované v adresáři %Program Files%\Microsoft\OnlineManagement.

Můžete si také projít informace v článku [Řešení potíží s instalací klientů v Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-client-setup-in-microsoft-intune), kde zjistíte, k jakým problémům by mohlo dojít a jaká (alternativní) řešení je možné použít.