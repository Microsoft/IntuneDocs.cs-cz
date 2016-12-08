---
title: "Zobrazení inventáře hardwaru a softwaru u počítačů s Windows | Microsoft Intune"
description: "Jak zobrazit informace o hardwaru a softwaru počítačů s Windows, které spravujete v Intune"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 807599d4a6a979c88732ab969fdecb64552a83d5


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Zobrazení inventáře hardwaru a softwaru u počítačů s Windows

Intune shromažďuje podrobné informace o hardwaru a softwaru spravovaných počítačů. V následujících postupech se dozvíte toto:

-   Jak vytvořit sestavu s informacemi o hardwarových možnostech počítačů, které spravujete

-   Jak vytvořit sestavu se seznamem softwaru nainstalovaného na jednotlivých počítačích

-   Jak aktualizovat inventář počítačů, abyste měli jistotu, že jsou data v sestavě aktuální

## <a name="to-display-information-about-computers-you-manage"></a>Zobrazení informací o počítačích, které spravujete

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) klikněte na **Sestavy** &gt; **Sestavy inventáře počítače**.

2.  Na stránce **Vytvořit novou sestavu** přijměte výchozí hodnoty, případně je upravte, aby se vyfiltrovaly výsledky, které bude sestava obsahovat. Můžete třeba vybrat, aby se v sestavě zobrazily jenom počítače, na kterých běží Windows 8.1.

3.  Kliknutím na **Zobrazit sestavu** otevřete **sestavu inventáře počítače** v novém okně.

    Když vyberete záhlaví příslušných sloupců, jako je třeba **Název**, **Typ skříně** nebo **Výrobce**, můžete sestavu podle těchto sloupců seřadit.

## <a name="to-display-software-installed-on-computers-you-manage"></a>Zobrazení softwaru nainstalovaného na počítačích, které spravujete

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) zvolte **Sestavy** &gt; **Zjištěné zprávy o softwaru**.

2.  Na stránce **Vytvořit novou sestavu** přijměte výchozí hodnoty, případně je upravte, aby se vyfiltrovaly výsledky, které bude sestava obsahovat. Můžete třeba vybrat, aby se v sestavě zobrazil jenom software publikovaný Microsoftem.

3.  Zvolte **Zobrazit sestavu**. **Sestav rozpoznaného softwaru** se otevře v novém okně.

    Když vyberete záhlaví příslušných sloupců, jako je třeba **Název**, **Vydavatel** nebo **Kategorie** , můžete sestavu podle těchto sloupců seřadit. Zvolením směrové šipky vedle položky seznamu můžete aktualizace v seznamu rozbalit a zobrazit tak další podrobnosti (třeba počítače, na kterých jsou nainstalované).

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Aktualizace inventáře počítače, abyste měli jistotu, že je aktuální

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) zvolte **Skupiny** &gt; **Všechna zařízení** (nebo na jinou skupinu obsahující počítač, pro který chcete inventář aktualizovat).

2.  Vyberte počítač. Nebo když stisknete a podržíte **Ctrl** , můžete vybrat víc počítačů.

3.  Na hlavním panelu zvolte **Vzdálené úlohy** &gt; **Obnovit inventář**.

4.  Pokud chcete zobrazit stav úlohy, v pravém dolním rohu stránky zvolte **Vzdálené úlohy**.

    V dialogovém okně **Stav úlohy** se zobrazí aktuální vzdálené úlohy, stav úloh, název zařízení, všechny hlášené chyby a odkaz na informace o odstraňování problémů.

### <a name="see-also"></a>Související témata

[Běžné úlohy správy počítačů s Windows pomocí klientského softwaru Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->

