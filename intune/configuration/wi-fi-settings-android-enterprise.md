---
title: Nastavení Wi-Fi pro zařízení s Androidem Enterprise a veřejného terminálu – Microsoft Intune | Microsoft Docs
description: Vytvořte nebo přidejte konfigurační profil zařízení s připojením Wi-Fi pro Android Enterprise a beznabídkový režim Androidu. Podívejte se na různá nastavení, včetně přidání certifikátů, volby typu protokolu EAP a výběru metody ověřování v Microsoft Intune. U zařízení s beznabídkovým režimem zadejte také předsdílený klíč sítě.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 266786de3122f8886bb3ed310764459568e1df6a
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585365"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Přidání nastavení Wi-Fi pro zařízení s Androidem Enterprise a s beznabídkovým režimem Androidu v Microsoft Intune

Můžete vytvořit profil s konkrétními nastaveními Wi-Fi a potom tento profil nasadit na zařízení s Androidem Enterprise a Androidem. Microsoft Intune nabízí mnoho funkcí, například ověřování v síti, použití předsdíleného klíče a další.

Těmito nastaveními se zabývá tento článek. [Použití Wi-Fi na vašich zařízeních](wi-fi-settings-configure.md) obsahuje další informace o funkci Wi-fi v Microsoft Intune.

## <a name="before-you-begin"></a>Před zahájením

