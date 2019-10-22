---
title: Řešení potíží s profily zařízení v Microsoft Intune – Azure | Microsoft Docs
description: Běžné dotazy a odpovědi se zásadami a profily zařízení, včetně změn profilu, které se u uživatelů nebo zařízení nepoužijí, jak dlouho trvá, než se nové zásady přidají do zařízení, která nastavení se použijí, když je k dispozici několik zásad, co se stane, když Profil se odstranil nebo odebírá a je k disMicrosoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7779e265680ded1b5d5d5b670bcf694376ee8016
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72494412"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Běžné otázky, problémy a řešení se zásadami a profily zařízení v Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Získejte odpovědi na běžné otázky při práci s profily a zásadami zařízení v Intune. Tento článek také uvádí časové intervaly vrácení se změnami, zajišťuje více zadržených konfliktů a další.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Proč uživatel nezíská nový profil, když změníte heslo u existujícího profilu Wi-Fi?

Vytvoříte profil podnikové sítě Wi-Fi, nasadíte profil u skupiny, změníte heslo a profil uložíte. Když se profil změní, nemusí někteří uživatelé nový profil obdržet.

Abyste zmírnili následky tohoto problému, nastavte Wi-Fi pro hosty. Když selže podniková síť Wi-Fi, můžou se uživatelé připojit k Wi-Fi pro hosty. Je nutné povolit veškerá nastavení automatického připojení. Nasaďte profil sítě Wi-Fi pro hosty všem uživatelům.

Další doporučení:  

- Pokud síť Wi-Fi, ke které se připojujete, používá heslo nebo přístupové heslo, ujistěte se, že se můžete připojit k směrovači sítě Wi-Fi přímo. Můžete to vyzkoušet na zařízení s iOSem.
- Až se úspěšně připojíte ke koncovému bodu sítě Wi-Fi (směrovači sítě Wi-Fi), zapište si identifikátor SSID a použité přihlašovací údaje (heslo).
- Zadejte identifikátor SSID a přihlašovací údaje (heslo) do pole Předsdílený klíč. 
- Nasaďte profil u testovací skupiny, která má omezený počet uživatelů, nejlépe jenom u IT týmu. 
- Synchronizujte vaše zařízení s iOSem do Intune. Zaregistrujte se (pokud jste to ještě neudělali). 
- Vyzkoušejte připojení ke stejnému koncovému bodu sítě Wi-Fi (jak je uvedeno v prvním kroku).
- Zaveďte profil u větších skupin a nakonec u všech předpokládaných uživatelů ve vaší organizaci. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Jak dlouho trvá, než zařízení získá zásadu, profil nebo aplikaci po jejich přiřazení?

Intune oznamuje zařízení, aby se mohla zaregistrovat ve službě Intune. Doba oznámení se liší, včetně okamžitého až několika hodin. Tato doba oznámení se také liší mezi platformami.

Pokud se zařízení po prvním oznámení nevrátí se změnami, zobrazí se v Intune tři další pokusy. Zařízení, které je offline, například vypnuté nebo není připojené k síti, nemusí dostávat oznámení. V takovém případě zařízení získá zásadu nebo profil při dalším plánovaném ohlášení se změnami ve službě Intune, která se **odhadne** na:

| Platforma | Aktualizovat cyklus|
| --- | --- |
| iOS | Přibližně každých 8 hodin |
| macOS | Přibližně každých 8 hodin |
| Android | Přibližně každých 8 hodin |
| Počítače s Windows 10 zaregistrované jako zařízení | Přibližně každých 8 hodin |
| Windows Phone | Přibližně každých 8 hodin |
| Windows 8.1 | Přibližně každých 8 hodin |

Pokud se zařízení nedávno zaregistrovalo, spouští se ověření kompatibility a konfigurace častěji, **Odhadované** na:

| Platforma | Četnost |
| --- | --- |
| iOS | Každých 15 minut po dobu 1 hodiny a pak přibližně každých 8 hodin |  
| macOS | Každých 15 minut po dobu 1 hodiny a pak přibližně každých 8 hodin | 
| Android | Každé 3 minuty každé 3 minuty, potom každých 15 minut, 2 hodiny a pak každých 8 hodin. | 
| Počítače s Windows 10 zaregistrované jako zařízení | Každé 3 minuty každé 3 minuty, potom každých 15 minut, 2 hodiny a pak každých 8 hodin. | 
| Windows Phone | Každých 15 minut každých 5 minut, potom každých 15 minut a pak přibližně každých 8 hodin | 
| Windows 8.1 | Každých 15 minut každých 5 minut, potom každých 15 minut a pak přibližně každých 8 hodin | 

