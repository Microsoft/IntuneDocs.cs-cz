---
title: "Konfigurace upgradů edicí Windows 10 pomocí Intune | Intune Azure Preview | Dokumentace Microsoftu"
description: "Intune Azure Preview: Zjistěte, jak můžete pomocí Intune upgradovat spravovaná zařízení s Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: 9ce16ea61da87aa5087fafeb5c1eaf743fef4a14


---

# <a name="how-to-configure-windows-10-edition-upgrades"></a>Jak nakonfigurovat upgrady edicí Windows 10 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Podle informací v tomto tématu můžete nakonfigurovat profil upgradů edicí Windows 10. Tento profil vám umožní automaticky upgradovat zařízení s některou z následujících verzí Windows 10 na novější edici:

- Windows 10 Desktop
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
2. Zvolte **Další služby** > **Jiné** > **Intune**.
3. V okně **Intune** zvolte **Konfigurovat zařízení**.
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
Pokud chcete pokračovat a přiřadit tento profil ke skupinám, podívejte se na téma [Jak přiřadit profily zařízení](how-to-assign-device-profiles.md).




<!--HONumber=Feb17_HO1-->

