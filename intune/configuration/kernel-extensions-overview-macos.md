---
title: Vytvoření profilu zařízení rozšíření jádra macOS pomocí Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Přidejte nebo vytvořte profil zařízení macOS a potom nakonfigurujte rozšíření jádra, aby bylo možné přepsat uživatele, přidat identifikátor týmu a sadu prostředků a identifikátor týmu v Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: abcd7b96de8f5f3984c2d4407abaf11b7b6b7e4f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492487"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Přidání rozšíření jádra macOS v Intune

Na zařízeních macOS můžete přidat funkce na úrovni jádra. Tyto funkce přistupují k částem operačního systému, ke kterým nemají běžné programy přístup. Vaše organizace může mít konkrétní potřeby nebo požadavky, které nejsou k dispozici v aplikaci, funkci zařízení atd. 

Pokud chcete přidat rozšíření jádra, která se vždycky můžou v zařízeních načíst, přidejte do Microsoft Intune rozšíření jádra (KEXT) a potom tato rozšíření nasaďte do svých zařízení.

Máte třeba program pro kontrolu virů, který v zařízení hledá škodlivý obsah. Toto rozšíření jádra programu pro kontrolu virů můžete přidat jako povolené rozšíření jádra v Intune. Pak přiřaďte rozšíření k zařízením macOS.

Díky této funkci můžou správci uživatelům umožnit přepsat rozšíření jádra, přidat identifikátory týmu a přidat konkrétní rozšíření jádra do Intune.

Tato funkce platí pro:

- macOS 10.13.2 a novější

Aby bylo možné tuto funkci používat, musí být zařízení:

- Zaregistrované v Intune pomocí Program registrace zařízeníu (DEP) společnosti Apple. [Automatická registrace zařízení MacOS](../enrollment/device-enrollment-program-enroll-macos.md) obsahuje další informace.

  NEBO

- Zaregistrováno v Intune s "uživatelem schváleným zápisem" (termínem Apple). [Příprava na změny rozšíření jádra v MacOS High Sierra](https://support.apple.com/en-us/HT208019) (otevře web společnosti Apple) obsahuje další informace.

Intune používá konfigurační profily k vytvoření a přizpůsobení těchto nastavení potřebám vaší organizace. Po přidání těchto funkcí do profilu můžete profil vložit nebo nasadit, abyste macOS zařízení ve vaší organizaci.

V tomto článku se dozvíte, jak vytvořit profil konfigurace zařízení pomocí rozšíření jádra v Intune.

> [!TIP]
> Další informace o rozšíření jádra najdete v tématu [Přehled rozšíření jádra](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (otevření webu společnosti Apple).

## <a name="what-you-need-to-know"></a>Co je potřeba vědět

- Je možné přidat nepodepsaná starší verze rozšíření jádra.
- Nezapomeňte zadat správný identifikátor týmu a ID sady rozšíření jádra. Intune neověřuje hodnoty, které zadáte. Pokud zadáte chybné informace, rozšíření na zařízení nebude fungovat.

> [!NOTE]
> Informace společnosti Apple, které se týkají podepisování a notarization pro veškerý software. U macOS 10.14.5 a novějších rozšíření jádra nasazená přes Intune nemusí splňovat zásady notarization od společnosti Apple.
>
> Informace o těchto zásadách notarization a všech aktualizacích a změnách najdete v následujících zdrojích informací:
>
> - [Notarizing aplikaci před distribucí](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (otevře web společnosti Apple) 
> - [Příprava na změny rozšíření jádra v MacOS High Sierra](https://support.apple.com/en-us/HT208019) (otevře web společnosti Apple)

## <a name="create-the-profile"></a>Vytvoření profilu

1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Vyberte **Konfigurace zařízení** > **Profily** > **Vytvořit profil**.
3. Zadejte následující vlastnosti:

    - **Název**: Zadejte popisný název nového profilu.
    - **Popis**: Zadejte popis profilu. Toto nastavení není povinné, ale doporučujeme ho zadat.
    - **Platforma**: vyberte **MacOS**
    - **Typ profilu**: vyberte **rozšíření**.
    - **Nastavení**: Zadejte nastavení, které chcete konfigurovat. Seznam všech nastavení a o tom, co dělají, najdete v těchto tématech:

        - [macOS](kernel-extensions-settings-macos.md)

4. Až to budete mít, vyberte **OK** > **Vytvořit** a změny uložte.

Profil se vytvoří a zobrazí se v seznamu. Nezapomeňte [profil přiřadit](../device-profile-assign.md) a [monitorovat jeho stav](../device-profile-monitor.md).

## <a name="next-steps"></a>Další kroky

Profil je po vytvoření připravený k přiřazení. Dále [Přiřaďte profil](../device-profile-assign.md) a [sledujte jeho stav](../device-profile-monitor.md).