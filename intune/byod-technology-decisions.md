---
title: "Rozhodnutí o technologiích pro používání vlastních zařízení uživatelů (BYOD) pomocí řešení EMS"
description: "Klíčová rozhodnutí o technologiích, která umožní používání vlastních zařízení uživatelů (BYOD) a ochranu firemních dat, pomocí řešení Microsoft Enterprise Mobility + Security"
keywords: 
author: 
ms.author: pfetty
manager: angrobe
ms.date: 12/8/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.openlocfilehash: a0b5f170c10cff189a269b29ffc466bd2d51ed12
ms.sourcegitcommit: a99a5104400708b47ecee80075264d541b82874f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Rozhodnutí o technologiích, která umožní používání vlastních zařízení uživatelů (BYOD), pomocí řešení Microsoft Enterprise Mobility + Security (EMS)

Při vývoji strategie umožňující vzdálenou práci zaměstnanců na vlastních zařízeních (BYOD) je potřeba udělat ve scénářích klíčová rozhodnutí, která umožní používání vlastních zařízení uživatelů a určí způsob ochrany firemních dat. Řešení EMS naštěstí nabízí všechny potřebné funkce jako komplexní sadu řešení.  

V tomto tématu prozkoumáme jednoduchý případ použití, ve kterém se povoluje přístup pomocí vlastních zařízení uživatelů k podnikovému e-mailu. Zaměříme se na to, jestli je potřeba spravovat celé zařízení nebo jenom aplikace, přičemž obě tyto možnosti jsou přípustné.

## <a name="assumptions"></a>Předpoklady
* Máte základní znalosti o Azure Active Directory a Microsoft Intune.
* Vaše e-mailové účty jsou hostované v Exchangi Online.

## <a name="common-reasons-to-manage-the-device-mdm"></a>Běžné situace, při kterých se provádí správa zařízení (MDM)
Nasazením zásad [podmíněného přístupu](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) na Exchangi Online můžete uživatele snadno přimět, aby si svoje zařízení zaregistrovali do správy zařízení. Toto jsou situace, kdy je vhodné spravovat osobní zařízení:

**WiFi/VPN** – Pokud uživatelé potřebují k produktivní práci podnikový profil připojení, je možné ho bezproblémově nakonfigurovat.

**Aplikace** – Pokud uživatelé potřebují do svého zařízení bez vyžádání stáhnout sadu aplikací, je možné je bezproblémově doručit. To zahrnuje i aplikace, které se můžou vyžadovat pro účely zabezpečení, jako je například aplikace pro ochranu před mobilními hrozbami.

**Dodržování předpisů** – Některé organizace musí dodržovat zákonné nebo jiné předpisy, které vyžadují specifické prvky MDM. MDM je například potřeba k šifrování celého zařízení nebo k vytvoření sestavy obsahující všechny aplikace na zařízení.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Běžné situace, při kterých se provádí jenom správa aplikací (MAM)
Používání MAM bez MDM je velmi rozšířené v organizacích, které podporují vlastní zařízení uživatelů. Nasazením zásad podmíněného přístupu na Exchangi Online můžete uživatele přimět, aby pro přístup k e-mailu používali Outlook Mobile (který podporuje ochranu MAM). Toto jsou situace, kdy je vhodné spravovat jenom aplikace na osobních zařízeních:

**Uživatelské prostředí** – Součástí registrace MDM je řada výzev s upozorněními (vynucovaných příslušnou platformou), které často mají za následek to, že se uživatel nakonec rozhodne nepřistupovat k e-mailu na svém osobním zařízení. Prostředí MAM není pro uživatele tak znepokojující, protože se jim zobrazí jenom jedno automaticky otevírané okno s oznámením, že se používá ochrana MAM.

**Dodržování předpisů** – Některé organizace musí dodržovat předpisy, které vyžadují, aby na osobních zařízeních bylo méně funkcí pro správu. MAM například umožňuje odebrat firemní data jenom z aplikací, na rozdíl od správy MDM, která umožňuje odebrat všechna data ze zařízení.

![Obrázek s porovnáním správy zařízení a aplikací na mobilních zařízeních](./media/byod-app-device-mgmt.png)

Přečtěte si další informace o [životních cyklech správy zařízení a aplikací](introduction-device-app-lifecycles.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Porovnání funkcí MDM a MAM
Jak jsme už uvedli, pomocí podmíněného přístupu lze uživatele přimět k tomu, aby si svoje zařízení zaregistroval nebo aby používal spravovanou aplikaci, jako je Outlook Mobile. V obou případech lze použít řadu dalších podmínek, například:

* Uživatel, který se pokouší o přístup
* Důvěryhodnost nebo nedůvěryhodnost umístění
*   Úroveň rizika přihlášení
* Platforma zařízení

Řada organizací má ještě často specifická rizika, kterými se musí zabývat.  Následující tabulka obsahuje běžné problémy a reakce MDM a MAM na tyto problémy.

| Problém   |   MDM  |   MAM  |
|------------|--------|--------|
|Neoprávněný přístup k datům | Vyžadování členství ve skupině | Vyžadování členství ve skupině |
|Neoprávněný přístup k datům | Vyžadování registrace zařízení | Vyžadování chráněné aplikace |
|Neoprávněný přístup k datům | Vyžadování konkrétního umístění | Vyžadování konkrétního umístění |
| | | |
|Ohrožení bezpečnosti uživatelského účtu| Vyžadování MFA | Vyžadování MFA|
|Ohrožení bezpečnosti uživatelského účtu | Blokování uživatelů s vysokým rizikem | Blokování uživatelů s vysokým rizikem |
|Ohrožení bezpečnosti uživatelského účtu | PIN kód zařízení | PIN kód aplikace |
| | | |
| Ohrožení bezpečnosti zařízení nebo aplikace | Vyžadování kompatibilního zařízení | Detekce jailbreaku při spuštění aplikace |
| Ohrožení bezpečnosti zařízení nebo aplikace | Zašifrování dat na zařízení | Zašifrovat data aplikací |
| | | |
|Ztráta nebo odcizení zařízení | Odebrání všech dat na zařízení | Odebrání všech dat aplikací|
| | | |
| Nechtěné sdílení dat nebo uložení do nezabezpečených umístění | Zakázání zálohování dat na zařízení | Zakázání funkcí Vyjmout, Kopírovat a Vložit|
| Nechtěné sdílení dat nebo uložení do nezabezpečených umístění | Zakázání funkce Uložit jako | Zakázání funkce Uložit jako |
|Nechtěné sdílení dat nebo uložení do nezabezpečených umístění | Zakázat tisk | není k dispozici|

## <a name="next-steps"></a>Další kroky
Teď je čas na rozhodnutí, jestli se ve vaší organizaci při povolování vlastních zařízení uživatelů (BYOD) zaměříte na správu zařízení, na správu aplikací nebo na kombinaci obou možností. Volba implementace je na vás, ale bez ohledu na zvolenou možnost máte jistotu, že budete mít k dispozici funkce pro práci s identitami a funkce zabezpečení, které jsou dostupné v Azure AD.

K navržení další úrovně plánování použijte [průvodce plánováním](planning-guide.md) Intune.