Uživatel může kdykoli otevřít aplikaci Portál společnosti, **nastavení** > **synchronizace** , aby okamžitě kontrolovala aktualizace zásad nebo profilů.

U zařízení bez přidružení uživatele se četnost synchronizací hned po registraci může lišit od hodin až po jeden den. Intune odesílá žádosti v různých intervalech, aby bylo možné zařízení zaregistrovat v Intune. Je ale stále až do zařízení, které se má vrátit. Po počáteční registraci je doba, kterou zařízení potřebuje k dokončení vrácení se změnami, nepředvídatelné. Záleží taky na typu registrace zařízení a zásadách a profilech přiřazených k zařízení. Jakmile se zařízení zaregistruje a uplatní se všechny počáteční zásady a profily, zařízení zkontroluje nové zásady a profily o každé 6-8 hodiny na základě toho, kdy se zařízení zaregistruje v Intune.

Osvědčeným postupem je zajistit, aby vaše zařízení byla online po dobu nejméně osmi po sobě jdoucích hodin, abyste dosáhli nejlepších výsledků.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Které akce způsobí, že Intune hned pošle oznámení do zařízení?

K dispozici jsou různé akce, které aktivují oznámení, například když je přiřazena zásada, profil nebo aplikace (nebo Nepřiřazená), aktualizovaná, Odstraněná a tak dále. Tato akce se mezi platformami liší.

Zařízení se zaregistrují v Intune, když dostanou oznámení pro vrácení se změnami nebo při plánovaném vrácení se změnami. Když zacílíte na zařízení nebo uživatele s akcí, jako je například uzamčení, resetování hesla, aplikace, profil nebo přiřazení zásad, pak Intune okamžitě oznámí zařízení, aby se tyto aktualizace dostalo.

Další změny, jako je třeba úprava kontaktních informací v aplikaci Portál společnosti, nezpůsobí okamžité oznámení na zařízení.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Pokud se stejnému zařízení nebo uživateli přiřadí několik zásad, jak poznám, které nastavení se použije?

Pokud se stejnému uživateli nebo zařízení přiřadí dvě nebo více zásad, pak se nastavení, které platí, stane na úrovni jednotlivých nastavení:

- Nastavení zásad dodržování předpisů mají vždycky přednost před nastavením konfiguračního profilu.

- Pokud se zásada dodržování předpisů vyhodnotí proti stejnému nastavení v jiné zásadě dodržování předpisů, uplatní se toto nastavení zásad dodržování předpisů.

- Pokud je nastavení zásady konfigurace v konfliktu s nastavením jiné zásady konfigurace, zobrazí se tento konflikt v Intune. Konflikty vyřešte ručně.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Co se stane, když zásady ochrany aplikací navzájem kolidují? Která se použije pro příslušnou aplikaci?

Nejpřísnějším nastavením dostupným v zásadách ochrany aplikací jsou konfliktní hodnoty, *s výjimkou* polí s počtem zadání, jako jsou třeba pokusy o připnutí před resetováním. Pole pro zadání čísla se nastavují stejně jako hodnoty, jako kdybyste vytvořili zásadu MAM pomocí možnosti Doporučené nastavení.

Ke konfliktům dochází, když jsou dvě nastavení profilu stejná. Představte si třeba, že jste nakonfigurovali dvě zásady MAM, které jsou stejné až na nastavení kopírování/vkládání. V tomto scénáři se nastavení kopírování/vkládání nastaví na nejvíce omezující hodnotu, ale ostatní nastavení se použijí tak, jak se nakonfigurovala.

Zásada se nasadí do aplikace a projeví se. Je nasazená druhá zásada. V tomto scénáři má přednost první zásada a zůstane u nich použito. Druhá zásada ukazuje konflikt. Pokud jsou obě aplikovány současně, což znamená, že nejsou předchozí zásady, dojde ke konfliktu obou. Všechna konfliktní nastavení se nastaví na nejvíce omezující hodnoty.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Co se stane při konfliktu vlastních zásad iOS?

Intune nevyhodnocuje datovou část konfiguračních souborů Apple nebo vlastní zásady OMA-URI (Open Mobile Alliance Uniform Resource Identifier). Slouží jenom jako mechanismus doručování.

