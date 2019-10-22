---
title: Zjištěné aplikace
titleSuffix: Microsoft Intune
description: Pochopte podrobnosti o zjištěných aplikacích, které Intune v zařízení našel.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5cadba411ea4aab74c70583062fcb90eccf19aa
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507487"
---
# <a name="intune-discovered-apps"></a>Zjištěné aplikace Intune

**Zjištěné aplikace** v Intune jsou seznam zjištěných aplikací na zařízeních zaregistrovaných v Intune ve vašem tenantovi. Slouží jako inventář softwaru pro vašeho tenanta. **Zjištěné aplikace** jsou samostatnou sestavou z sestav [instalace aplikace](apps-monitor.md) . V případě osobních zařízení Intune nikdy neshromažďuje informace o nespravovaných aplikacích. V podnikových zařízeních je libovolná aplikace, ať už jde o spravovanou aplikaci, nebo není pro tuto sestavu shromažďována. Níže je uvedená tabulka s mapováním očekávaného chování. Obecně platí, že sestava se aktualizuje každých 7 dní od doby registrace (nejedná se o týdenní aktualizaci celého tenanta). Jedinou výjimkou z tohoto intervalu aktualizace jsou informace o aplikaci shromážděné prostřednictvím rozšíření pro správu Intune pro aplikace Win32, které se shromáždí každých 24 hodin.

## <a name="monitor-discovered-apps-with-intune"></a>Monitorování zjištěných aplikací pomocí Intune

Intune poskytuje agregovaný seznam zjištěných aplikací na zařízeních zaregistrovaných v Intune ve vašem tenantovi.

1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. V podokně **Intune** vyberte **klientské aplikace** > **zjištěné aplikace**.

>[!NOTE]
>Seznam zjištěných aplikací můžete exportovat do souboru. csv výběrem možnosti **exportovat** v okně **zjištěné aplikace** .
>
>Pro zjištěné aplikace Win32 není aktuálně k dispozici žádný agregovaný počet. Tento typ dat se dá zobrazit jenom na jednotlivých zařízeních.

Intune také nabízí seznam zjištěných aplikací pro jednotlivá zařízení ve vašem tenantovi.

1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. V podokně Intune vyberte **zařízení** > **všechna zařízení**.
3. Vyberte zařízení.
4. Pokud chcete zobrazit zjištěné aplikace pro toto zařízení, vyberte v části **monitorování** **zjištěné aplikace** .

## <a name="details-of-discovered-apps"></a>Podrobnosti zjištěných aplikací

Následující seznam poskytuje typ aplikační platformy, aplikace, které jsou monitorovány pro osobní zařízení, aplikace, které jsou monitorovány pro zařízení vlastněná společností, a cyklus aktualizace. Další informace o typech aplikací podporovaných službou Intune najdete v tématu [typy aplikací v Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Platforma | Pro zařízení vlastněná osobně | Pro zařízení vlastněná společností | Aktualizovat cyklus |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (aplikace Win32) Poznámka: [vyžaduje rozšíření správy Intune](intune-management-extension.md) na zařízení. | Nelze použít | Všechny aplikace Win32 nalezené v seznamu přidat nebo odebrat programy | Každých 24 hodin od registrace zařízení |
| Windows 10 (moderní aplikace) | Jenom spravované moderní aplikace | Všechny moderní aplikace nainstalované v zařízení | Každých 7 dnů od registrace zařízení |
| Windows 8.1 | Jenom spravované aplikace | Jenom spravované aplikace | Každých 7 dnů od registrace zařízení |
| Windows Phone 8 | Jenom spravované aplikace | Jenom spravované aplikace | Každých 7 dnů od registrace zařízení |
| Windows RT | Jenom spravované aplikace | Jenom spravované aplikace | Každých 7 dnů od registrace zařízení |
| iOS | Jenom spravované aplikace | Všechny aplikace nainstalované v zařízení | Každých 7 dnů od registrace zařízení |
| macOS | Všechny aplikace nainstalované v zařízení | Všechny aplikace nainstalované v zařízení | Každých 7 dnů od registrace zařízení |
| Android | Jenom spravované aplikace | Všechny aplikace nainstalované v zařízení | Každých 7 dnů od registrace zařízení |
| Android Enterprise | Jenom spravované aplikace | Jenom aplikace nainstalované v pracovním profilu | Každých 7 dnů od registrace zařízení |

> [!NOTE]
> Hybridní zařízení s Windows 10 připojená k Azure AD, jak je znázorněno v úloze správy aplikací v Configuration Manager, teď neshromažďují inventář aplikací prostřednictvím rozšíření pro správu Intune (IME) podle výše uvedeného plánu. Aby se tento problém vyřešil, měla by být úloha správy aplikací v Configuration Manager přepnuta do Intune, aby se editor IME nainstaloval na zařízení (vyžaduje se editor IME pro inventarizaci a nasazení PowerShellu). Všimněte si, že jakékoli změny nebo aktualizace tohoto chování jsou oznámeny ve [vývoji](../fundamentals/in-development.md) a/nebo [co je nového](../fundamentals/whats-new.md).

Počet zjištěných aplikací nemusí odpovídat stavovému počtu instalací aplikací. K příčinám nekonzistencí můžou patřit tyto:

- Změna cílení nainstalované spravované aplikace může způsobit, že se počet instalací ve stavovém okně sníží, bude ale dál hlášený mezi zjištěnými aplikacemi.
- Cílení více instancí téže aplikace v tenantovi povede k různým počtům kvůli možnému překrývání uživatelů nebo zařízení. Každá instance aplikace započítá překrývající se uživatele, ale zjištěné aplikace budou mít duplicitní počty.
- Zjištěné aplikace a stavy aplikací se shromažďují v různých časových intervalech, což může způsobit nesoulad v počtech aplikací.

## <a name="next-steps"></a>Další kroky

- [Typy aplikací v Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Monitorování informací a přiřazení aplikace pomocí Microsoft Intune](apps-monitor.md)