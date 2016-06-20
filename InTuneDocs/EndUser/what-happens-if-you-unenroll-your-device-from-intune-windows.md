---
# required metadata

title: Co se stane, když zrušíte registraci zařízení v Intune? | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Co se stane, když zrušíte registraci zařízení v Intune?

Když odinstalujete aplikaci Portál společnosti ze svého zařízení, zruší se také jeho registrace v Intune. Další informace najdete pomocí odkazu v části V tomto článku, který odpovídá použitému zařízení.

- [Windows 10 Mobile, 8.1, Windows 8, Windows 7, Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10, Windows 8.1 nebo Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [Windows RT se systémem Windows 8.1 nebo Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10, Windows 8.1, Windows 8, Windows 7, Vista

-   Vaše zařízení se už nebude zobrazovat na portálu společnosti a z tohoto portálu už nebudete moct instalovat aplikace.

-   Pokud jste nainstalovali klientský software Intune, bude z počítače odebrán.

-   Z počítače se odebere software Intune Endpoint Protection. Pokud je v počítači nainstalovaný jiný software antivirové ochrany a je zakázaný, může být po odebrání softwaru Intune Endpoint Protection znovu povolený. Po odebrání z portálu společnosti byste měli počítač zkontrolovat.

    > [!IMPORTANT] Pokud tento jiný software antivirové ochrany nebude znovu povolený a není nainstalovaný žádný jiný software antivirové ochrany, může být počítač od daného okamžiku ohrožen a zvýší se tím riziko napadení viry a malwarem.

-   Už nebudou platit nastavení, která se v zařízení změnila od jeho přidání (třeba zakázání fotoaparátu/kamery).

-   Počítač se už nebude automaticky aktualizovat prostřednictvím aktualizací softwaru nebo antivirového programu ze služby Intune. V závislosti na tom, jak je počítač nakonfigurován, však může počítač nadále získávat aktualizace prostřednictvím služeb Windows Server Update Services, Windows Update či Microsoft Update.

Kromě toho pro Windows 8.1 platí:

-   Nebudete již moci v zařízení používat aplikace a data společnosti.

-   Některé e-mailové aplikace, například Windows Pošta, nebudou mít přístup k e-mailům společnosti, které jsou uloženy v zařízení.

-   Je možné, že se nebudete schopni připojit k podnikové síti pomocí sítě Wi-Fi nebo virtuální privátní sítě (VPN).

-   Je možné, že již v zařízení nebudete mít přístup k některým prostředkům společnosti, jako jsou sdílené složky nebo interní weby.

## Windows 10 Mobile, Windows Phone 8.1 nebo Windows Phone 8

-   Ze zařízení se odinstaluje aplikace Portál společnosti. To znamená, že už se vaše zařízení nebude zobrazovat na portálu společnosti a nebudete moct instalovat aplikace z aplikace nebo webu Portál společnosti.

-   Nebudete již moci v zařízení používat aplikace a data společnosti.

-   Nastavení, která byla v zařízení změněna od jeho přidání, například zakázání fotoaparátu/kamery nebo vyžadování určité délky hesla, již nebudou platit.

    > [!IMPORTANT]
    > Jedinou výjimkou jsou zde zásady šifrování, které budou platit stále. Pokud zásady vaší společnosti vyžadovaly, aby byl váš Windows Phone zašifrovaný, jde v telefonu šifrování zrušit jedině obnovením telefonu do výchozího továrního nastavení pomocí nabídky **Nastavení** ve Windows Phonu.

## Windows RT se systémem Windows 8.1 nebo Windows RT

-   Ze zařízení se odinstaluje aplikace Portál společnosti. To znamená, že už se vaše zařízení nebude zobrazovat na portálu společnosti a nebudete z něj moct instalovat aplikace.

-   Nebudete již moci v zařízení používat aplikace a data společnosti.

-   Nastavení, která byla v zařízení změněna od jeho přidání, například zakázání fotoaparátu/kamery nebo vyžadování určité délky hesla, již nebudou platit.

-   Je možné, že se již nebudete schopni připojit k podnikové síti pomocí sítě Wi-Fi nebo virtuální privátní sítě (VPN).

-   Je možné, že již v zařízení nebudete mít přístup k některým prostředkům společnosti, jako jsou sdílené složky nebo interní weby.

-   Některé e-mailové aplikace, například Windows Pošta, nebudou mít přístup k e-mailům společnosti, které jsou uloženy v zařízení.

Při odebrání zařízení se systémem Windows RT dojde k následujícímu:

-   Ze zařízení se odinstaluje aplikace Portál společnosti. To znamená, že už se vaše zařízení nebude zobrazovat na portálu společnosti a nebudete z něj moct instalovat aplikace.

-   Nebudete již moci v zařízení používat aplikace a data společnosti.

-   Nastavení, která byla v zařízení změněna od jeho přidání, například zakázání fotoaparátu/kamery nebo vyžadování určité délky hesla, již nebudou platit.


### Související témata
[Použití zařízení Windows s Intune](using-your-windows-device-with-intune.md)

<!--HONumber=May16_HO3-->

