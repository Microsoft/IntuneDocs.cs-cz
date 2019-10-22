---
title: Výjimky zásad přenosu dat pro aplikace
titleSuffix: Microsoft Intune
description: Vytvořte výjimky zásad přenosu dat ve správě mobilních aplikací Intune (MAM).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01c3bfe853d87f42a6171999f6b358fb73844fb1
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499479"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Vytvoření výjimek zásad přenosu dat ve správě mobilních aplikací Intune (MAM)

Jako správce můžete vytvořit výjimky zásad přenosu dat ve správě mobilních aplikací Intune (MAM). Pomocí výjimky lze konkrétně vybrat nespravované aplikace, které budou moct přenášet data do spravovaných aplikací a ze spravovaných aplikací. Vaše IT oddělení musí důvěřovat nespravovaným aplikacím, které jste zahrnuli do seznamu výjimek. 

>[!WARNING] 
> Za provádění změn v zásadách výjimek přenosu dat nesete zodpovědnost. Nespravované aplikace (aplikace, které nejsou spravované pomocí Intune), které přidáte do těchto zásad, budou mít přístup k datům chráněným pomocí spravovaných aplikací. Takový přístup k chráněným datům může mít za následek porušení zabezpečení dat. Výjimky přenosu dat přidávejte jenom pro aplikace, které vaše organizace musí používat, ale které nepodporují zásady ochrany aplikací Intune. Kromě toho přidávejte výjimky jenom pro aplikace, které nepovažujete za rizikové z hlediska úniku dat.

V rámci zásad ochrany aplikací Intune nastavení **Allow aplikace pro přenos dat do jiných aplikací** do **aplikací spravovaných podle zásad** znamená, že aplikace může přenášet data jenom do aplikací spravovaných přes Intune. Pokud potřebujete povolit přenos dat do konkrétních aplikací, které nepodporují aplikaci Intune, můžete k této zásadě vytvořit výjimky pomocí **vybrat aplikace, které se mají vyloučit**. Výjimky umožňují, aby aplikace spravované Intune vyvolaly nespravované aplikace založené na protokolu URL (iOS) nebo názvu balíčku (Android). Intune přidává ve výchozím nastavení důležité nativní aplikace do seznamu výjimek. 

> [!NOTE]
> Změna nebo přidání aplikací do výjimek zásad přenosu dat nemá vliv na jiné zásady ochrany aplikací, jako jsou omezení vyjmutí, kopírování a vložení. 

## <a name="ios-data-transfer-exceptions"></a>Výjimky přenosu dat pro iOS
U zásad cílících na iOS můžete nakonfigurovat výjimky přenosu dat pomocí protokolu URL. Pokud chcete přidat výjimku, vyhledejte informace o podporovaných protokolech URL v dokumentaci od vývojáře příslušné aplikace. Další informace o výjimkách přenosu dat pro iOS najdete v tématu [nastavení zásad ochrany aplikací pro iOS – výjimky přenosu dat](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> U aplikací jiných výrobců Microsoft nenabízí metodu ručního vyhledání protokolu adresy URL pro vytváření výjimek aplikací. 

## <a name="android-data-transfer-exceptions"></a>Výjimky přenosu dat pro Android
U zásad cílících na Android můžete nakonfigurovat výjimky přenosu dat pomocí názvu balíčku aplikace. Název balíčku aplikace můžete vyhledat na stránce obchodu **Google Play** pro aplikaci, pro kterou chcete přidat výjimku. Další informace o výjimkách přenosu dat pro Android najdete v tématu [nastavení zásad ochrany aplikací pro Android – výjimky přenosu dat](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> ID balíčku aplikace najdete tak, že na tuto aplikaci přejdete v obchodě Google Play. ID balíčku je součástí adresy URL stránky aplikace. Třeba aplikace Microsoft Word má ID balíčku **com.microsoft.office.word**.

### <a name="example"></a>Příklad
Po přidání balíčku **Webex** jako výjimky k zásadám přenosu dat MAM se budou moct odkazy Webex v e-mailové zprávě spravovaného Outlooku otevírat přímo v aplikaci Webex. V ostatních nespravovaných aplikacích bude přenos dat i nadále omezený.

- Příklad **WebEx** pro iOS: Pokud chcete určit výjimku pro aplikaci **WebEx** , aby ji mohly vyvolávat spravované aplikace Intune, je nutné přidat výjimku přenosu dat pro následující řetězec: <code>wbx</code>
    
- Příklad **mapování** iOS: Pokud chcete určit výjimku pro nativní aplikaci **Maps** , aby ji mohly vyvolávat spravované aplikace Intune, je nutné přidat výjimku přenosu dat pro tento řetězec: <code>maps</code>

- Příklad **WebEx** pro Android: Pokud chcete určit výjimku pro aplikaci **WebEx** , aby ji mohly vyvolávat spravované aplikace Intune, je nutné přidat výjimku přenosu dat pro následující řetězec: <code>com.cisco.webex.meetings</code>
    
- Příklad **SMS** pro Android: Pokud chcete určit výjimku pro nativní aplikaci **SMS** , aby ji mohly vyvolávat spravované aplikace Intune v různých aplikacích pro zasílání zpráv a zařízeních s Androidem, musíte přidat výjimky přenosu dat pro následující řetězce: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Další kroky

- [Vytvoření a nasazení zásad ochrany aplikací](app-protection-policies.md)
- [Nastavení zásad ochrany aplikací pro iOS – výjimky přenosu dat](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Nastavení zásad ochrany aplikací pro Android – výjimky přenosu dat](app-protection-policy-settings-android.md#data-transfer-exemptions)