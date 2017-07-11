---
title: "Konfigurace vlastního názvu domény"
description: "Přidání názvu vlastní domény do předplatného Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d75292ce60eb1db232aed12fc80a7cbccc063fb4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="configure-a-custom-domain-name"></a>Konfigurace vlastního názvu domény

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

V tomto tématu najdou správci informace o tom, jak vytvořit záznam DNS CNAME pro zjednodušení a přizpůsobení možností přihlašování.

Pokud si vaše organizace zaregistruje cloudovou službu Microsoftu, třeba Intune, získáte počáteční název domény, jejímž hostitelem je Azure Active Directory (AD). Název může vypadat takto: **vaše_doména.onmicrosoft.com**. V tomhle příkladu je **vaše_doména** název domény, který jste si zvolili při registraci, a **onmicrosoft.com** je přípona přiřazená účtům přidaným do vašeho předplatného. Pokud má vaše organizace vlastní doménu, můžete instanci Intune nakonfigurovat tak, aby místo názvu domény poskytnutého s vaším předplatným používala tuto doménu.

Než vytvoříte uživatelské účty nebo synchronizujete místní službu Active Directory, důrazně doporučujeme, abyste se rozhodli, jestli chcete používat jenom doménu .onmicrosoft.com, nebo jestli chcete přidat jeden nebo více názvů vlastních domén. Konfigurace vlastní domény před přidáním uživatelů může zjednodušit správu identit uživatelů ve vašem předplatném, protože se uživatelé budou moct přihlašovat pomocí přihlašovacích údajů, které používají pro přístup k jiným prostředkům domény.

Když se přihlásíte k odběru cloudové služby od Microsoftu, stane se instance této služby [tenantem služby Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), která bude vašim cloudovým službám poskytovat identitu a adresářové služby. Vzhledem k tomu, že postup konfigurace Intune pro používání vlastního názvu domény vaší organizace je stejný jako u jiných tenantů Azure AD, můžete použít informace a postupy uvedené v tématu [Přidání domény](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Další informace o používání vlastní domény s cloudovou službou od Microsoftu najdete v tématu věnovaném [koncepčnímu přehled vlastních názvů domén v Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Tento počáteční název domény nelze přejmenovat ani odebrat. Můžete však přidat, ověřit nebo odebrat své vlastní názvy domén, které chcete používat s Intune, což je užitečné, pokud chcete zachovat svou obchodní identitu.

## <a name="to-add-and-verify-your-custom-domain"></a>Přidání a ověření vlastní domény

1. Přejděte na [portál pro správu Office 365](https://portal.office.com/Admin/Default.aspx) a přihlaste se k účtu správce.

2. V navigačním podokně zvolte **Nastavení** &gt; **Domény**.

3. Zvolte **Přidat doménu** a zadejte vlastní název domény.

4. Otevře se dialogové okno **Ověřit doménu** s hodnotami pro vytvoření záznamu TXT u poskytovatele hostingu DNS.
    - **Uživatelé GoDaddy:** Portál pro správu Office 365 vás přesměruje na přihlašovací stránku služby GoDaddy. Po zadání přihlašovacích údajů a přijetí smlouvy o oprávnění ke změně domény se záznam TXT vytvoří automaticky. Případně můžete [záznam TXT vytvořit](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a).
    - **Uživatelé Register.com:** Postupujte podle [podrobných pokynů](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) k vytvoření záznamu TXT.

Postup pro přidání a ověření vlastní domény může být také [proveden v Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Další informace najdete v článku [Informace o vaší počáteční doméně onmicrosoft.com v Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A).