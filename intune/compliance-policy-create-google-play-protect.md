---
title: "Povolení zásady dodržování předpisů pro Google Play Protect v Intune"
titleSuffix: Azure portal
description: "Naučte se vytvořit zásadu dodržování předpisů pro zařízení s Androidem, která bude platit pro službu Google Play Protect."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d610bc338c1bcf81ed3bc71f1357e001914c5877
ms.sourcegitcommit: 71e6e80b7370024624ce2e5fad1ca5b372975748
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Jak vytvořit zásadu dodržování předpisů zařízeními pro službu Google Play Protect

Můžete vytvořit novou zásadu dodržování předpisů pro platformu Android, která bude kontrolovat dodržování předpisů službou Google Play Protect (GPP).

Zásadu dodržování předpisů, která vyžaduje potřebná nastavení, můžete potom zacílit na skupinu uživatelů nebo zařízení s Androidem. Pokud zařízení nebude mít povolená požadovaná nastavení, bude se považovat za nedodržující předpisy.

## <a name="create-a-compliance-policy"></a>Tvorba zásady dodržování předpisů

1. Přihlaste se k portálu Azure Portal. Zvolte **Další služby** > **Monitorování + správa** + **Intune**.
2. Ve skupině **Spravovat** zvolte **Dodržování předpisů zařízením**. 
3. Zvolte **Zásady** a potom **Vytvořit zásadu**.
4. Zadejte pro zásadu **Název** a **Popis**.
5. Jako platformu vyberte **Android**.
6. Zvolte **Nastavení** > **Stav zařízení**.
7. Nakonfigurujte nastavení **Google Play Protect**.
8. Po nakonfigurování nastavení Google Play Protect zadejte nastavení **Zabezpečení** a **Vlastnosti zařízení**. Když jste hotovi, klikněte na **OK**.

## <a name="configure-the-google-play-protect-settings"></a>Konfigurace nastavení Google Play Protect

 - **Aplikace Služby Google Play je nakonfigurovaná**  
   Vyžaduje, aby byla nainstalovaná a povolená aplikace Služby Google Play. Aplikace Služby Google Play umožňuje instalaci aktualizací zabezpečení a je základní závislostí pro mnoho funkcí zabezpečení na zařízeních s certifikací Google.
 - **Aktualizovaný poskytovatel zabezpečení**  
   Vyžaduje, aby aktualizovaný poskytovatel zabezpečení chránil zařízení před známými chybami zabezpečení.
 - **Kontrola ohrožení aplikací**  
   Vyžaduje, aby byla povolená funkce Androidu **Ověřovat aplikace**.
    > [!Note]  
    > Na starších verzích platformy Android tato funkce představuje nastavení dodržování předpisů. Intune může jenom zkontrolovat, jestli je toto nastavení povolené na úrovni zařízení. Na zařízeních s pracovními profily (dříve označovaných jako Android for Work) je toto nastavení dostupné jako nastavení zásad konfigurace. To správcům umožňuje povolit nastavení pro zařízení.

    Pokud vaše společnost používá pracovní profily Androidu, můžete nastavení **Kontrola ohrožení aplikací** povolit pro zaregistrovaná zařízení. Vytvořte profil zařízení a vyžadujte v něm toto nastavení zabezpečení systému. Další informace najdete v článku [Nastavení omezení pro zařízení s Androidem for Work v Microsoft Intune](device-restrictions-android-for-work.md).

 - **Ověření zařízení SafetyNet**  
   Nastavuje úroveň integrity, které musí zařízení dosáhnout při ověření SafetyNet. Mezi možné úrovně patří **Nenakonfigurováno**, **Zkontrolovat základní integritu** a **Zkontrolovat základní integritu a certifikovaná zařízení**.




## <a name="next-steps"></a>Další kroky

Další informace o práci se zásadami dodržování předpisů pro zařízení v Intune najdete v článku [Začínáme se zásadami dodržování předpisů zařízeními v Intune](device-compliance-get-started.md).