[Vytvořte profil zařízení v Microsoft Intune](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Pouze vlastník zařízení

Tuto možnost vyberte, pokud používáte vyhrazené zařízení s Androidem Enterprise jako veřejný terminál.

### <a name="basic"></a>Basic

- **Typ Wi-Fi**: Zvolte **Základní**.
- **Název sítě**: Zadejte název pro toto připojení Wi-Fi. Koncoví uživatelé uvidí tento název při procházení svého zařízení k dostupným připojením Wi-FI. Zadejte například **Contoso Wi-Fi**.
- **SSID**: zadejte **identifikátor sady služeb**, což je skutečný název bezdrátové sítě, ke které se zařízení připojují. **Název sítě**, který jste nakonfigurovali, ale uživatelé uvidí jen při zvolení připojení.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.
- **Typ Wi-Fi**: Vyberte protokol zabezpečení, který se má použít k ověření sítě Wi-Fi. Možnosti:

  - **Otevřené (bez zabezpečení):** tuto možnost použijte jenom v případě, že síť není zabezpečená.
  - **Předsdílený klíč WEP**: Zadejte heslo do pole **Předsdílený klíč**. Po nastavení nebo konfiguraci firemní sítě se nakonfiguruje také heslo nebo síťový klíč. Toto heslo nebo síťový klíč zadejte jako hodnotu PSK.
  - **Předsdílený klíč WPA**: Zadejte heslo do pole **Předsdílený klíč**. Po nastavení nebo konfiguraci firemní sítě se nakonfiguruje také heslo nebo síťový klíč. Toto heslo nebo síťový klíč zadejte jako hodnotu PSK.

### <a name="enterprise"></a>Společnosti

- **Typ Wi-Fi**: Zvolte **Enterprise**.
- **SSID**: zadejte **identifikátor sady služeb**, což je skutečný název bezdrátové sítě, ke které se zařízení připojují. **Název sítě**, který jste nakonfigurovali, ale uživatelé uvidí jen při zvolení připojení.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.
- **Typ EAP**: Zvolte typ protokolu EAP (Extensible Authentication Protocol) pro ověřování zabezpečených bezdrátových připojení. Možnosti:

  - **EAP-TLS**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Když se klient připojí k síti, zobrazí se tento certifikát serveru a ověří připojení.

    - **Ověřování klientů** – **Klientský certifikát pro ověření klienta (certifikát identity)** : Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

    - **Ochrana identity (vnější identita)** : Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

  - **EAP-TTLS**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Když se klient připojí k síti, zobrazí se tento certifikát serveru a ověří připojení.

    - **Ověřování klientů**: vyberte **metodu ověřování**. Možnosti:

      - **Uživatelské jméno a heslo**: Zobrazí uživateli výzvu k zadání uživatelského jména a hesla pro ověření připojení. Dále zadejte:
        - **Metoda bez protokolu EAP (vnitřní identita)** : Zvolte, jak chcete připojení ověřovat. Nezapomeňte vybrat stejný protokol, který je nakonfigurovaný u sítě Wi-Fi. Možnosti:

          - **Nezašifrované heslo (PAP)**
          - **Protokol Microsoft CHAP (MS-CHAP)**
          - **Protokol Microsoft CHAP verze 2 (MS-CHAP v2)**

      - **Certifikáty**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

      - **Ochrana identity (vnější identita)** : Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

  - **PEAP**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Když se klient připojí k síti, zobrazí se tento certifikát serveru a ověří připojení.

    - **Ověřování klientů**: vyberte **metodu ověřování**. Možnosti:

      - **Uživatelské jméno a heslo**: Zobrazí uživateli výzvu k zadání uživatelského jména a hesla pro ověření připojení. Dále zadejte:
        - **Ověřování metodou bez protokolu EAP (vnitřní identita)** : Zvolte, jak chcete připojení ověřovat. Nezapomeňte vybrat stejný protokol, který je nakonfigurovaný u sítě Wi-Fi. Možnosti:

          - **Žádné**
          - **Protokol Microsoft CHAP verze 2 (MS-CHAP v2)**

      - **Certifikáty**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

      - **Ochrana identity (vnější identita)** : Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

## <a name="work-profile-only"></a>Pouze pracovní profil

### <a name="basic"></a>Basic

- **Typ Wi-Fi**: Zvolte **Základní**.
- **SSID**: zadejte **identifikátor sady služeb**, což je skutečný název bezdrátové sítě, ke které se zařízení připojují. **Název sítě**, který jste nakonfigurovali, ale uživatelé uvidí jen při zvolení připojení.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.

### <a name="enterprise"></a>Společnosti

- **Typ Wi-Fi**: Zvolte **Enterprise**.
- **SSID**: zadejte **identifikátor sady služeb**, což je skutečný název bezdrátové sítě, ke které se zařízení připojují. **Název sítě**, který jste nakonfigurovali, ale uživatelé uvidí jen při zvolení připojení.
- **Skrytá síť**: Zvolte **Povolit**, pokud chcete tuto síť skrýt v seznamu dostupných sítí na zařízení. Identifikátor SSID se všesměrově nevysílá. Zvolte **Zakázat**, pokud tuto síť chcete v seznamu dostupných sítí na zařízení zobrazit.
- **Typ EAP**: Zvolte typ protokolu EAP (Extensible Authentication Protocol) pro ověřování zabezpečených bezdrátových připojení. Možnosti:

  - **EAP-TLS**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Když se klient připojí k síti, zobrazí se tento certifikát serveru a ověří připojení.

    - **Ověřování klientů** – **Klientský certifikát pro ověření klienta (certifikát identity)** : Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

    - **Ochrana identity (vnější identita)** : Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

  - **EAP-TTLS**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Když se klient připojí k síti, zobrazí se tento certifikát serveru a ověří připojení.

    - **Ověřování klientů**: vyberte **metodu ověřování**. Možnosti:

      - **Uživatelské jméno a heslo**: Zobrazí uživateli výzvu k zadání uživatelského jména a hesla pro ověření připojení. Dále zadejte:
        - **Metoda bez protokolu EAP (vnitřní identita)** : Zvolte, jak chcete připojení ověřovat. Nezapomeňte vybrat stejný protokol, který je nakonfigurovaný u sítě Wi-Fi. Možnosti:

          - **Nezašifrované heslo (PAP)**
          - **Protokol Microsoft CHAP (MS-CHAP)**
          - **Protokol Microsoft CHAP verze 2 (MS-CHAP v2)**

      - **Certifikáty**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

      - **Ochrana identity (vnější identita)** : Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

  - **PEAP**: Dále zadejte:

    - **Vztah důvěryhodnosti serveru** – **Kořenový certifikát pro ověřování serveru**: Zvolte existující profil důvěryhodného kořenového certifikátu. Když se klient připojí k síti, zobrazí se tento certifikát serveru a ověří připojení.

    - **Ověřování klientů**: vyberte **metodu ověřování**. Možnosti:

      - **Uživatelské jméno a heslo**: Zobrazí uživateli výzvu k zadání uživatelského jména a hesla pro ověření připojení. Dále zadejte:
        - **Ověřování metodou bez protokolu EAP (vnitřní identita)** : Zvolte, jak chcete připojení ověřovat. Nezapomeňte vybrat stejný protokol, který je nakonfigurovaný u sítě Wi-Fi. Možnosti:

          - **Žádné**
          - **Protokol Microsoft CHAP verze 2 (MS-CHAP v2)**

      - **Certifikáty**: Zvolte profil klientského certifikátu SCEP nebo PKCS, který je také nasazený na zařízení. Tento certifikát představuje identitu, kterou zařízení předloží serveru pro ověření připojení.

      - **Ochrana identity (vnější identita)** : Zadejte text odeslaný v odpovědi na žádost o identitu EAP. Tento text může být libovolná hodnota, například `anonymous`. Při ověřování se nejdřív pošle tato anonymní identita a po ní následuje skutečná identifikace poslaná přes zabezpečené tunelové propojení.

## <a name="next-steps"></a>Další kroky

Profil se vytvoří, ale nic nedělá. Pak [přiřaďte tento profil](device-profile-assign.md) a [sledujte jeho stav.](device-profile-monitor.md)..

Můžete také vytvořit profily sítě Wi-Fi pro zařízení s [Androidem](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md)a [Windows 8.1](wi-fi-settings-import-windows-8-1.md) .