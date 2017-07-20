---
title: "Podmíněný přístup na základě aplikace s Intune"
description: "Seznamte se s principy fungování podmíněného přístupu na základě aplikace se službou Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0893d511c73e4154c61063d96e26937ea2825467
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Podmíněný přístup na základě aplikace s Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[Zásady ochrany aplikací Intune](app-protection-policy.md) pomáhají chránit vaše firemní data na zařízeních, která jsou zaregistrovaná v Intune. Zásady ochrany aplikací můžete použít také u zařízení vlastněných zaměstnanci, která nejsou zaregistrovaná ke správě v Intune. V takovém případě potřebujete mít pořád jistotu, že jsou vaše firemní data a prostředky chráněné, i když tato zařízení vaše společnost nespravuje.

Podmíněný přístup na základě aplikace a správa mobilních aplikací tvoří další vrstvu zabezpečení, protože zajišťují, že přístup k Exchangi Online a dalším službám Office 365 budou mít pouze mobilní aplikace podporující zásady ochrany aplikací Intune.

> [!NOTE]
> Spravovaná aplikace je taková aplikace, která využívá zásady ochrany aplikací a která lze spravovat pomocí Intune.

Blokovat integrované e-mailové aplikace na zařízeních s iOSem a Androidem můžete jen tehdy, pokud aplikaci Microsoft Outlook povolíte přístup k Exchangi Online. Kromě toho můžete u aplikací, které nepoužívají zásady ochrany aplikací Intune, blokovat přístup k SharePointu Online.

## <a name="prerequisites"></a>Požadavky
Před vytvořením zásady podmíněného přístupu na základě aplikace je potřeba mít:

- **Předplatné Azure Active Directory Premium nebo Enterprise Mobility + Security** a uživatelé musí být licencovaní pro EMS nebo Azure AD.
    - Další informace najdete na [stránce s cenami služby Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) nebo na [stránce s cenami služby Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Podporované aplikace

- **Exchange Online**:
    - Microsoft Outlook pro Android a iOS
<br></br>
- **SharePoint Online**
    - Microsoft Word pro iOS a Android
    - Microsoft Excel pro iOS a Android
    - Microsoft PowerPoint pro iOS a Android
    - Microsoft OneDrive pro firmy pro iOS a Android
    - Microsoft OneNote pro iOS
<br></br>
- **Microsoft Teams**

    > [!NOTE] 
    > Podmíněný přístup na základě aplikace [podporuje také obchodní aplikace](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication). Ty ale musí využívat [moderní ověřování Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).

## <a name="how-app-based-conditional-access-works"></a>Jak podmíněný přístup na základě aplikace funguje

V tomto příkladu použil správce zásady ochrany aplikací u aplikace Outlook a následné pravidlo podmíněného přístupu. To přidá Outlook na seznam schválených aplikací, které lze využít k přístupu k firemnímu e-mailu.

> [!NOTE] 
> Vývojový diagram vyobrazený níže lze použít i pro další spravované aplikace.

![Vývojový diagram podmíněného přístupu na základě aplikace s Intune](./media/ca-intune-common-ways-3.png)

1.  Uživatel se pokusí ověřit ve službě Azure AD z aplikace Outlook.

2.  Při prvním pokusu o ověření je uživatel přesměrován do obchodu s aplikacemi, odkud si má nainstalovat zprostředkující aplikaci. Zprostředkující aplikací může být buď Microsoft Authenticator pro zařízení s iOSem, nebo Portál společnosti Microsoft pro zařízení s Androidem.

    > [!NOTE]
    > Pokud se v tomto scénáři uživatel pokusí použít nativní e-mailovou aplikaci, bude přesměrován do obchodu s aplikacemi, aby si nainstaloval aplikaci Outlook.

3.  Zprostředkující aplikace se nainstaluje na zařízení.

4.  Zprostředkující aplikace zahájí proces registrace v Azure AD, který v této službě vytvoří záznam zařízení. Tento proces se liší od procesu registrace ke správě mobilních zařízení. Záznam je ale nutný k tomu, aby bylo možné vynucovat na zařízení zásady podmíněného přístupu.

5.  Zprostředkující aplikace ověří identitu aplikace. Zde se používá vrstva zabezpečení, která umožňuje zprostředkující aplikaci ověřit, zda má aplikace oprávnění k použití uživatelem.

6.  Zprostředkující aplikace odešle v rámci ověřování uživatele ID klienta aplikace do Azure AD, aby zkontrolovala, že je v seznamu schválených zásad.

7.  Azure AD umožní ověření uživatele a použití aplikace na základě seznamu schválených zásad. Pokud aplikace v tomto seznamu není, Azure AD k ní uživateli zakáže přístup.

8.  Aplikace Outlook komunikuje s cloudovou službou Outlooku a iniciuje tak komunikaci s Exchangem Online.

9.  Cloudová služba Outlooku komunikuje s Azure AD, aby pro uživatele načetla přístupový token služby Exchange Online.

10.  Aplikace Outlook komunikuje s Exchangem Online, aby načetla firemní e-mail uživatele.

11.  Firemní e-mail se doručí do uživatelovy poštovní schránky.

## <a name="next-steps"></a>Další kroky
[Vytvoření zásady podmíněného přístupu na základě aplikace](app-based-conditional-access-intune-create.md)

[Blokování aplikací, které nepoužívají moderní ověřování](app-modern-authentication-block.md)