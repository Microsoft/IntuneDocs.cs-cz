---
title: Přidání vlastního nastavení do zařízení s macOS v Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Nastavení macOS můžete exportovat z nástrojů Apple Configurator nebo Apple Profile Manager a pak je importovat do Microsoft Intune. Tato nastavení můžou vytvářet, používat a řídit vlastní nastavení a funkce na zařízeních macOS. Vlastní profil pak můžete přiřadit zařízením s macOS v organizaci nebo je mezi ně distribuovat, a vytvořit tak základní nebo standardní nastavení.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c24c120b033a4db0162e985ef185932dd931eda
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506925"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Použití vlastního nastavení u zařízení s macOS v Microsoft Intune

V Microsoft Intune můžete použít vlastní profil k přidání nebo vytvoření vlastního nastavení zařízení s macOS. Vlastní profily jsou funkcí Intune. Jsou navržené tak, aby bylo možné přidat nastavení a funkce zařízení, které nejsou integrované do Intune.

U zařízení s macOS existují dva způsoby, jak do Intune dostat vlastní nastavení:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Tyto nástroje můžete použít k exportu nastavení do konfiguračního profilu. Tento soubor importujete do Intune a pak profil přiřadíte uživatelům a zařízením s macOS. Po přiřazení jsou nastavení distribuována. Pro macOS ve vaší organizaci taky vytvoří Směrný plán nebo Standard.

Tento článek obsahuje pokyny k používání Apple Configuratoru a Apple Profile Manageru a popisuje vlastnosti, které můžete nakonfigurovat.

## <a name="before-you-begin"></a>Před zahájením

[Vytvořte profil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Co je potřeba vědět

- Když při vytváření konfiguračního profilu používáte **Apple Configuratoru** , ujistěte se, že nastavení, která exportujete, jsou kompatibilní s verzí MacOS na zařízeních. Informace potřebné k řešení nekompatibilních nastavení najdete v **referenčních materiálech k profilu konfigurace** a **referenčních materiálech k protokolu správy mobilních zařízení** na webu pro [vývojáře Apple](https://developer.apple.com/).

- Pokud používáte **Apple Profile Manager**, nezapomeňte:

  - Povolit v Profile Manageru [správu mobilních zařízení](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C).
  - Přidat [zařízení s macOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) v Profile Manageru.
  - Po přidání zařízení v Profile Manageru přejděte na **Under the Library** (pod Knihovna)  > **Devices** (Zařízení) > vyberte zařízení > **Settings** (Nastavení). Zadejte obecné nastavení, nastavení zabezpečení, ochrany osobních údajů, adresáře a certifikátu zařízení.

    Stáhněte a uložte si tento soubor. Zadáte ho v profilu Intune. 

  - Ujistěte se, že nastavení, která exportujete z nástroje Apple Profile Manager, jsou kompatibilní s verzí macOS na zařízeních. Informace potřebné k řešení nekompatibilních nastavení najdete v **referenčních materiálech k profilu konfigurace** a **referenčních materiálech k protokolu správy mobilních zařízení** na webu pro [vývojáře Apple](https://developer.apple.com/).

## <a name="custom-configuration-profile-settings"></a>Nastavení vlastního konfiguračního profilu

- **Název vlastního konfiguračního profilu:** Zadejte název zásady. Tento název se zobrazí na zařízení a ve stavu Intune.
- **Soubor konfiguračního profilu:** Přejděte ke konfiguračnímu profilu vytvořenému v Apple Configuratoru nebo Apple Profile Manageru. Importovaný soubor se zobrazí v části **Obsah souboru**.

  Do souborů `.mobileconfig` můžete také přidat tokeny zařízení. Tokeny zařízení se používají k přidání informací specifických pro zařízení. Pokud například chcete zobrazit sériové číslo, zadejte `{{serialnumber}}`. V zařízení se text zobrazuje podobně jako `123456789ABC`, což je pro každé zařízení jedinečné. Při zadávání proměnných nezapomeňte použít složené závorky `{{ }}`. [Tokeny konfigurace aplikace](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) obsahují seznam proměnných, které se dají použít. Můžete také použít `deviceid` nebo jiná hodnota specifická pro zařízení.

  > [!NOTE]
  > Proměnné nejsou v uživatelském rozhraní ověřeny a rozlišují se velká a malá písmena. V důsledku toho mohou být profily uloženy s nesprávným vstupem. Pokud například zadáte `{{DeviceID}}` namísto `{{deviceid}}`, pak se místo jedinečného ID zařízení zobrazí literální řetězec. Nezapomeňte zadat správné informace.

Vyberte **OK** > **Vytvořit** a změny uložte. Profil se vytvoří a zobrazí se v seznamu profily.

## <a name="next-steps"></a>Další kroky

Profil je vytvořený, ale zatím se nepoužívá. V dalším kroku [profil přiřadíte](device-profile-assign.md).

Podívejte se, jak [vytvořit profil na zařízeních s iOSem](../custom-settings-ios.md).