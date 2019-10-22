---
title: Ochrana zařízení pomocí Microsoft Intune
titleSuffix: Microsoft Intune
description: Přečtěte si o některých způsobech, kterými vám Intune může pomoct chránit vaše zařízení před neoprávněným přístupem a dalšími hrozbami.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: conceptual
ms.subservice: protect
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 471eb35cb7b96166aaacfbe1ce0ee36cfa06e9c0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502365"
---
# <a name="protect-devices-with-microsoft-intune"></a>Ochrana zařízení pomocí Microsoft Intune

Microsoft Intune pomáhá chránit vámi spravovaná zařízení i data, která jsou na nich uložená.

## <a name="device-configuration"></a>Konfigurace zařízení
[Zásady konfigurace](../configuration/device-profiles.md) umožňují Intune nastavit celou řadu parametrů a funkcí a pomáhají tak s ochranou a konfigurací zařízení. Například:

- Na zařízení můžete omezit používání hardwarových funkcí, jako je fotoaparát nebo Bluetooth.
- Můžete nakonfigurovat, které aplikace splňují či nesplňují vaše požadavky. Když se nainstaluje aplikace nesplňující požadavky, dostanete upozornění (a některé platformy instalaci přímo zablokují).

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Resetování přístupových kódů v případě, že se uživatelé nemůžou přihlásit k zařízení
Vzhledem k tomu, že prvním krokem při ochraně dat společnosti na mobilních zařízeních je vyžadování hesla pro použití zařízení, je někdy nutné [Resetovat heslo](../remote-actions/device-passcode-reset.md) nebo s tím zaměstnanci pomoci odebráním hesla nebo nastavením dočasného hesla vzdáleně. Pokud dojde ke ztrátě nebo odcizení zařízení, můžete ho také [vzdáleně uzamknout](../remote-actions/device-remote-lock.md).

## <a name="retire-devices-and-remove-data"></a>Vyřazení zařízení a odebrání dat
Pokud je potřeba [odebrat zařízení ze správy Intune](../remote-actions/devices-wipe.md) (třeba když uživatel odejde z organizace nebo dojde ke ztrátě či odcizení zařízení), pravděpodobně budete chtít ze zařízení odebrat data. S Intune můžete firemní data uchovat v bezpečí hned několika způsoby.

## <a name="require-devices-to-be-compliant"></a>Nastavení požadavků pro zařízení
Intune obsahuje [zásady dodržování předpisů](device-compliance-get-started.md), s jejichž pomocí můžete vyhodnotit, jaká zařízení nesplňují vámi stanovené požadavky (v některých případech můžete stav i napravit). Můžete si třeba nechat hlásit:
- Zařízení s iOSem s jailbreakem
- Šifrovaná nebo nešifrovaná zařízení
- Stav zařízení s Windows 10 (podle Služby pro ověření stavu)

## <a name="protect-apps-and-the-data-they-use"></a>Ochrana aplikací a jimi využívaných dat
Intune poskytuje celou řadu funkcí, které usnadňují ochranu aplikací a jejich dat. Zásady správy mobilních aplikací například můžou:
- Zabránit zálohování dat z chráněné aplikace
- Zakázat kopírování a vkládání do ostatních aplikací
- Požadovat PIN pro přístup k aplikaci – další informace najdete v tématu [Ochrana dat a aplikací pomocí Microsoft Intune](../apps/app-protection-policy.md)

## <a name="add-an-additional-layer-of-protection-to-devices"></a>Přidání další vrstvy ochrany do zařízení
[Multi-Factor Authentication (MFA)](../enrollment/multi-factor-authentication.md) představuje bezpečnější způsob ověřování uživatelů zařízení v síti.  Pokud se používá služba MFA, uživatelé musí potvrdit svou identitu i jinak než jen pomocí svého uživatelského jména a hesla – prostřednictvím telefonního hovoru nebo SMS zprávy.

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Nastavení Windows Hello pro firmy na zařízeních s Windows
Intune umožňuje integraci se službou [Windows Hello pro firmy](windows-hello.md). Tato alternativní metoda pro přihlašování do systému Windows 10 a novějších pomocí účtu služby Active Directory nebo Azure Active Directory nahrazuje heslo, čipovou kartu nebo virtuální čipovou kartu.

## <a name="bypass-activation-lock-on-ios-devices"></a>Obejití zámku aktivace na zařízeních s iOSem
Zámek aktivace je funkce, která pomáhá chránit zařízení uživatelů. Tato funkce vyžaduje, aby uživatelé před vymazáním nebo opětovnou aktivací zařízení zadali své Apple ID a heslo. Tato funkce ale může vést k problémům, pokud třeba uživatel odejde ze společnosti, aniž by ze zařízení zámek odebral. Možnost [obejít zámek aktivace na zařízeních s iOSem](../remote-actions/device-activation-lock-bypass.md) může pomoct odebrat zámek ze zařízení s iOSem, která jsou pod dohledem, abyste je mohli přidělit jinému uživateli nebo z nich vymazat obsah.

## <a name="next-steps"></a>Další kroky

Přečtěte si další informace o [ochraně před mobilním hrozbami](mobile-threat-defense.md).