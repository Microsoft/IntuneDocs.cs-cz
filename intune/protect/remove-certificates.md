---
title: Odebrání certifikátů SCEP a PKCS v Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Správci můžou k odebrání certifikátů z Microsoft Intune použít akce vymazání nebo vyřazení. Při některých scénářích, třeba při zrušení registrace zařízení nebo při odebrání zásady dodržování předpisů, se certifikát odebere automaticky. Při jiných scénářích naopak certifikáty zůstanou v zařízení, třeba při ztrátě nebo odebrání licence v Intune. Podívejte se na různé způsoby u zařízení se systémy Android, Android Enterprise, iOS, macOS a Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: e00600abb8327623eff4efe8509670779710ab7d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509032"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Odebrání certifikátů SCEP a PKCS v Microsoft Intune

V Microsoft Intune můžete k přidávání certifikátů do zařízení použít profily certifikátů Simple Certificate Enrollment Protocol (SCEP) a PKCS (Public Key Cryptography Standards).

Tyto certifikáty je možné odebrat, když zařízení [vymažete](../remote-actions/devices-wipe.md#wipe) nebo vyřadíte z [provozu](../remote-actions/devices-wipe.md#retire) . K dispozici jsou také scénáře, kdy se certifikáty automaticky odstraňují, a scénáře, kdy se certifikáty na zařízení nacházejí. V tomto článku najdete nejčastější scénáře, které mají vliv na certifikáty PKCS a SCEP.

> [!NOTE]
> Pokud chcete odebrat a odvolat certifikáty pro uživatele, který se odebírá z místní služby Active Directory nebo Azure Active Directory (Azure AD), postupujte podle těchto kroků v uvedeném pořadí:
>
> 1. Vymazání nebo vyřazení zařízení uživatele.
> 2. Odeberte uživatele z místní služby Active Directory nebo Azure AD.

## <a name="manually-deleted-certificates"></a>Ručně odstraněné certifikáty

Ruční odstranění certifikátu je scénář, který platí pro různé platformy a certifikáty zřízené profily certifikátů SCEP nebo PKCS. Uživatel může například odstranit certifikát ze zařízení, když zařízení cílí na zásady certifikátu.

V tomto scénáři se po odstranění certifikátu při příštím ověření zařízení v Intune zjistí, že nedodržuje předpisy, protože u něho chybí očekávaný certifikát. Intune pak vystaví nový certifikát pro obnovení kompatibility zařízení. K obnovení certifikátu není nutná žádná další akce.

## <a name="windows-devices"></a>Zařízení s Windows

### <a name="scep-certificates"></a>Certifikáty SCEP

K odvoláni *a* odebrání certifikátu SCEP dojde, když:

- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .
- Zařízení se odebere ze skupiny Azure AD.
- Z přiřazení skupiny se odebere profil certifikátu.

K odvolání certifikátu SCEP dojde, když:
- Správce změní nebo aktualizuje profil SCEP.

Kořenový certifikát se odebere, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Certifikáty SCEP *zůstávají* v zařízení (certifikáty se neodvolává ani neodeberou), když:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.

### <a name="pkcs-certificates"></a>Certifikáty PKCS

K odvoláni *a* odebrání certifikátu PKCS dojde, když:

- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Kořenový certifikát se odebere, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Certifikáty PKCS *zůstávají* v zařízení (certifikáty se neodvolává nebo odeberou) v těchto případech:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.
- Správce změní nebo aktualizuje profil PKCS.
- Z přiřazení skupiny se odebere profil certifikátu.


## <a name="ios-devices"></a>zařízení s iOS

### <a name="scep-certificates"></a>Certifikáty SCEP

K odvoláni *a* odebrání certifikátu SCEP dojde, když:

- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .
- Zařízení se odebere ze skupiny Azure AD.
- Z přiřazení skupiny se odebere profil certifikátu.

K odvolání certifikátu SCEP dojde, když:
- Správce změní nebo aktualizuje profil SCEP.

Kořenový certifikát se odebere, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Certifikáty SCEP *zůstávají* v zařízení (certifikáty se neodvolává ani neodeberou), když:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.

### <a name="pkcs-certificates"></a>Certifikáty PKCS

K odvoláni *a* odebrání certifikátu PKCS dojde, když:

- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

K odebrání certifikátu PKCS dojde, když:
- Z přiřazení skupiny se odebere profil certifikátu.

Kořenový certifikát se odebere, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Certifikáty PKCS *zůstávají* v zařízení (certifikáty se neodvolává nebo odeberou) v těchto případech:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.
- Správce změní nebo aktualizuje profil PKCS.

## <a name="android-knox-devices"></a>Zařízení s Androidem KNOX

### <a name="scep-certificates"></a>Certifikáty SCEP

K odvoláni *a* odebrání certifikátu SCEP dojde, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .

K odvolání certifikátu SCEP dojde, když:
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .
- Zařízení se odebere ze skupiny Azure AD.
- Z přiřazení skupiny se odebere profil certifikátu.
- Správce odebere uživatele nebo skupinu z Azure AD.
- Správce změní nebo aktualizuje profil SCEP.

Kořenový certifikát se odebere, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Certifikáty SCEP *zůstávají* v zařízení (certifikáty se neodvolává ani neodeberou), když:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.

### <a name="pkcs-certificates"></a>Certifikáty PKCS

K odvoláni *a* odebrání certifikátu PKCS dojde, když:

- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Kořenový certifikát se odebere, když:
- Uživatel zruší registraci.
- Správce spustí akci [vymazání](../remote-actions/devices-wipe.md#wipe) .
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .

Certifikáty PKCS *zůstávají* v zařízení (certifikáty se neodvolává nebo odeberou) v těchto případech:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.
- Správce změní nebo aktualizuje profil PKCS.
- Z přiřazení skupiny se odebere profil certifikátu.


> [!NOTE]
> Zařízení s Androidem for Work nejsou ověřená pro předchozí scénáře.
> Pro odebrání certifikátu nejsou povolena starší verze zařízení se systémem Android (zařízení nevyužívající Samsung, nepracovní profil).

## <a name="macos-certificates"></a>Certifikáty macOS

### <a name="scep-certificates"></a>Certifikáty SCEP

K odvoláni *a* odebrání certifikátu SCEP dojde, když:
- Uživatel zruší registraci.
- Správce spustí akci [vyřazení](../remote-actions/devices-wipe.md#retire) .
- Zařízení se odebere ze skupiny Azure AD.
- Z přiřazení skupiny se odebere profil certifikátu.

K odvolání certifikátu SCEP dojde, když:
- Správce změní nebo aktualizuje profil SCEP.

Certifikáty SCEP *zůstávají* v zařízení (certifikáty se neodvolává ani neodeberou), když:
- Uživatel ztratí licenci Intune.
- Správce odvolá licenci Intune.
- Správce odebere uživatele nebo skupinu z Azure AD.

> [!NOTE]
> U zařízení s macOS není podporované obnovení továrního nastavení akcí [vymazání](../remote-actions/devices-wipe.md#wipe).

### <a name="pkcs-certificates"></a>Certifikáty PKCS

Certifikáty PKCS nejsou v macOS podporované.
