---
title: "Shromažďování protokolů zařízení"
description: "Přečtěte si, jak shromažďovat protokoly ze spravovaných zařízení."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b15e4b7fa0c650a85a080c42d00cd75cb8783c62
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
# <a name="device-logs"></a>Protokoly zařízení

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Jako součást řešení potíží můžete chtít shromažďovat protokoly ze zařízení uživatelů. Pokyny pro shromažďování těchto protokolů najdete tady. Obvykle potřebujete přístup k zařízení, abyste protokoly získali, nebo požádáte uživatele, aby protokoly shromáždili a poslali vám je.

### <a name="android-logs"></a>Protokoly Androidu
Protokoly Androidu jsou umístěné v adresáři *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Někdy se soubory nezobrazí, zejména na novějších zařízeních s Androidem. V takovém případě požádejte uživatele, aby otevřeli aplikaci Portál společnosti pro Android. Pak by měli zvolit **Nastavení**>**Kopírovat protokoly** a restartovat svá zařízení.

Další informace o tom, jak vám uživatelé můžou posílat svoje protokoly dat, najdete v těchto článcích:

- [Pomoc správci IT s řešením problémů zařízení pomocí podrobného protokolování](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): Popisuje, jak uživatelé můžou zapnout podrobné protokolování, které vám bude automaticky posílat všechny jejich protokoly dat. Ve výchozím nastavení je podrobné protokolování zapnuté.

- [Odeslání protokolů s diagnostickými daty Androidu e-mailem vašemu správci IT](/intune-user-help/send-logs-to-your-it-admin-by-email-android)

- [Odeslání protokolů s diagnostickými daty správci IT pomocí kabelu USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Protokoly iOS

Uživatelé vám můžou posílat chyby registrace. To se popisuje v tématu [Odeslání chyb registrace zařízení s iOSem správci IT](/intune-user-help/send-errors-to-your-it-admin-ios).

Uživatelé můžou posílat protokoly zařízení, jak to popisuje téma [Odeslání protokolů pro zařízení s iOSem](/intune-user-help/send-logs-to-microsoft-ios).

### <a name="mac-os-x-logs"></a>Protokoly Mac OS X

1. Otevřete aplikaci **Konzola**.
2. V části **SOUBORY** zvolte **system.log**.
3. V panelu nabídek nahoře zvolte **Soubor** > **Uložit kopii jako**. Pak soubor uložte.

### <a name="windows-phone"></a>Windows Phone

V aplikaci Portál společnosti pro Windows Phone přejdou uživatelé do nabídky zvolením tří teček (**...**) a pak zvolí **Poslat protokoly**. Tato možnost je k dispozici před i po přihlášení k aplikaci Portál společnosti.

### <a name="windows"></a>Windows

V případě aplikace Portál společnosti pro Windows se protokoly nacházejí v adresáři *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.