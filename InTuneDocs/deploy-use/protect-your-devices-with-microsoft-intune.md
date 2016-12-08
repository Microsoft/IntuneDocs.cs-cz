---
title: "Ochrana zařízení | Microsoft Intune"
description: "Přečtěte si o některých způsobech, kterými vám Intune může pomoct chránit vaše zařízení před neoprávněným přístupem a dalšími hrozbami."
keywords: 
author: Robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 5c82e905afeab2d7da8a2e9cebf651ed3c8ce21c


---

# Ochrana zařízení pomocí Microsoft Intune

Microsoft Intune nabízí kompletní sadu možností na ochranu vámi spravovaných zařízení a dat, která na nich máte uložená. Přečtěte si toto téma a objevte základní možnosti. Povíme si také, kde se můžete dozvědět víc.

## Jak lze obecně chránit všechna zařízení

### Konfigurace zařízení
[Zásady konfigurace](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) Intune umožňují nastavit celou řadu parametrů a funkcí, a pomáhají tak s ochranou a konfigurací zařízení. Například:
- Na zařízení můžete omezit používání hardwarových funkcí, jako je fotoaparát nebo Bluetooth.
- Můžete nakonfigurovat, které aplikace splňují či nesplňují vaše požadavky. Když se nainstaluje aplikace nesplňující požadavky, dostanete upozornění (a některé platformy instalaci přímo zablokují).

### Resetování přístupových kódů v případě, že se uživatelé nemůžou přihlásit k zařízení
Vzhledem k tomu, že prvním krokem při ochraně dat společnosti na mobilních zařízeních je vyžadování hesla pro použití zařízení, je někdy nutné [Resetovat heslo](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) nebo s tím zaměstnanci pomoci odebráním hesla nebo nastavením dočasného hesla vzdáleně. Pokud dojde ke ztrátě nebo odcizení, můžete také [vzdáleně uzamknout zařízení](use-remote-lock-and-passcode-reset-in-microsoft-intune.md).

### Vyřazení zařízení a odebrání dat
Pokud je třeba [odebrat zařízení ze správy Intune](retire-devices-from-microsoft-intune-management) (třeba když uživatel odejde z organizace nebo dojde ke ztrátě či odcizení zařízení), pravděpodobně budete chtít ze zařízení odebrat data. S Intune můžete data uchovat v bezpečí hned několika způsoby.

### Nastavení požadavků pro zařízení
Intune obsahuje [zásady dodržování předpisů](introduction-to-device-compliance-policies-in-microsoft-intune), s jejichž pomocí můžete vyhodnotit, jaká zařízení nesplňují vámi stanovené požadavky (v některých případech můžete stav i napravit). Můžete například odhalit zařízení iOS s jailbreakem či zašifrovaná zařízení nebo ověřit stav zařízení s Windows 10.

### Ochrana aplikací a jimi využívaných dat
Intune poskytuje celou řadu funkcí, které usnadňují ochranu aplikací a jejich dat. Pomocí zásad správy mobilních aplikací (MAM) se například dá zabránit zálohování dat chráněné aplikace, omezit kopírování a vkládání do jiných aplikací nebo požadovat při přístupu k aplikaci kód PIN. Další podrobnosti o ochraně aplikací najdete v tématu [Ochrana dat a aplikací pomocí Microsoft Intune](protect-apps-and-data-with-microsoft-intune).

## Další možnosti pro zařízení s Windows

### Přidání další vrstvy ochrany do zařízení s Windows
[Multi-Factor Authentication (MFA)](protect-windows-devices-with-multi-factor-authentication.md) představuje bezpečnější způsob ověřování uživatelů zařízení s Windows a Windows Phone v síti.  Pokud se používá služba MFA, uživatelé musí potvrdit svou identitu i jinak než jen pomocí svého uživatelského jména a hesla – prostřednictvím telefonního hovoru nebo SMS zprávy.

### Nastavení Windows Hello pro firmy na zařízeních s Windows
Intune umožňuje integraci se službou [Windows Hello pro firmy](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (dříve Microsoft Passport). Tato alternativní metoda pro přihlašování do systému Windows 10 a novějších pomocí účtu služby Active Directory nebo Azure Active Directory nahrazuje heslo, čipovou kartu nebo virtuální čipovou kartu.

## Další možnosti pro zařízení s iOS

### Obejití zámku aktivace na zařízeních s iOS
Zámek aktivace je funkce, která pomáhá chránit zařízení uživatelů tím, že před vymazáním nebo opětovnou aktivací zařízení od uživatele požaduje zadání Apple ID a hesla. To však může vést k problémům (například pokud uživatel odejde ze společnosti, aniž by ze zařízení zámek odebral). Možnost [obejít zámek aktivace na zařízeních s iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) může pomoct odebrat zámek ze zařízení s iOS, která jsou pod dohledem, abyste je mohli přidělit jinému uživateli nebo z nich vymazat obsah.



## Ochrana osobních počítačů s Windows pomocí klienta Intune
Intune i nadále podporuje zásady zabezpečení pro osobní počítače s Windows, které nejsou registrované, ale spravované pomocí počítačového klientského softwaru Intune. Chcete-li zjistit, jak vám tyto zásady mohou pomoci se zabezpečením osobních počítačů s Windows, přečtěte si téma [Použití zásad k ochraně osobních počítačů s Windows, na nichž běží klientský software Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Oct16_HO4-->

