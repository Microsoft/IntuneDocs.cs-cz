---
title: Omezení pro zařízení s Windows 10 Team v Microsoft Intune
titleSuffix: ''
description: Přečtěte si o omezeních zařízení, která jsou k dispozici pro zařízení s Windows 10 Team.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 20e25b2a2d1b20e577e99cf0b391945c16c67c64
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72489880"
---
# <a name="microsoft-intune-windows-10-team-device-restriction-settings"></a>Nastavení omezení pro zařízení s Windows 10 Team v Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Tento článek ukazuje nastavení omezení zařízení v Microsoft Intune, která můžete nakonfigurovat pro zařízení s Windows 10 Team.


## <a name="apps-and-experience"></a>Aplikace a prostředí

- **Probudit obrazovku, když je někdo v místnosti** – Umožňuje automatické probuzení zařízení, když jeho senzor zachytí osobu v místnosti.
- **Zobrazování informací o schůzkách na úvodní obrazovce** – Pokud povolíte tuto možnost, budete moct zvolit informace, které se zobrazí na dlaždici Schůzky na úvodní obrazovce. Můžete postupovat následovně:
  - **Zobrazit jenom organizátora a čas**
  - **Zobrazit organizátora, čas a předmět (u privátních schůzek je předmět skrytý)**
- **Adresa URL obrázku na pozadí úvodní obrazovky** – Povolením tohoto nastavení umožníte zobrazit na **úvodní** obrazovce zařízení s Windows 10 Team vlastní pozadí ze zadané adresy URL.<br>Obrázek musí být ve formátu PNG a adresa URL musí začínat **https://** .

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights** – Služba Azure Operational Insights, která je součástí sady Microsoft Operations Manager, shromažďuje, ukládá a analyzuje data protokolů ze zařízení s Windows 10 Team.
Pokud se chcete připojit k Azure Operational Insights, musíte zadat **ID** a **klíč pracovního prostoru**.

## <a name="maintenance"></a>Údržba

- **Časové období údržby pro aktualizace** – Konfiguruje okno pro provádění aktualizací na zařízení. Můžete nakonfigurovat **Počáteční čas** okna a jeho **Dobu trvání v hodinách** (1 až 5 hodin).

## <a name="wireless-projection"></a>Bezdrátová projekce

- **Kód PIN pro bezdrátovou projekci** – Určuje, jestli před použitím možností bezdrátové projekce zařízení musíte zadat kód PIN.
- **Bezdrátová projekce Miracast** – Tuto možnost vyberte, pokud chcete zařízením s Windows 10 Team umožnit použít k projekci zařízení s podporou Miracastu.
- **Kanál bezdrátové projekce Miracast** – Vyberte kanál Miracast, který se použije k navázání připojení.


## <a name="next-steps"></a>Další kroky

S použitím informací v tématu [Jak nakonfigurovat nastavení omezení zařízení](../device-restrictions-configure.md) uložte a přiřaďte profil uživatelům a zařízením.