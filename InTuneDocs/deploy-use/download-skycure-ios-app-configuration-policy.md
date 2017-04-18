---
title: "Stažení zásad konfigurace aplikace Skycure pro iOS | Dokumentace Microsoftu"
description: "Stáhněte si zásady konfigurace aplikace Skycure pro iOS, které můžete použít s aplikací Skycure pro iOS nasazenou pro koncové uživatele."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: b05083e6c5c93a8ed68477341a1ac732019fa764
ms.lasthandoff: 03/22/2017


---

# <a name="download-skycure-ios-app-configuration-policy"></a>Stažení zásad konfigurace aplikace Skycure pro iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>Před zahájením

K provedení dalších kroků je potřeba, abyste se přihlásili do konzoly pro správu Skycure.

> [!TIP] 
> Pokud používáte Microsoft Internet Explorer 11 nebo Edge, budete možná muset otevřít konzolu pro správu Skycure v anonymním okně prohlížeče.

## <a name="to-download-the-ios-app-configuration-policy"></a>Postup stažení zásad konfigurace aplikace pro iOS

1.  Přejděte do [konzoly pro správu Skycure](https://aad.skycure.com).

2.  Zadejte své **přihlašovací údaje správce Skycure** a potom klikněte na **Continue** (Pokračovat).

    ![Přihlášení do konzoly pro správu Skycure](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Uživatelské jméno správce Skycure je e-mailový účet, který musí být platným uživatelským účtem služby Azure Active Directory, jinak se přihlášení nezdaří. Služba Skycure k ověření uživatelského jména správce používá službu Azure Active Directory a jednotné přihlašování (SSO).

3.  Přejděte do **Settings** (Nastavení ) &gt; **Device Management Integrations** (Integrace správy zařízení) &gt; **EMM Integration Selection** (Volba integrace EMM), vyberte **Microsoft Intune** a potom svou volbu uložte.

2.  Klikněte na odkaz **Integration setup files** (Integrační soubory nastavení) a vygenerovaný soubor \*.zip uložte. Soubor .zip obsahuje soubor **skycure\_configuration.plist**, který se použijte k vytvoření zásad konfigurace aplikace pro iOS v klasické konzole služby Intune.

![Integrační soubory nastavení služby Skycure](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Další kroky

[Přidání aplikací Skycure, aplikace Microsoft Authenticator a zásad konfigurace aplikace pro iOS](https://docs.microsoft.com/intune/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)
