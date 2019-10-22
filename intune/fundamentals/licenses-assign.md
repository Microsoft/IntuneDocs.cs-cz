---
title: Přiřazení licencí Microsoft Intune
description: Přiřazení licencí uživatelům, aby mohli zaregistrovat zařízení v Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f09f4ba58e3da5821eea06fcfec6e55c9c007d44
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502703"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Přiřazení licencí uživatelům, aby mohli zaregistrovat zařízení v Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Ať už přidáváte uživatele ručně, nebo provádíte synchronizaci z místní služby Active Directory, musíte nejdřív všem uživatelům přiřadit licence Intune, aby mohli svá zařízení registrovat do Intune. Seznam licencí najdete v tématu [Licence zahrnující Intune](../licenses.md).

## <a name="assign-an-intune-license-in-the-microsoft-365-admin-center"></a>Přiřazení licence Intune v centru pro správu Microsoft 365

[Centrum pro správu Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) můžete použít k ručnímu přidání cloudových uživatelů a přiřazení licencí ke cloudovým uživatelským účtům a účtům synchronizovaným z vaší místní služby Active Directory do Azure AD.

1. Přihlaste se k [centru pro správu Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) pomocí svých přihlašovacích údajů správce tenanta a pak zvolte **Uživatelé** > **aktivní uživatelé**.

2. Vyberte uživatelský účet, kterému chcete přiřadit uživatelskou licenci Intune, a potom vyberte **Licence na produkty** > **Upravit**.

3. Přepněte **Intune** nebo **Enterprise Mobility + Security** na **Zapnuto** a vyberte **Uložit**.

   ![Snímek obrazovky oddílu Microsoft 365 licence k produktu centra pro správu](./media/licenses-assign/office-assign-license.png)

4. Uživatelský účet má teď oprávnění potřebná k používání služby a registraci zařízení pro správu.

> [!NOTE]
> Uživatelé se budou zobrazovat na portálu Intune Classic až po registraci zařízení pomocí POČÍTAČového klienta Intune. Můžete také vybrat skupinu uživatelů a přidat nebo odebrat licence pro všechny najednou.

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Přiřazení licence Intune pomocí Azure Active Directory

Licence Intune můžete uživatelům přiřadit také pomocí Azure Active Directory. Další informace najdete v článku věnovaném [licencování uživatelů v Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal). 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Přiřazení licencí uživatelům v Intune for Education pomocí služby SDS (School Data Sync)
Pokud patříte mezi vzdělávací organizace, můžete k přiřazení licencí na Intune for Education synchronizovaným uživatelům použít službu SDS (School Data Sync). Při nastavování profilu SDS stačí zaškrtnout políčko Intune for Education.  

![Snímek obrazovky s nastavením profilu SDS](./media/licenses-assign/i4e-sds-profile-setup-setting.png)

Při přiřazování licence na Intune for Education ověřte, že je přiřazená také licence Intune A Direct.

![Snímek obrazovky s nastavením produktové licence](./media/licenses-assign/i4e-set-licenses.png)

Další informace o službě SDS najdete v článku [Přehled služby SDS (School Data Sync)](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>Vliv licencí pro uživatele a zařízení na přístup ke službám
* Každý **uživatel** , kterému přiřadíte softwarovou licenci pro uživatele, může získat přístup k online služby a souvisejícímu softwaru (včetně softwaru System Center) a používat ho ke správě aplikací a až 15 zařízení MDM. Intune PC Agent pro počítače umožňuje 5 fyzických a 1 virtuálních počítačů na uživatelskou licenci.
* Licence pro libovolná zařízení si můžete koupit odděleně od uživatelských licencí. Licence zařízení nemusí být přiřazené zařízením. Každé zařízení, které přistupuje k online službám a souvisejícímu softwaru (včetně softwaru System Center) a používá je, musí mít licenci zařízení.
* Pokud zařízení používá více než jeden uživatel, bude každý potřebovat softwarovou licenci pro zařízení nebo budou všichni uživatelé potřebovat softwarovou licenci pro uživatele.

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>Porozumění typu licencí, které jste zakoupili

Informace o předplatném určuje způsob, jakým jste zakoupili Intune:

- Pokud jste Intune zakoupili na základě smlouvy Enterprise, najdete informace o předplatném na portálu multilicencí v části **Předplatná**.
- Pokud jste Intune zakoupili přes poskytovatele Cloud Solution Provider, obraťte se na prodejce.
- Pokud jste Intune zakoupili přes CC# nebo na fakturu, budou vaše licence uživatelské.




## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Použití PowerShellu k selektivní správě uživatelských licencí pro EMS
Organizace, které používají Microsoft Enterprise Mobility + Security (dříve Enterprise Mobility Suite), můžou mít uživatele, kteří v balíčku EMS vyžadují jenom služby Azure Active Directory Premium nebo Intune. Pomocí [rutin PowerShellu pro Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx) můžete přiřadit jednu službu nebo podmnožinu služeb.

Pokud chcete selektivně přiřadit uživatelské licence pro služby EMS, otevřete PowerShell jako správce v počítači, kde je instalovaný [modul Azure Active Directory pro Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule). PowerShell můžete nainstalovat na místní počítač nebo na server služby AD FS.

Musíte vytvořit novou definici SKU licence, která se vztahuje jenom na požadované plány služeb. To provedete tak, že zakážete plány, které nechcete použít. Můžete třeba vytvořit definici SKU licence, která nepřiřazuje licenci pro Intune. Pokud chcete zobrazit seznam dostupných služeb, zadejte:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Spuštěním následujícího příkazu můžete vyloučit plán služby Intune. Stejnou metodu můžete použít k rozšíření na celou skupinu zabezpečení nebo můžete použít podrobnější filtry.

**Příklad 1**<br>
Vytvořte nového uživatele na příkazovém řádku a přiřaďte mu licenci EMS bez povolení části licence pro Intune:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Ověřte pomocí:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Příklad 2**<br>
Zakažte část licence EMS pro Intune uživateli, kterému má licenci už přiřazenou:

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Ověřte pomocí:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/licenses-assign/posh-addlic-verify.png)