Když přiřadíte vlastní zásadu, zkontrolujte, jestli nakonfigurované nastavení není v konfliktu s dodržováním předpisů, konfigurací nebo jinými vlastními zásadami. Pokud vlastní zásada a její nastavení kolidují, nastavení se náhodně použije.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Co se stane, když se profil odstraní nebo už není použitelný?

Když odstraníte profil nebo odeberete zařízení ze skupiny, která má profil, pak se profil a nastavení ze zařízení odeberou, jak je popsáno níže:

- Profily sítě Wi-Fi, VPN, certifikátu a e-mailu: Tyto profily se odeberou ze všech podporovaných registrovaných zařízení.
- Všechny ostatní typy profilů:  

  - **Zařízení s Windows a Androidem**: nastavení se ze zařízení odeberou.
  - **Zařízení Windows Phone 8.1**: Odeberou se tato nastavení:  
  
    - Vyžadovat heslo k odemknutí mobilních zařízení
    - Povolit jednoduchá hesla
    - Minimální délka hesla
    - Vyžadovaný typ hesla
    - Vypršení platnosti hesla (dny)
    - Pamatovat si historii hesel
    - Počet povolených opakovaných neúspěšných přihlášení, než bude zařízení vymazáno
    - Počet minut nečinnosti před vyžadováním hesla
    - Typ požadovaného hesla – minimální počet znaků
    - Povolit fotoaparát
    - Vyžadovat šifrování u mobilního zařízení
    - Povolit vyměnitelné úložiště
    - Povolit webový prohlížeč
    - Povolit obchod s aplikacemi
    - Povolit snímek obrazovky
    - Povolit zeměpisnou polohu
    - Povolit účet Microsoft
    - Povolit kopírování a vkládání
    - Povolit sdílení internetového připojení přes Wi-Fi
    - Povolit automatické připojení k bezplatným Wi-Fi hotspotům
    - Povolit oznamování Wi-Fi hotspotů
    - Povolit vymazání
    - Povolit Bluetooth
    - Povolit komunikaci NFC
    - Povolit Wi-Fi

  - **iOS**: Odeberou se všechna nastavení s těmito výjimkami:
  
    - Povolit hlasový roaming
    - Povolit datový roaming
    - Povolit automatickou synchronizaci při roamingu

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Změnil(a) jsem profil omezení zařízení, ale tyto změny se neprojevily

Po nastavení zařízení Windows Phone nedovolí, aby se v zabezpečení snížily zásady zabezpečení nastavené pomocí MDM nebo EAS. Například nastavíte **minimální počet znaků hesla** na hodnotu 8. Pokusíte se ho zmenšit na 4. V zařízení se už používá více omezující profil.

Pokud chcete profil změnit na méně bezpečnou hodnotu, resetujte zásady zabezpečení. Například v Windows 8.1 na ploše potáhnutím prstem vpravo > vyberte **nastavení** > **Ovládací panely**. Vyberte aplet **Uživatelské účty** . V navigační nabídce vlevo najdete odkaz **resetovat zásady zabezpečení** (směrem k dolnímu). Vyberte ho a potom zvolte **Resetovat zásady**.

Jiná zařízení MDM, například Android, Windows Phone 8,1 a novější, iOS a Windows 10, může být potřeba vyřadit a znovu zaregistrovat do Intune a použít tak méně omezující profil.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Některá nastavení v profilu Windows 10 vrátí "nepoužitelné".

Některá nastavení na zařízeních s Windows 10 se můžou zobrazovat jako "nepoužitelné". Pokud k tomu dojde, toto konkrétní nastavení se nepodporuje ve verzi nebo edici Windows spuštěné v zařízení. Tato zpráva může nastat z následujících důvodů:

- Nastavení je dostupné jenom pro novější verze Windows a ne pro aktuální verzi operačního systému (OS) na zařízení.
- Toto nastavení je dostupné jenom pro konkrétní edice Windows nebo konkrétní SKU, jako je například Home, Professional, Enterprise a školství.

Další informace o požadavcích na verzi a SKU pro různá nastavení najdete v referenčních informacích k [poskytovateli konfiguračních služeb (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Další kroky

Potřebujete další pomoc? Přečtěte si téma [Jak získat podporu pro Microsoft Intune](../fundamentals/get-support.md).