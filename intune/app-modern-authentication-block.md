---
title: "Blokování aplikací bez moderního ověřování v Intune"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fbdb9d6e7e1869aba12b3639b8e887401491a79
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blokování aplikací, které nepoužívají moderní ověřování (ADAL)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Podmíněný přístup založený na aplikaci pomocí zásad ochrany aplikací spoléhá na aplikace, které používají [moderní ověřování](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), což je implementace protokolu OAuth2. Většina současných mobilních a desktopových aplikací Office moderní ověřování používá, existují ale aplikace třetích stran a starší aplikace Office, které používají jiné metody ověřování, například základní ověřování a ověřování na základě formulářů.

Pokud chcete přístup k těmto aplikacím zablokovat, doporučujeme následující postup:

* Nastavte pravidla deklarací služby AD FS pro blokování jiných než moderních ověřovacích protokolů. Podrobné pokyny jsou uvedené ve scénáři 3 – [Blokování veškerého přístupu k O365 kromě aplikací využívajících prohlížeč](https://technet.microsoft.com/library/dn592182.aspx).
* V případě **SharePointu Online** zakažte jiné než moderní ověřování ve službě SharePoint Online pomocí rutiny PowerShellu [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx), která nastaví vlastnost starších verzí protokolů ověřování na hodnotu false:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>Podmíněný přístup založený na aplikaci se nesmí používat s ověřováním na základě certifikátů Azure Active Directory (Azure AD). Současně můžete mít nakonfigurovanou jen jednu z těchto metod.

### <a name="see-also"></a>Viz taky
[Podmíněný přístup na základě aplikace s Intune](app-based-conditional-access-intune.md)