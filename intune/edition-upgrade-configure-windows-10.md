---
title: "Konfigurace upgradů edice Windows 10 v Intune"
titleSuffix: Intune on Azure
description: "Přečtěte si, jak můžete pomocí Intune upgradovat spravovaná zařízení s Windows 10 na jinou edici."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30cea0ecfa62e9bbc0200d15eff94782d48a81fa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Konfigurace nastavení upgradu edice Windows 10 v Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Podle informací v tomto tématu můžete nakonfigurovat profil upgradů edicí Windows 10. Tento profil vám umožní automaticky upgradovat zařízení s některou z následujících verzí Windows 10 na jinou edici:

- Windows 10 Home
- Windows 10 Holographic
- Windows 10 Mobile


Podporují se tyto možnosti upgradu:

- Z Windows 10 Pro na Windows 10 Enterprise
- Z Windows 10 Home na Windows 10 Education
- Z Windows 10 Mobile na Windows 10 Mobile Enterprise
- Z Windows 10 Holographic Pro na Windows 10 Holographic Enterprise


## <a name="before-you-start"></a>Než začnete
Před zahájením upgradu zařízení na nejnovější verzi budete potřebovat:

- Kód Product Key, který opravňuje k instalaci nové verze Windows ve všech zařízeních, na která touto zásadou cílíte (pro edice Windows 10 Desktop). Můžete využít klíče k vícenásobné aktivaci (MAK) nebo kódy serveru správy klíčů (KMS). Další možností je použít licenční soubor od Microsoftu, který obsahuje licenční informace pro instalaci nové verze Windows ve všech zařízeních, na která touto zásadou cílíte (pro edice Windows 10 Mobile a Windows 10 Holographic).
- Cílová zařízení Windows 10 musí být registrovaná v Microsoft Intune. Zásady upgradu edice nejde použít pro počítače s klientským softwarem Intune pro počítače.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Vytvoření profilu zařízení obsahujícího nastavení omezení zařízení

1. Přihlaste se k portálu Azure Portal.
2. Zvolte **Další služby** > **Monitorování + správa** > **Intune**.
3. V okně **Intune** zvolte **Konfigurace zařízení**.
2. V okně **Konfigurace zařízení** zvolte **Spravovat** > **Profily**.
3. V okně profilů zvolte **Vytvořit profil**.
4. V okně **Vytvořit profil** zadejte **Název** a **Popis** profilu pro upgrade edice.
5. V rozevíracím seznamu **Platforma** zvolte **Windows 10 a novější**.
6. V rozevíracím seznamu **Typ profilu** zvolte **Upgrade edice**.
7. V okně **Upgrade edice** nakonfigurujte následující nastavení:
    - **Edice, ze které se má provést upgrade** – Vyberte v rozevíracím seznamu verzi Windows 10, kterou chcete na zařízeních upgradovat.
    - **Edice, na kterou se má upgradovat** – V rozevíracím seznamu vyberte verzi Windows 10 Desktop, Windows 10 Holographic nebo Windows 10 Mobile, na kterou chcete cílová zařízení upgradovat.
    - **Kód Product Key** – Zadejte kód Product Key, který jste získali od Microsoftu a který se může použít k upgradu všech cílových zařízení s Windows 10 Desktop.<br>Po vytvoření zásady obsahující kód Product Key už tento kód nepůjde změnit. Důvodem je to, že kód se z bezpečnostních důvodů schová. Pokud chcete kód Product Key změnit, musíte celý kód zadat znovu.
    - **Soubor s licencí** – Zvolte **Procházet** a vyberte soubor s licencí získaný od Microsoftu, který obsahuje informace o licenci pro edici Windows Holographic nebo Windows 10 Mobile, na kterou chcete cílová zařízení upgradovat.
8. Až to budete mít, vraťte se do okna **Vytvořit profil** a klikněte na **Vytvořit**.

Profil se vytvoří a zobrazí se v okně se seznamem profilů.
Pokud chcete pokračovat a přiřadit tento profil ke skupinám, podívejte se na téma [Jak přiřadit profily zařízení](device-profile-assign.md).
