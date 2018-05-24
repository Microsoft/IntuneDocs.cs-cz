---
title: Automatická registrace zařízení s Androidem pomocí technologie Knox Mobile Enrollment od Samsungu
titlesuffix: Microsoft Intune
description: Přečtěte si, jak zaregistrovat zařízení s Androidem pomocí Samsung KME.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88cb733c688019b2fc5455a0184e968d91e77806
ms.sourcegitcommit: b0ad42fe5b5627e5555b2f9e5bb81bb44dbff078
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/09/2018
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Automatická registrace zařízení s Androidem pomocí technologie Knox Mobile Enrollment od Samsungu

Toto téma vám pomůže s nastavením Intune pro registraci podporovaných zařízení s Androidem pomocí technologie Samsung Knox Mobile Enrollment (KME). Když použijete Intune se Samsung KME, můžete zaregistrovat velké počty zařízení s Androidem vlastněných společností při jejich prvním zapnutí koncovými uživateli a jejich připojení k síti Wi-Fi nebo mobilní síti. Zařízení se také dají zaregistrovat pomocí Bluetooth nebo NFC, když použijete aplikaci Knox Deployment App.

Pokud chcete povolit registraci Intune pomocí Samsung KME, použijte oba portály Intune i Samsung Knox v tomto pořadí:

