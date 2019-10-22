---
title: Upgrade nebo použití režimu S v zařízeních S Windows 10 – Microsoft Intune – Azure | Microsoft Docs
description: Pomocí Microsoft Intune můžete upgradovat zařízení s Windows 10 na jinou edici nebo přepnout na režim S. Správci můžou použít konfigurační profil zařízení k upgradu Windows 10 Professional na Windows 10 Enterprise a přepnutí z režimu S. Seznamte se s podporovanými způsoby upgradu pro Windows 10 pro, N Edition, školství, Cloud, Enterprise, Core, holografická a mobilní zařízení.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f5519429bae69fe277c72b12a2801a1875295824
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493789"
---
# <a name="upgrade-windows-10-editions-or-switch-out-of-s-mode-on-devices-using-microsoft-intune"></a>Upgradovat edice Windows 10 nebo zapínat na zařízeních v režimu S použitím Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

V rámci řešení pro správu mobilních zařízení (MDM) můžete chtít upgradovat zařízení s Windows 10. Například chcete upgradovat zařízení s Windows 10 Professional na Windows 10 Enterprise. Nebo chcete, aby zařízení přepnulo režim S.

[Režim Windows 10 S](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) (otevře jiný web společnosti Microsoft) je navržený pro zabezpečení a výkon. K přepnutí do režimu S můžete použít Intune. Přepnutí z režimu S se nedá vrátit. Jakmile se přepnete z režimu S, nemůžete se do tohoto režimu Windows 10 vrátit.

Podívejte se [na nejčastější dotazy](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq) týkající se režimu S.

Tato funkce platí pro:

- Windows 10 a novější
- Windows 10 1809 nebo novější pro režim S
- Windows Holographic for Business

Tyto funkce jsou dostupné v Intune a správce je může nakonfigurovat. Intune používá konfigurační profily k vytvoření a přizpůsobení těchto nastavení potřebám vaší organizace. Po přidání těchto funkcí do profilu můžete tento profil vložit nebo nasadit do zařízení s Windows 10 ve vaší organizaci. Když nasadíte profil, Intune automaticky upgraduje zařízení nebo přepne z režimu S.

Tento článek obsahuje seznam podporovaných cest upgradu a ukazuje, jak vytvořit profil konfigurace zařízení. Můžete si také prohlédnout všechna dostupná nastavení upgradu a režimu S [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Pokud přiřazení zásady odeberete později, verze Windows na zařízení se nevrátí. Zařízení bude nadále fungovat normálně.

## <a name="prerequisites"></a>Požadované součásti

Před upgradem zařízení se ujistěte, že máte následující požadavky:

- Platný kód Product Key k instalaci aktualizované verze Windows na všechna zařízení, na která touto zásadou cílíte (pro edice Windows 10 Desktop). Můžete využít klíče k vícenásobné aktivaci (MAK) nebo kódy serveru správy klíčů (KMS).
- Pro edice Windows 10 Mobile a Windows 10 je možné použít soubor s licencí společnosti Microsoft. Soubor s licencí obsahuje licenční informace pro instalaci aktualizované edice na všechna zařízení, na která tato zásada cílíte.
- Zařízení s Windows 10, kterým zásady přiřazujete, jsou zaregistrovaná v Microsoft Intune. Zásadu upgradu edice nemůžete použít u počítačů s klientským softwarem Intune pro počítače.

## <a name="supported-upgrade-paths"></a>Podporované cesty upgradu

V následující tabulce jsou podporované cesty upgradu pro profil upgradu edice Windows 10.

| Upgradovat z | Upgrade na |
|---|---|
| Windows 10 pro | Windows 10 – vzdělávání <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Edice Windows 10 Pro N | Edice Windows 10 Education N <br/>Edice Windows 10 Enterprise N <br/>Edice Windows 10 Pro Education N | 
| Windows 10 Pro Education | Windows 10 – vzdělávání | 
| Edice Windows 10 Pro Education N | Edice Windows 10 Education N |
| Windows 10 Cloud | Windows 10 – vzdělávání <br/>Windows 10 Enterprise <br/>Windows 10 pro <br/>Windows 10 Pro Education | 
| Edice Windows 10 Cloud N | Edice Windows 10 Education N <br/>Edice Windows 10 Enterprise N <br/>Edice Windows 10 Pro N <br/>Edice Windows 10 Pro Education N | 
| Windows 10 Enterprise | Windows 10 – vzdělávání | 
| Edice Windows 10 Enterprise N | Edice Windows 10 Education N | 
| Windows 10 Core | Windows 10 – vzdělávání <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Edice Windows 10 Core N | Edice Windows 10 Education N <br/>Edice Windows 10 Enterprise N <br/>Edice Windows 10 Pro Education N | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)  (X) = not supported    
![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Mobile|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Holographic|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png) -->

## <a name="create-the-profile"></a>Vytvoření profilu

1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Vyberte **Konfigurace zařízení** > **Profily** > **Vytvořit profil**.
3. Zadejte následující vlastnosti:

    - **Název**: Zadejte popisný název nového profilu. Například zadejte něco jako `Windows 10 edition upgrade profile` nebo `Windows 10 switch off S mode`.
    - **Popis**: Zadejte popis profilu. Toto nastavení není povinné, ale doporučujeme ho zadat.
    - **Platforma**: vyberte platformu:  

        - **Windows 10 a novější**

    - **Typ profilu**: vyberte **upgrade edice**.
    - **Nastavení**: Zadejte nastavení, které chcete konfigurovat. Seznam všech nastavení a o tom, co dělají, najdete v těchto tématech:

        - [Upgrade a režim S Windows 10](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Vyberte **OK** > **Vytvořit** a změny uložte.

Profil se vytvoří a zobrazí se v seznamu. Nezapomeňte [profil přiřadit](device-profile-assign.md) a [monitorovat jeho stav](device-profile-monitor.md).

## <a name="next-steps"></a>Další kroky

Profil je po vytvoření připravený k přiřazení. Dále [Přiřaďte profil](device-profile-assign.md) a [sledujte jeho stav](device-profile-monitor.md).

Zobrazit nastavení upgradu a režimu S pro zařízení S [Windows 10](edition-upgrade-windows-settings.md) a [Windows holografickým pro firmy](holographic-upgrade.md) .