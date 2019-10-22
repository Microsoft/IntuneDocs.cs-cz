---
title: Konektor Zimperium MTD s Intune
titleSuffix: Intune on Azure
description: Přečtěte si o integraci Intune se službou Zimperium Mobile Threat Defense za účelem regulace přístupu mobilních zařízení k firemním prostředkům.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4ff350bd8c1c16eedd30a6b7af4f3927bce3c3e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508763"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Konektor Zimperium Mobile Threat Defense s Intune

Přístup mobilních zařízení k podnikovým prostředkům můžete řídit pomocí podmíněného přístupu na základě posouzení rizik, které provádí Zimperium, řešení ochrany před mobilními hrozbami (MTD), které se integruje s Microsoft Intune. Riziko se posuzuje na základě telemetrie, která se shromažďuje ze zařízení, na kterých aplikace Zimperium běží.

Zásady podmíněného přístupu můžete nakonfigurovat na základě posouzení rizik Zimperium povoleného prostřednictvím zásad dodržování předpisů zařízením v Intune. Zásady hodnocení rizik můžou zařízením nesplňujících požadavky dovolit nebo blokovat přístup k podnikovým prostředkům na základě zjištěných hrozeb.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Jak služby Intune a Zimperium pomáhají chránit prostředky společnosti?

Aplikace Zimperium pro Android a iOS zaznamenává telemetrii systému souborů, zásobníku sítě, zařízení a aplikací tam, kde je k dispozici, a posílá ji do cloudové služby Zimperium, kde se posoudí ohrožení zařízení mobilními hrozbami.

Zásady dodržování předpisů, které platí pro zařízení v Intune, zahrnují pravidlo pro službu Zimperium Mobile Threat Defense. Toto pravidlo je založené na hodnocení rizika službou Zimperium. Když je toto pravidlo aktivní, Intune vyhodnocuje soulad zařízení se zásadami, které jste povolili. Pokud se zjistí, že zařízení nesplňuje dané předpisy, zablokuje se přístup uživatelů k podnikovým prostředkům, jako jsou Exchange Online a SharePoint Online. Uživatelé dostanou také pokyny z mobilní aplikace Zimperium nainstalované na jejich zařízeních, jak problém vyřešit a jak opět získat přístup k firemním prostředkům.

## <a name="sample-scenarios"></a>Ukázkové scénáře

Níže najdete několik scénářů pro integraci řešení Zimperium s Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Řízení přístupu na základě hrozeb od škodlivých aplikací

Když se na zařízeních zjistí přítomnost škodlivých aplikací (třeba malwaru), můžete jim až do vyřešení problému zablokovat následující:

- Připojení k firemnímu e-mailu

- Synchronizaci firemních souborů přes OneDrive for Work

- Přístup k aplikacím společnosti

**Zablokování při zjištění přítomnosti škodlivých aplikací:**

![Zjistila se koncepční bitová kopie škodlivých aplikací.](./media/zimperium-mobile-threat-defense-connector/Maliciousapps_blocked_Zimperium.png)

**Přístup udělený po nápravě:**

![Koncepční bitová kopie přístupu udělená po nápravě](./media/zimperium-mobile-threat-defense-connector/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Řízení přístupu na základě ohrožení sítě

Zjišťuje hrozby v síti, například **útoky prostředníkem**, a chrání přístup k sítím Wi-Fi na základě rizika zařízení.

**Zablokování přístupu k síti prostřednictvím sítě Wi-Fi:**

![Zablokování přístupu k síti prostřednictvím sítě Wi-Fi](./media/zimperium-mobile-threat-defense-connector/network_wifi_blocked_Zimperium.png)

**Přístup udělený po nápravě:**

![Přístup udělený po nápravě](./media/zimperium-mobile-threat-defense-connector/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Řízení přístupu k SharePointu Online na základě ohrožení sítě

Zjišťuje hrozby v síti, například **útoky prostředníkem**, a zabraňuje synchronizaci podnikových souborů na základě rizika zařízení.

**Zablokování SharePointu Online v případě, že se zjistí ohrožení sítě:**

![Zablokování SharePointu Online v případě zjištění ohrožení sítě](./media/zimperium-mobile-threat-defense-connector/network_spo_blocked_Zimperium.png)

**Přístup udělený po nápravě:**

![Sharepointový příklad přístupu uděleného po nápravě](./media/zimperium-mobile-threat-defense-connector/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Podporované platformy

- **Android 4.1 nebo novější**

- **iOS 8 nebo novější**

## <a name="prerequisites"></a>Požadované součásti

- Azure Active Directory Premium

- Odběr služby Microsoft Intune

- Předplatné služby Zimperium Mobile Threat Defense

  - Další informace najdete na [webu Zimperium](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Další kroky

- [Integrace řešení Zimperium do Intune](zimperium-mtd-connector-integration.md)

- [Nastavení aplikací Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Vytvoření zásad dodržování předpisů pro zařízení Zimperium](mtd-device-compliance-policy-create.md)

- [Povolení konektoru Zimperium MTD](mtd-connector-enable.md)