1. Na portálu Knox:
    1. [Vytvoření profilu MDM](#create-mdm-profile)
    2. [Přidání zařízení](#add-devices)
    3. [Přiřazení profilu MDM zařízení](#assign-an-mdm-profile-to-devices)
2. Na portálu Azure Portal [identifikujte zařízení jako vlastněná společností](#identify-devices-as-corporate-owned).
3. Na portálu Knox [nakonfigurujte přihlášení koncového uživatele](#configure-how-end-users-sign-in).
4. [Distribuujte zařízení](#distribute-devices).


Seznam identifikátorů zařízení (sériová čísla a čísla IMEI) se při nákupu zařízení od autorizovaných prodejců, kteří se účastní programu Knox Deployment Program, automaticky přidá na portál Knox.


## <a name="prerequisites"></a>Požadavky

Pokud chcete provést registraci do Intune pomocí KME, musíte nejprve zaregistrovat vaši společnost na portálu Samsung Knox pomocí tohoto postupu:
1.  [Ujistěte se, že je technologie KME dostupná ve vaší oblasti](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): Technologie KME je dostupná ve více než 55 zemích. Ujistěte se, že se podporuje vaše země nasazení.

2.  [Podporovaná zařízení](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): Technologie KME je k dispozici na všech zařízeních Samsung s verzí Knox 2.4 a vyšší.

3.  [Požadavky sítě](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Ujistěte se, že jsou ve vaší síti povolena nezbytná pravidla firewallu a přístupu k síti.

4.  [Registrace účtu Samsung](https://www2.samsungknox.com/en/user/register): K registraci a povolení KME a správě veškerých oprávnění Knox Enterprise na jednom místě se vyžaduje účet Samsung.

5.  Kontrola registrace: Jakmile se váš profil dokončí a odešle, provede Samsung kontrolu vaší žádosti a buď ji okamžitě schválí, nebo ji převede do stavu čekání na kontrolu pro další zpracování. Po schválení účtu můžete pokračovat dalšími kroky.

## <a name="create-mdm-profile"></a>Vytvoření profilu MDM

Když se vaše společnost úspěšně zaregistruje, můžete na portálu Knox pomocí níže uvedených informací vytvořit profil MDM pro Microsoft Intune. Podrobné pokyny najdete v článku [Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) (Průvodce nastavením profilu Samsung Knox).

| Pole profilu MDM| Požadováno? | Hodnoty |
|-------------------|-----------|-------|
|MDM Server URI (URI serveru MDM)     | Ne        |Nechte prázdné.
|Profile Name (Název profilu)       | Ano       |Zadejte libovolný název profilu.
|description        | Ne        |Zadejte text popisující profil.
|MDM Agent APK (APK Agent MDM)      | Ano       |https://aka.ms/intune_kme
|Skip Setup wizard (Přeskočit průvodce nastavením)  | Ne        |Tuto možnost vyberte, pokud chcete přeskočit standardní výzvy k nastavení zařízení jménem koncového uživatele.
|Allow End User to Cancel Enrollment (Povolit koncovému uživateli zrušit registraci) | Ne | Tuto možnost vyberte, pokud chcete uživatelům povolit, aby zrušili KME.
|Custom JSON (Vlastní JSON)        | Ne        |Nechte prázdné.
| EULAs, Terms of Service & User Agreements (Smlouvy EULA, podmínky služby a smlouvy s uživateli)| Ne | Tuto možnost vyberte, pokud chcete zobrazit smlouvy související s platformou Knox vyžadující přijetí uživatelem.
Associate a Knox license with this profile (Přiřadit tomuto profilu licenci Knox) | Ne | Tuto možnost nechejte nezvolenou. Registrace do Intune pomocí KME nevyžaduje licenci Knox.

## <a name="add-devices"></a>Přidání zařízení

Abyste mohli zařízením přiřadit profily MDM, musí být na portál Knox přidána podporovaná zařízení Samsung Knox pomocí jedné z následujících metod:
- **Prostřednictvím prodejců schválených společností Samsung:** Tuto metodu použijte, pokud nakupujete zařízení od některého z prodejců schválených společností Samsung. Prodejci za vás mohou po schválení automaticky odesílat zařízení. [Pokud chcete zjistit, jak přidat prodejce, přečtěte si uživatelskou příručku pro registraci Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Prostřednictvím aplikace Knox Deployment App (KDA):** Tuto metodu použijte, pokud máte stávající zařízení, která je potřeba zaregistrovat pomocí KME. Pro přidání zařízení na portál Knox můžete pomocí této metody použít Bluetooth nebo NFC. [Informace o použití aplikace KDA najdete v uživatelské příručce pro registraci Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Přiřazení profilu MDM k zařízením
Přidaným zařízením na portálu Knox musíte přiřadit profil MDM dříve, než budou moct být zaregistrována. [Informace o konfiguraci zařízení najdete v uživatelské příručce pro registraci Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="identify-devices-as-corporate-owned"></a>Identifikace zařízení jako vlastněných společností
Zařízení zaregistrovaná pomocí KME můžete identifikovat jako zařízení vlastněná společností. Je to potřeba provést před registrací zařízení. Umožní vám to provádět další úlohy správy a sbírat další informace, třeba celé telefonní číslo a inventář aplikací.

Použijte tento postup k identifikaci zařízení jako vlastněných společností:

1. Seznam zařízení z portálu Knox exportujte jako soubor CSV.

2. Soubor CSV naformátujte pomocí čísla IMEI nebo sériového čísla, jak je popsáno [zde](https://docs.microsoft.com/en-us/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number).

3. Na portálu Azure Portal nahrajte soubor CSV do **Registrace zařízení** > **Identifikátory podnikových zařízení** > **Přidat**.

Nyní se identifikovaná zařízení, která se zaregistrují, označí jako vlastněná společností.

> [!NOTE]
>Intune automaticky přiřadí zařízením zaregistrovaným s účtem [Správce registrace zařízení](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll) stav, který označuje, že jsou ve vlastnictví společnosti.

## <a name="configure-how-end-users-sign-in"></a>Konfigurace způsobu přihlašování koncových uživatelů

Pro zařízení zaregistrovaná v Intune pomocí KME můžete pomocí následujícího postupu nakonfigurovat způsob, jakým se přihlašuje koncový uživatel:

- **Bez přiřazení uživatelského jména:** Na portálu Knox v části **Device details** (Podrobnosti zařízení) nechejte pole **User ID** (ID uživatele) a **Password** (Heslo) pro přidaná zařízená prázdná. Je nutné, aby koncový uživatel zadal při registraci do Intune uživatelské jméno i heslo.

- **S přiřazením uživatelského jména:** Na portálu Knox v části **Device details** (Podrobnosti zařízení) zadejte **User ID** (ID uživatele) (například uživatelské jméno přiřazeného uživatele nebo účet [Správce registrace zařízení](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)) pro přidaná zařízení. Tento způsob předem vyplní uživatelské jméno a vyžaduje, aby koncový uživatel při registraci do Intune zadal heslo.

> [!NOTE]
>
>Jakmile je nadefinováno přiřazení uživatele, může zařízení pomocí KME zaregistrovat pouze přiřazený uživatel. Platí to i po obnovení zařízení do továrního nastavení. Pokud na portálu Knox není nadefinováno žádné přiřazení uživatele, může zařízení pomocí KME zaregistrovat jakýkoli uživatel s platnou licencí Intune.
>

## <a name="distribute-devices"></a>Distribuujte zařízení.

Jakmile vytvoříte a přiřadíte profil MDM, přiřadíte uživatelské jméno a identifikujete zařízení v Intune jako vlastněná společností, můžete zařízení distribuovat uživatelům.

Potřebujete ještě další pomoc? Podívejte se na celou [uživatelskou příručku pro KME](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
- **Účet Google Play:** Účet Google Play není pro registraci zařízení do Microsoft Intune nezbytný. Budoucí aktualizace aplikace Portál společnosti Intune mohou účet Google Play na zařízení vyžadovat.

- **Režim vlastníka zařízení Google:** Registrace v režimu vlastníka zařízení Google prostřednictvím KME se v této verzi Preview nepodporuje. V současné době tento scénář prozkoumáváme.

- **Pole Password (Heslo) se ignoruje:** Pokud je pole s **heslem** v části **Device details** (Podrobnosti zařízení) na portálu Knox vyplněno, bude ho aplikace Portál společnosti Inture ignorovat. Aby se registrace zařízení dokončila, koncový uživatel musí heslo zadat na zařízení.

## <a name="getting-support"></a>Získání podpory
Přečtěte si další informace o tom, [jak získat podporu pro Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).

