---
title: Nastavení integrace Better Mobile s Intune
titleSuffix: Intune on Azure
description: Integrace konektoru Better Mobile do Intune
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.openlocfilehash: 5aad0e4aa0f3377c0d46f241d92712d81e4cfbd6
ms.sourcegitcommit: 973a06f4a35b74314fece2bae17dd6885b4211c3
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42823219"
---
# <a name="integrate-better-mobile-with-intune"></a>Integrace Better Mobile s Intune

Při integraci řešení Better Mobile Threat Defense do Intune je potřeba provést následující kroky.

## <a name="before-you-begin"></a>Před zahájením

> [!NOTE]
> Následující kroky je potřeba provést v [konzole pro správu Better Mobile](https://aad.bmobi.net).

Před zahájením procesu integrace řešení Better Mobile a Intune zkontrolujte, že máte následující:

-   Odběr služby Microsoft Intune

-   Přihlašovací údaje správce Azure Active Directory pro udělení následujících oprávnění:

    -   Přihlášení a čtení profilu uživatele

    -   Přístup k adresáři jako přihlášený uživatel

    -   Čtení dat z adresáře

    -   Odeslání informací o zařízení do Intune

-   Přihlašovací údaje správce pro přístup ke konzole pro správu Better Mobile

### <a name="better-mobile-app-authorization"></a>Autorizace aplikace Better Mobile

Postup autorizace aplikace Better Mobile:

-   Povolte službě Better Mobile předávání informací, které se týkají stavu zařízení, zpět do Intune.

-   Better Mobile se synchronizuje s členstvím skupiny registrace Azure AD, aby se mohla naplnit databáze zařízení.

-   Povolte u konzoly pro správu Better Mobile použití jednotného přihlašování (SSO) k Azure AD.

-   Povolte aplikaci Better Mobile přihlášení pomocí jednotného přihlašování k Azure AD.

## <a name="to-set-up-better-mobile-integration"></a>Nastavení integrace Better Mobile

1. Přejděte ke [konzole pro správu Better Mobile](https://aad.bmobi.net) a přihlaste se pomocí svých přihlašovacích údajů.
2. Zvolte **Integrace** > **EMM/MDM** > **PŘIDAT ÚČET**.

     ![Konzola pro správu Better Mobile](media/better_mobile_console.png)
 
3. Zvolte **Intune**.
4. Vedle položky **NÁZEV ÚČTU** zadejte popisovač. 
5. V okně **Přihlášení k Microsoftu** zadejte svoje přihlašovací údaje k Intune.
6. V okně **Požadovaná oprávnění** zvolte **Přijmout**.
7. Vyhledejte skupiny zabezpečení Azure AD Security, ze kterých má Better Mobile synchronizovat zařízení, a vyberte je v seznamu. Potom vyberte **Pokračovat**.
8. Vyberte **Hotovo**.
9. Znovu se zobrazí stránka **Přidat účet**. Stránku zavřete. 

## <a name="next-steps"></a>Další kroky

-   [Nastavení aplikací Better Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)