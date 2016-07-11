---
title: "Příručka pro testování Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 4af13629986e7cef814104f3d1f298eb2be240ac
ms.openlocfilehash: 26ecc3dfe8816da9f30829901d929af53b1bedc0


---

# Příručka pro testování Intune
Nastavení bezplatného 30denního testování Intune pro správu mobilních zařízení a počítačů je rychlé a snadné. Pomocí několika jednoduchých kroků můžete do testování přidat až 100 uživatelů a zařízení, nastavit skupiny, nakonfigurovat zásady dodržování předpisů a registrovat a spravovat mobilní zařízení a počítače.

V tomto tématu se dozvíte základní informace o zprovoznění testování Intune a získáte o službě Intune přehled, abyste mohli vyhodnotit její funkce a možnosti.

Podívejte se na následující pětiminutovou videoukázku, ve které se dozvíte, jak je snadné začít s bezplatným zkušebním používáním Microsoft Intune a spravovat zařízení. První část videa se zmiňuje o portálu, který byl „vyřazen“, a i když budete používat jiný portál, kroky budou v podstatě stejné. Další informace o portálu najdete [zde](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365).

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## Před zahájením
Před zahájením práce s Intune budete potřebovat:

-   Zařízení s webovým prohlížečem, který podporuje technologii Silverlight a který můžete použít pro přístup k webům, kde vytvoříte uživatelské účty Intune (**Centrum pro správu Office 365**) a kde budete spravovat zařízení, skupiny a zásady (**konzola pro správu Intune**).

-   Druhé zařízení s webovým prohlížečem, které použijete k testování toho, jak budou uživatelé Intune zapisovat a spravovat svá zařízení pomocí portálu společnosti. Budete taky testovat, jak budou uživatelé moct hledat a instalovat aplikace a požádat správce o pomoc. Pokud nemáte druhé zařízení, můžete použít „režim ochrany osobních údajů“ ve stejném prohlížeči, který používáte pro správu Intune (třeba v Internet Exploreru můžete zvolit **Nástroje**&gt;**Procházení InPrivate**).

-   Pokud máte stávající účet služeb Microsoft Online Services, budete pro něj potřebovat přihlašovací údaje správce. Pokud uvedený účet nemáte nebo chcete tohoto klienta Intune použít jenom pro účely hodnocení, pak tyto přihlašovací údaje správce potřebovat nebudete.

-   Pokud budete spravovat zařízení s iOS nebo Windows Phone pomocí testování Intune, budete potřebovat certifikáty (nebo klíče) a účty k načtení těchto certifikátů (viz následující tabulka). Zařízení s Androidem žádné další certifikáty nepotřebují.

    |Platforma|Požadavky na certifikát|Další informace|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 a Windows Phone 8 |Pro uživatele Windows Phone 8.1, kteří si aplikaci Portál společnosti nainstalují ze Storu, žádný certifikát potřeba není. Pro Windows Phone 8.0 nebo v případě použití Intune k nasazení aplikace Portál společnost na zařízení s Windows Phone 8.1 se vyžaduje certifikát Symantec.|Tyto pokyny předpokládají, že uživatelé aplikaci Portál společnosti získají ze Storu na zařízení s Windows Phone 8.1 nebo novějším. Informace o podpoře zařízení Windows Phone 8.0 najdete v tématu [Nastavení správy pro zařízení Windows Phone v Microsoft Intune](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).|
    |Zařízení s Windows 10, Windows RT 8.1, Windows RT nebo Windows 8.1|Na registraci zařízení s Windows RT a Windows nejsou žádné požadavky.|[Instalace klienta na počítači s Windows pomocí Microsoft Intune](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune).|
    |iOS 7.1 nebo novější|Získání certifikátu služby Apple Push Notification:|Požádejte o certifikát služby Apple Push Notification od společnosti Apple, jak se popisuje v tématu [Nastavení správy pro iOS a Mac pomocí Microsoft Intune](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).|

## Kroky k dokončení 30denního testování Intune
- [Krok 1: Registrace nebo přihlášení k 30dennímu testování](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md). Před registrací nebo přihlášením k Intune byste měli zvážit, jestli se chcete přihlásit pomocí existujícího účtu nebo si vytvořit dočasný účet pouze pro účely 30denního testování Microsoft Intune.
- [Krok 2: Přidání uživatelů](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md). Po nastavení účtu můžete buď přidávat jednotlivé uživatelské účty do Intune, nebo přidávat uživatele hromadně (viz pokyny v této části). Než s tím začnete, je důležité, abyste rozuměli tomu, jak Intune zachází s účty správců.
- [Krok 3: Vytvoření skupiny pro uspořádání uživatelů a zařízení](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md). Skupiny v Intune poskytují flexibilitu pro správu zařízení a uživatelů. Můžete nastavit skupiny podle potřeb vaší organizace (třeba podle zeměpisné polohy, oddělení nebo vlastností hardwaru) a použít je k provádění řady úloh správy se škálováním od nastavení zásad pro sadu uživatelů po nasazení aplikací na sadu zařízení.
- [Krok 4: Vytvoření zásad a publikování aplikace](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md) Intune nabízí nastavení, které pomáhá řídit nastavení zabezpečení na mobilních zařízeních, spravovat nastavení brány Windows Firewall a Endpoint Protection pro počítače a nasazovat aplikace.
- [Krok 5: Registrace mobilních zařízení a instalace aplikace](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md). Abyste v Intune nastavili správu mobilních zařízení, musíte nastavit autoritu pro správu mobilního zařízení, povolit správu pro specifické platformy zařízení a zaregistrovat zařízení pomocí aplikace Portálu společnosti. Pak můžete nasadit aplikaci Microsoft Skype, kterou jste publikovali.
- [Krok 6: Další možnosti a funkce](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md). Vyberte si způsob používání výstrah, sestav a dalších možností Intune tak, aby to vyhovovalo vašim obchodním potřebám
- [Krok 7: Další kroky](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md). Připravte se na přechod na placené předplatné Intune a využijte výhod Centra FastTrack pro Intune.


### Další kroky
Je na čase zahájit 30denní testovací předplatné!

>[!div class="step-by-step"]
[**Registrace k Intune** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### Související témata
[Úvodní příručka služby Intune](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Jun16_HO4-->

