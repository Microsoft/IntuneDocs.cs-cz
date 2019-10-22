---
title: Integrace služby Zimperium MTD s Microsoft Intune
titleSuffix: Microsoft Intune
description: Přečtěte si, jak integrovat řešení Zimperium Mobile Threat Defense s Microsoft Intune, abyste mohli regulovat přístup mobilních zařízení k firemním prostředkům.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ba94a649f9d7b49437d5d97bb621b0b0a94466c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508682"
---
# <a name="integrate-zimperium-with-intune"></a>Integrace řešení Zimperium do Intune

Při integraci řešení Zimperium Mobile Threat Defense do Intune je potřeba provést následující kroky.

## <a name="before-you-begin"></a>Před zahájením

> [!NOTE]
> Následující kroky je potřeba provést v [konzole Zimperium MTD](https://www.zimperium.com/platform).

Před zahájením procesu integrace řešení Zimperium do Intune zkontrolujte, že máte následující předplatné a přihlašovací údaje:

- Odběr služby Microsoft Intune

- Azure Active Directory přihlašovací údaje správce globálního správce pro udělení následujících oprávnění:

  - Přihlášení a čtení profilu uživatele

  - Přístup k adresáři jako přihlášený uživatel

  - Čtení dat z adresáře

  - Odeslání informací o zařízení do Intune

- Přihlašovací údaje správce pro přístup ke konzole Zimperium MTD

### <a name="zimperium-app-authorization"></a>Autorizace aplikace Zimperium

Postup autorizace aplikace Zimperium:

- Udělte službě Zimperium oprávnění ke sdělování informací týkajících se stavu zařízení zpátky do Intune. Pokud chcete udělit tato oprávnění, musíte použít přihlašovací údaje globálního správce. Udělení oprávnění je jednorázová operace. Po udělení oprávnění nejsou přihlašovací údaje globálního správce potřeba pro každodenní operaci.

- Zimperium se synchronizuje s členstvím skupiny registrace Azure Active Directory (AD), aby se mohla naplnit databáze zařízení.

- Povolte u konzoly pro správu Zimperium použití jednotného přihlašování (SSO) k Azure AD.

- Povolte aplikaci Zimperium přihlášení pomocí jednotného přihlašování k Azure AD.

Další informace o souhlasu a Azure Active Directorych aplikacích najdete v tématu [vyžádání oprávnění od správce adresáře](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) v Azure Active Directory článku *oprávnění a souhlas v koncovém bodu Azure Active Directory v 2.0*.


## <a name="to-set-up-zimperium-integration"></a>Nastavení integrace řešení Zimperium

1. Přejděte do [konzoly Zimperium MTD](https://www.zimperium.com/platform) a přihlaste se pomocí přihlašovacích údajů. Chcete-li provést proces nastavení integrace Zimperium, musíte se přihlásit pomocí Azure Active Directory uživatele, který má roli globálního správce. Tato jednorázová operace nastavení používá globální práva správce k udělení oprávnění ve vaší organizaci, aby aplikace Zimperium komunikovaly s Intune. 

2. Zvolte z levé nabídky možnost **Management** (Správa).

3. Vyberte kartu **MDM settings** (Nastavení MDM).

4. Zvolte **Add MDM** (Přidat MDM) a pak vyberte **Microsoft Intune** ze seznamu **MDM provider** (Zprostředkovatel MDM).

5. Po nastavení Microsoft Intune jako služby MDM se zobrazí okno pro **konfiguraci Microsoft Intune**. Zvolte **Přidat uživatele Azure Active Directory** pro každou z těchto možností: **Zimperium zConsole** a **zIPS pro iOS a Android**. Tím povolíte, aby řešení Zimperium komunikovalo s Intune a Azure AD prostřednictvím jednotného přihlašování Azure AD.

    > [!IMPORTANT]  
    > Abyste mohli dokončit proces integrace s Intune, musíte přidat Zimperium zConsole, zIPS aplikace pro iOS a Android.

6. Volbou **Accept** (Přijmout) povolte komunikaci aplikace Zimperium s Intune a Azure Active Directory.

7. Až do Azure AD přidáte **Zimperium zConsole** a aplikace **zIPS pro iOS a Android** , přidejte skupiny zabezpečení Azure AD. Tím umožníte, aby aplikace Zimperium mohla příslušnou skupinu zabezpečení Azure AD synchronizovat se svou službou.

8. Volbou **Finish** (Dokončit) uložte konfiguraci a spusťte první synchronizaci skupiny zabezpečení Azure AD.

9. Odhlaste se z konzoly Zimperium MTD.

## <a name="next-steps"></a>Další kroky

- [Nastavení aplikací Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)