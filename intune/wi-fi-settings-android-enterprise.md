---
title: Konfigurace nastavení Wi-Fi pro zařízení s Androidem Enterprise a pro zařízení s beznabídkovým režimem – Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Vytvořte nebo přidejte konfigurační profil zařízení s připojením Wi-Fi pro Android Enterprise a beznabídkový režim Androidu. Podívejte se na různá nastavení, včetně přidání certifikátů, volby typu protokolu EAP a výběru metody ověřování v Microsoft Intune. U zařízení s beznabídkovým režimem zadejte také předsdílený klíč sítě.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c2983f2f7b7079f73c857bf7caafe4236373c5dc
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2018
ms.locfileid: "49431913"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Přidání nastavení Wi-Fi pro zařízení s Androidem Enterprise a s beznabídkovým režimem Androidu v Microsoft Intune

Můžete vytvořit profil s konkrétním nastavením Wi-Fi a potom ho nasadit na zařízení s Androidem Enterprise a na zařízení s beznabídkovým režimem Androidu. Microsoft Intune nabízí mnoho funkcí, například ověřování v síti, použití předsdíleného klíče a další.

Těmito nastaveními se zabývá tento článek.

## <a name="before-you-begin"></a>Před zahájením

[Vytvořte profil zařízení v Microsoft Intune](device-profile-create.md).

## <a name="device-owner-only---kiosk"></a>Jen vlastník zařízení – beznabídkový režim

Tuto možnost vyberte, pokud používáte zařízení s Androidem Enterprise v beznabídkovém režimu.

- **Název sítě**: Zadejte název pro toto připojení Wi-Fi. Tato hodnota představuje název, který uživatelé na svém zařízení uvidí při procházení seznamu dostupných připojení.
- **SSID**: Zkratka pro **Service Set Identifier**. Toto nastavení je reálným názvem bezdrátové sítě, ke které se zařízení připojí. **Název sítě**, který jste nakonfigurovali, ale uživatelé uvidí jen při zvolení připojení.
- **Připojovat automaticky**: Zvolte **Povolit**, pokud se chcete automaticky připojovat k této síti, když je zařízení v rozsahu. Zvolte **Zakázat**, pokud chcete zařízením zabránit v automatickém připojování.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.
- **Typ Wi-Fi**: Vyberte protokol zabezpečení, který se má použít k ověření sítě Wi-Fi. Možnosti:

  - **Otevřené (bez zabezpečení):** tuto možnost použijte jenom v případě, že síť není zabezpečená.
  - **Předsdílený klíč WEP**: Zadejte heslo do pole **Předsdílený klíč**. Po nastavení nebo konfiguraci firemní sítě se nakonfiguruje také heslo nebo síťový klíč. Toto heslo nebo síťový klíč zadejte jako hodnotu PSK.
  - **Předsdílený klíč WPA**: Zadejte heslo do pole **Předsdílený klíč**. Po nastavení nebo konfiguraci firemní sítě se nakonfiguruje také heslo nebo síťový klíč. Toto heslo nebo síťový klíč zadejte jako hodnotu PSK.

Výběrem **OK** uložte změny.

## <a name="work-profile-only"></a>Pouze pracovní profil

### <a name="basic-settings"></a>Základní nastavení

- **Typ Wi-Fi**: Zvolte **Základní**.
- **SSID**: Zkratka pro **Service Set Identifier**. Toto nastavení je reálným názvem bezdrátové sítě, ke které se zařízení připojí.
- **Připojovat automaticky**: Zvolte **Povolit**, pokud se chcete automaticky připojovat k této síti, když je zařízení v rozsahu. Zvolte **Zakázat**, pokud chcete zařízením zabránit v automatickém připojování.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.

## <a name="enterprise-profile"></a>Podnikový profil

- **Typ Wi-Fi**: Zvolte **Enterprise**.
- **SSID**: Zkratka pro **Service Set Identifier**. Toto nastavení je reálným názvem bezdrátové sítě, ke které se zařízení připojí.
- **Připojovat automaticky**: Zvolte **Povolit**, pokud se chcete automaticky připojovat k této síti, když je zařízení v rozsahu. Zvolte **Zakázat**, pokud chcete zařízením zabránit v automatickém připojování.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.
- **Typ EAP**: Zvolte typ protokolu EAP (Extensible Authentication Protocol) pro ověřování zabezpečených bezdrátových připojení. Možnosti: 

  - **EAP-TLS**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Tento certifikát se předloží serveru při připojení klienta k síti a slouží k ověření připojení.

      Výběrem **OK** uložte změny.

    - **Ověřování klientů** – **Klientský certifikát pro ověření klienta (certifikát identity)**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

      Výběrem **OK** uložte změny.

  - **EAP-TTLS**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Tento certifikát se předloží serveru při připojení klienta k síti a slouží k ověření připojení.

      Výběrem **OK** uložte změny.

    - **Ověřování klientů**: Zvolte **metodu ověřování**. Možnosti:

      - **Uživatelské jméno a heslo**: Zobrazí uživateli výzvu k zadání uživatelského jména a hesla pro ověření připojení. Dále zadejte:
        - **Metoda bez protokolu EAP (vnitřní identita)**: Zvolte, jak chcete připojení ověřovat. Nezapomeňte vybrat stejný protokol, který je nakonfigurovaný u sítě Wi-Fi.

          Máte tyto možnosti: **Nešifrované heslo (PAP)**, **CHAP (Challenge Handshake Authentication Protocol)**, **Microsoft CHAP (MS-CHAP)** nebo **Microsoft CHAP verze 2 (MS-CHAP v2)**.

      - **Certifikáty**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

        Výběrem **OK** uložte změny.

      - **Ochrana identity (vnější identita)**: Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

  - **PEAP**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Tento certifikát se předloží serveru při připojení klienta k síti a slouží k ověření připojení.

      Výběrem **OK** uložte změny.

    - **Ověřování klientů**: Zvolte **metodu ověřování**. Možnosti:

      - **Uživatelské jméno a heslo**: Zobrazí uživateli výzvu k zadání uživatelského jména a hesla pro ověření připojení. Dále zadejte:
        - **Ověřování metodou bez protokolu EAP (vnitřní identita)**: Zvolte, jak chcete připojení ověřovat. Nezapomeňte vybrat stejný protokol, který je nakonfigurovaný u sítě Wi-Fi.

          Máte tyto možnosti: **Žádné** nebo **Microsoft CHAP verze 2 (MS-CHAP v2)**.

      - **Certifikáty**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

        Výběrem **OK** uložte změny.

      - **Ochrana identity (vnější identita)**: Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

Vyberte **OK** > **Vytvořit** a změny uložte. Profil se vytvoří a zobrazí se v seznamu profilů.

## <a name="next-steps"></a>Další kroky

Profil se vytvoří, ale nic nedělá. Dále [tento profil přiřaďte](device-profile-assign.md).

## <a name="more-resources"></a>Další zdroje

- Nastavení dostupná pro zařízení s Androidem najdete v článku, který se zabývá [nastaveními Wi-Fi pro zařízení s Androidem](wi-fi-settings-android.md).
- [Přehled nastavení Wi-Fi](wi-fi-settings-configure.md), včetně dalších platforem