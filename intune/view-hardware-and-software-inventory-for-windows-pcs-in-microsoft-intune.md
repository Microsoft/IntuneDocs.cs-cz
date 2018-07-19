---
title: Zobrazení inventáře hardwaru a softwaru u počítačů s Windows
titlesuffix: Microsoft Intune
description: Jak zobrazit informace o hardwaru a softwaru počítačů s Windows, které spravujete pomocí klienta softwaru Intune
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: beba79e6f8e169fc7cb5852e1bafa7ae96270388
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310534"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Zobrazení inventáře hardwaru a softwaru u počítačů s Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Intune shromažďuje podrobné informace o hardwaru a softwaru počítačů, které spravujete pomocí klienta softwaru Intune. V následujících postupech se dozvíte toto:

-   Jak vytvořit sestavu s informacemi o hardwarových možnostech počítačů, které spravujete

-   Jak vytvořit sestavu se seznamem softwaru nainstalovaného na jednotlivých počítačích

-   Jak aktualizovat inventář počítačů, abyste měli jistotu, že jsou data v sestavě aktuální

## <a name="to-display-information-about-pcs-you-manage"></a>Zobrazení informací o počítačích, které spravujete

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) klikněte na **Sestavy** &gt; **Sestavy inventáře počítače**.

2.  Na stránce **Vytvořit novou sestavu** přijměte výchozí hodnoty, případně je upravte, aby se vyfiltrovaly výsledky, které bude sestava obsahovat. Můžete třeba vybrat, aby se v sestavě zobrazily jenom počítače, na kterých běží Windows 8.1.

3.  Kliknutím na **Zobrazit sestavu** otevřete **sestavu inventáře počítače** v novém okně.

    Když vyberete záhlaví příslušných sloupců, jako je třeba **Název**, **Typ skříně** nebo **Výrobce**, můžete sestavu podle těchto sloupců seřadit.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Zobrazení softwaru nainstalovaného na počítačích, které spravujete

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) zvolte **Sestavy** &gt; **Zjištěné zprávy o softwaru**.

2.  Na stránce **Vytvořit novou sestavu** přijměte výchozí hodnoty, případně je upravte, aby se vyfiltrovaly výsledky, které bude sestava obsahovat. Můžete třeba vybrat, aby se v sestavě zobrazil jenom software publikovaný Microsoftem.

3.  Zvolte **Zobrazit sestavu**. **Sestav rozpoznaného softwaru** se otevře v novém okně.

    Když vyberete záhlaví příslušných sloupců, jako je třeba **Název**, **Vydavatel** nebo **Kategorie** , můžete sestavu podle těchto sloupců seřadit. Zvolením směrové šipky vedle položky seznamu můžete aktualizace v seznamu rozbalit a zobrazit tak další podrobnosti (třeba počítače, na kterých jsou nainstalované).

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Aktualizace inventáře počítače, abyste měli jistotu, že je aktuální

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) zvolte **Skupiny** &gt; **Všechna zařízení** (nebo jinou skupinu obsahující počítač, pro který chcete inventář aktualizovat).

2.  Vyberte počítač. Nebo když stisknete a podržíte **Ctrl**, můžete vybrat víc počítačů.

3.  Na hlavním panelu zvolte **Vzdálené úlohy** &gt; **Obnovit inventář**.

4.  Pokud chcete zobrazit stav úlohy, v pravém dolním rohu stránky zvolte **Vzdálené úlohy**.

    V dialogovém okně **Stav úlohy** se zobrazí aktuální vzdálené úlohy, stav úloh, název zařízení, všechny hlášené chyby a odkaz na informace o odstraňování problémů.

### <a name="see-also"></a>Viz taky

[Běžné úlohy správy počítačů s Windows pomocí klientského softwaru Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)