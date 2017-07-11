---
title: "Správa propojení uživatelů se zařízeními u počítačů s Windows"
description: "Jak propojit uživatele s počítačem s Windows spravovaným pomocí Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9641c40229be52066a97389584e55f2f95bc286d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Správa propojení uživatelů se zařízeními u počítačů s Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Informace v tomto tématu se vztahují jenom na desktopové systémy Windows, které spravujete jako počítače (PC) pomocí softwarového klienta Intune. 

Abyste mohli nasadit software pro uživatele, musíte uživatele propojit s počítačem. Uživatele můžete propojit s několika počítači, ale každý počítač může být propojený jenom s jedním uživatelem. Uživatelé se automaticky propojí se všemi počítači, které si přes portál společnosti zaregistrovali v Intune.

Propojení uživatele s počítačem:

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com/) zvolte **Skupiny** &gt; **Všechna zařízení** (nebo jinou skupinu obsahující počítač, který chcete propojit s uživatelem).

2.  Vyberte počítač, který chcete propojit s uživatelem, a potom zvolte **Propojit uživatele**.

    V dialogovém okně **Propojit uživatele** se zobrazí seznam dostupných uživatelů včetně jejich zobrazovaného jména, ID a počtu počítačů, se kterými jsou aktuálně propojení. Pokud je s vybraným počítačem už nějaký uživatel propojený, je v části **Aktuální uživatel** zobrazené jeho jméno a ID. Když počítač není propojený s žádným uživatelem, tak se v části **Aktuální uživatel** zobrazuje **Žádný uživatel**.

3.  Udělejte jednu z těchto věcí:

    -   Pokud chcete nechat počítač propojený s případným aktuálním uživatelem, klikněte na **Zrušit**.

    -   Pokud chcete propojení s aktuálním uživatelem odebrat, zvolte **Odebrat odkaz **&gt; **OK**.

    -   Pokud chcete propojit počítač s novým uživatelem, vyberte uživatele v seznamu **Všichni uživatelé**. Potvrďte správnost údajů o uživateli a potom zvolte **OK**.

> [!TIP]
> Když chcete koncovým uživatelům omezit schopnost propojit se s počítači, povolte možnost **Omezit schopnosti uživatelů propojit s počítači vlastní účet** v zásadě **Nastavení agenta Microsoft Intune**.

### <a name="see-also"></a>Viz také

[Běžné úlohy správy počítačů s Windows pomocí klientského softwaru Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)