---
title: Přejmenování zařízení pomocí Microsoft Intune – Azure | Microsoft Docs
description: Přejmenujte zařízení pomocí Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1c02248b3208073a3bb09cafe69cf0473eacb2b
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584539"
---
# <a name="rename-a-device-in-intune"></a>Přejmenování zařízení v Intune

Akce **Přejmenovat zařízení** umožňuje přejmenovat zařízení, které je zaregistrované v Intune. V Intune a na zařízení se změní název zařízení.

Můžete přejmenovat následující typy zařízení:
- Okna vlastněná společností 
- iOS – pod dohledem
- MacOS vlastněné společností 10

Tato funkce v současné době nepodporuje přejmenování hybridních zařízení se systémem Windows Azure AD.

## <a name="rename-a-device"></a>Přejmenování zařízení

1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Vyberte **zařízení** > **všechna zařízení** > zvolit zařízení > **více** > **Přejmenovat zařízení**.
4. V okně **Přejmenovat zařízení** zadejte nový název do textového pole. Můžete použít písmena, číslice a spojovníky. Název musí obsahovat alespoň jedno písmeno nebo spojovník.
5. Pokud chcete po přejmenování zařízení restartovat, klikněte na **tlačítko Ano** vedle možnosti **po přejmenování restartovat**.
6. Vyberte možnost **Přejmenovat**.

## <a name="windows-device-rename-rules"></a>Pravidla přejmenování zařízení Windows
Při přejmenování zařízení s Windows musí nové jméno dodržovat tato pravidla:
- maximálně 15 znaků (musí být menší než nebo rovno 63 bajtů, včetně koncové hodnoty NULL)
- Není null nebo prázdný řetězec
- Povolené znakové sady ASCII: písmena (a-z, A – Z), číslice (0-9) a spojovníky
- Povolené kódování Unicode: znaky > = 0x80, musí být platný UTF8, musí být možné mapovat na IDN (to znamená, že RtlIdnToNameprepUnicode je úspěšných, viz RFC 3492)
- Názvy nesmí obsahovat jenom číslice.
- Žádné mezery v názvu
- Nepovolené znaky: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>Další kroky

Pokud chcete zobrazit stav akce **Přejmenovat** zařízení, podívejte se na stránku s **přehledem** pro dané zařízení.