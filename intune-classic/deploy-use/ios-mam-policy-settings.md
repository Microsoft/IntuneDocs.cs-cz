---
title: "Nastavení zásad MAM pro iOS"
description: "Toto téma popisuje nastavení zásad správy mobilních aplikací pro zařízení s iOSem."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 384c3a8c930bf7ee8487726c37f1ff3652675650
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2017
---
#  <a name="ios-mobile-app-protection-policy-settings"></a>Nastavení zásad ochrany mobilních aplikací pro iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nastavení zásad popsané v tomto tématu se dá [nakonfigurovat](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) pro zásady ochrany aplikací v okně **Všechna nastavení** na portálu Azure Portal.

Existují dvě kategorie nastavení zásad:nastavení přemístění dat a nastavení přístupu. Termín _**aplikace spravované podle zásad**_ v tomto tématu označuje aplikace, které jsou konfigurované pomocí zásad ochrany aplikací.

##  <a name="data-relocation-settings"></a>Nastavení přemístění dat

| Nastavení | Způsob použití | Výchozí hodnota |
|------|------|------|
| **Zakázat zálohování dat v iTunes a na iCloudu** | Zvolte **Ano**, pokud chcete této aplikaci zabránit v zálohování pracovních nebo školních dat na iTunes a iCloud. Zvolte **Ne**, pokud chcete této aplikaci povolit zálohování pracovních nebo školních dat na iTunes a iCloud.| Ano |
| **Povolit aplikaci přenos dat do ostatních aplikací** | Určete, jaké aplikace můžou přijímat data z této aplikace: <ul><li> **Aplikace spravované podle zásad:** Povoluje přenos jenom do jiných aplikací spravovaných podle zásad.</li> <li>**Všechny aplikace**: Povoluje přenos do všech aplikací. </li> <li>**Žádné:** Nepovoluje přenos dat do žádné aplikace, včetně ostatních aplikací spravovaných podle zásad.</li></ul> Pokud nastavíte tuto možnost na hodnotu **Aplikace spravované podle zásad** nebo **Žádné**, bude blokovaná funkce iOS 9, která umožňuje vyhledávání Spotlight dat v rámci aplikací. <br><br> Do některých aplikací a služeb, které mají výjimku, může Intune povolit přenos dat. Úplný seznam takových aplikací a služeb najdete v části [Výjimky přenosu dat](#Data-transfer-exemptions). | Všechny aplikace |
| **Povolit aplikaci, aby přijímala data z jiných aplikací** | Určete, jaké aplikace můžou převádět data do této aplikace: <ul><li>**Aplikace spravované podle zásad:** Povoluje přenos jenom z jiných aplikací spravovaných podle zásad.</li><li>**Všechny aplikace**: Povoluje přenos dat ze všech aplikací.</li><li>**Žádné:** Nepovoluje přenos dat z žádné aplikace, včetně ostatních aplikací spravovaných podle zásad.</li></ul> Z některých aplikací a služeb, které mají výjimku, může Intune povolit přenos dat. Úplný seznam takových aplikací a služeb najdete v části [Výjimky přenosu dat](#Data-transfer-exemptions).  | Všechny aplikace |
| **Zakázat možnost Uložit jako** | Pokud chcete v této aplikaci zakázat možnost Uložit jako, zvolte **Ano**. Pokud chcete povolit použití možnosti Uložit jako, vyberte **Ne**. | Ne |
| **Omezit vyjmutí, kopírování a vkládání v ostatních aplikacích** | Určete, kdy se můžou v této aplikaci použít akce vyjmutí, kopírování a vložení. Vybírejte z těchto možností: <ul><li>**Blokováno:** Nepovoluje akce vyjmutí, kopírování a vložení mezi touto a jakoukoliv jinou aplikací.</li><li>**Aplikace spravované podle zásad:** Povoluje operace vyjmutí, kopírování a vložení mezi touto aplikací a jinými aplikacemi spravovanými podle zásad.</li><li>**Aplikace s vložením spravované podle zásad:** Povoluje vyjmutí a kopírování mezi touto aplikací a jinými aplikacemi spravovanými podle zásad. Povoluje vložení dat z jakékoliv aplikace do této aplikace.</li><li>**Libovolná aplikace:** Operace vyjmutí, kopírování a vložení do a z této aplikace nejsou nijak omezené. | Libovolná aplikace |
|**Omezit webový obsah tak, aby se spouštěl v Managed Browseru** | Pokud chcete vynutit, aby se webové odkazy v aplikaci otevíraly v aplikaci Managed Browser, zvolte **Ano**. <br><br> U zařízení, která nejsou zaregistrovaná v Intune, se webové odkazy v aplikacích spravovaných podle zásad můžou otevírat jenom v aplikaci Managed Browser. <br><br> Pokud ke správě zařízení používáte Intune, přečtěte si téma [Správa přístupu k internetu pomocí zásad spravovaného prohlížeče v Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | Ne |
| **Šifrovat data aplikace** | U aplikací spravovaných podle zásad se data šifrují v klidu pomocí schématu šifrování na úrovni zařízení poskytovaného iOSem. Když se vyžaduje PIN, data se zašifrují podle nastavení v zásadách ochrany aplikací. <br><br> Přejděte na oficiální dokumentaci společnosti Apple [tady](https://support.apple.com/HT202739) a podívejte se, které šifrovací moduly iOS jsou certifikované jako FIPS 140-2 nebo které na tuto certifikaci čekají. <br><br> Určete, kdy se budou šifrovat pracovní nebo školní data v této aplikaci. Vybírejte z těchto možností: <ul><li>**Když je zařízení blokované:** Všechna data aplikace přidružená k této zásadě jsou při uzamčení zařízení zašifrovaná.</li><li>**Když je zařízení uzamčené a existují otevřené soubory:** Všechna data aplikace přidružená k této zásadě jsou při uzamčení zařízení zašifrovaná, kromě dat v souborech, které jsou v aplikaci aktuálně otevřené.</li><li>**Po restartování zařízení:** Všechna data aplikace přidružená k této zásadě jsou při restartování zařízení zašifrovaná až do doby, než se zařízení poprvé odemkne.</li><li>**Použít nastavení zařízení:** Data aplikace se zašifrují podle výchozího nastavení v zařízení. </li></ul> Pokud povolíte toto nastavení, je možné, že si uživatel bude muset nastavit kód PIN a používat ho pro přístup k zařízení.  Pokud není PIN zařízení nastavený a vyžaduje se šifrování, aplikace se neotevře a uživateli se místo toho zobrazí zpráva, že jeho organizace vyžaduje, aby pro přístup k této aplikaci nejdřív povolil PIN zařízení.  | Když je zařízení blokované |
| **Zakázat synchronizaci kontaktů** | Pokud nechcete, aby aplikace ukládala data do nativní aplikace Kontakty na zařízení, zvolte **Ano**. Když zvolíte **Ne**, může aplikace ukládat data do nativní aplikace Kontakty na zařízení. <br><br>Když budete z aplikace selektivně mazat pracovní nebo školní data, odeberou se kontakty synchronizované přímo z aplikace do nativní aplikace Kontakty. Kontakty synchronizované z nativního adresáře do dalšího externího zdroje není možné vymazat. To se v současné době týká jenom aplikace Microsoft Outlook. | Ne |
| **Zakázat tisk** | Pokud chcete v aplikaci zakázat tisk pracovních nebo školních dat, zvolte **Ano**. | Ne |
| **Vyberte, do kterých služeb úložiště se můžou ukládat firemní data** | Uživatelé můžou ukládat data do vybraných služeb (OneDrive pro firmy, SharePoint a Místní úložiště). Všechny ostatní služby budou blokované. | Vybráno: 0 |

> [!NOTE]
> Žádné z nastavení přemístění dat na zařízeních s iOSem neřídí funkci otevírání v aplikaci spravované Applem. Pokud chcete spravovat funkci Otevřít v od Applu, přečtěte si [Správa přenosu dat mezi aplikacemi pro iOS pomocí Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

## <a name="data-transfer-exemptions"></a>Výjimky přenosu dat

U některých aplikací a služeb platformy, které mají výjimku, můžou zásady ochrany aplikací Intune v některých scénářích povolit přenos dat. Tento seznam se může měnit. Obsahuje služby a aplikace, které se považují za užitečné pro bezpečné a produktivní použití.

| Název aplikace nebo služby | Popis |
| ---- | --- |
|tel; telprompt | Nativní telefonní aplikace |
| skype | Skype |
| app-settings | Nastavení zařízení |
| itms; itmss; itms-apps; itms-appss; itms-services | App Store |
| calshow | Nativní kalendář |




## <a name="access-settings"></a>Nastavení přístupu

| Nastavení | Způsob použití | Výchozí hodnota |
|------|------|------|
| **Vyžadovat pro přístup kód PIN** | Zvolte **Ano**, aby se k použití této aplikace vyžadoval kód PIN. Uživateli se zobrazí výzva k nastavení tohoto kódu PIN při prvním spuštění aplikace v pracovním nebo školním kontextu. Výchozí hodnota = **Ano**<br><br> Sílu kódu PIN nakonfigurujete pomocí následujících nastavení: <ul><li>**Počet pokusů před resetem PIN kódu:** Zadejte počet pokusů, které uživatel bude mít k úspěšnému zadání PINu, než bude nutné PIN resetovat. Výchozí hodnota = **5**</li><li> **Povolit jednoduchý kód PIN:** Pokud chcete uživatelům povolit používání jednoduchých posloupností v kódu PIN, třeba 1234 nebo 1111, zvolte **Ano**. V případě, že nechcete, aby jednoduché posloupnosti používali, zvolte **Ne**. Výchozí hodnota = **Ano** </li><li> **Délka kódu PIN:** Zadejte minimální počet číslic v PINu. Výchozí hodnota = **4** </li><li> **Povolit otisk prstu místo PIN kódu (iOS 8.0+):** Zvolte **Ano**, pokud chcete uživateli ke zpřístupnění aplikace povolit použití [Touch ID](https://support.apple.com/HT201371) místo PINu. Výchozí hodnota = **Ano**</li></ul> Na zařízeních s iOSem můžete nechat uživatele prokazovat svoji identitu pomocí [Touch ID](https://support.apple.com/HT201371) namísto PINu. Když se uživatel pokusí použít tuto aplikaci se svým pracovním nebo školním účtem, zobrazí se výzva k zadání otisku prstu a uživatel nemusí zadávat kód PIN. Když je toto nastavení povolené, bude při používání pracovního nebo školního účtu obrázek náhledu v přepínači aplikací rozostřený. </li></ul>| Požadovat kód PIN: Ano <br><br> Počet pokusů před resetováním kódu PIN: 5 <br><br> Povolit jednoduchý PIN: Ano <br><br> Délka PINu: 4 <br><br> Povolit otisk prstu: Ano |
| **Vyžadovat podnikové přihlašovací údaje pro přístup** | Pokud chcete, aby se uživatel k získání přístupu k aplikaci přihlašoval pomocí svého pracovního nebo školního účtu namísto zadávání kódu PIN, zvolte **Ano**. Pokud nastavíte **Ano**, přepíše se tím požadavek na PIN nebo Touch ID.  | Ne |
| **Blokovat spuštění spravovaných aplikací na zařízeních s jailbreakem nebo rootem** |  Pokud chcete zabránit spuštění této aplikace v zařízeních s jailbreakem nebo rootem, zvolte **Ano**. Uživatel bude moct dál používat tuto aplikaci pro své osobní účely, ale k práci s pracovními nebo školními daty v této aplikaci bude muset používat jiné zařízení. | Ano |
| **Znovu zkontrolovat požadavky na přístup po (minuty)** | Proveďte konfiguraci následujících nastavení: <ul><li>**Časový limit:** Toto je počet minut před opakovaným zkontrolováním požadavků na přístup k aplikaci (definovaným dříve v zásadách). Správce například v zásadách zapne kód PIN, uživatel otevře aplikaci MAM a musí zadat PIN. Při použití tohoto nastavení nemusí uživatel u žádné aplikace MAM zadávat PIN dalších **30 minut** (výchozí hodnota).<br><br>K měření časového limitu požadavků na přístup se používá doba nečinnosti všech aplikací spravovaných podle těchto zásad.<br><br></li><li>**Období odkladu pro offline režim:** Toto je počet minut, po které může aplikace MAM běžet offline. Zadejte dobu (v minutách) před opakovaným zkontrolováním požadavků na přístup k aplikaci. Výchozí hodnota = **720** minut (12 hodin) Aby mohla aplikace po uplynutí této doby dál běžet, bude vyžadovat ověření uživatele ve službě AAD.</li></ul>| Časový limit: 30 <br><br> Offline: 720 |
| **Doba v offline režimu (ve dnech) před vymazáním dat** | Po tomto počtu dnů (definovaném správcem) běhu v offline režimu provede aplikace sama selektivní vymazání. Je to stejné selektivní vymazání, jaké může vyvolat správce v pracovním postupu vymazání MAM. <br><br> | 90 dnů |
| **Zakázat PIN kód aplikace, když je PIN kód zařízení spravovaný** | Pokud chcete zakázat PIN kód aplikace, když bude na zaregistrovaném zařízení zjištěn zámek zařízení, zvolte **Ano**. | Ne |
| **Vyžadovat minimální verzi operačního systému iOS** | Zvolte **Ano**, pokud k používání této aplikace vyžadujete minimální verzi operačního systému iOS. Uživateli bude zablokován přístup, pokud verze iOS v zařízení nesplňuje tento požadavek. | Ne |
| **Vyžadovat minimální verzi operačního systému iOS (jenom upozornění)** | Zvolte **Ano**, pokud k používání této aplikace vyžadujete minimální verzi operačního systému iOS. Uživateli se zobrazí oznámení, pokud verze iOS v zařízení nesplňuje tento požadavek. Toto oznámení je možné zavřít. | Ne |
| **Vyžadovat minimální verzi aplikace** | Zvolte **Ano**, pokud k používání této aplikace vyžadujete minimální verzi aplikace. Uživateli bude zablokován přístup, pokud verze aplikace v zařízení nesplňuje tento požadavek.<br><br>Při výběru cílových aplikací si prosím uvědomte, že aplikace mívají často odlišná schémata verzí.<br><br> | Ne | 
| **Vyžadovat minimální verzi aplikace (jenom upozornění)** | Zvolte **Ano**, pokud k používání této aplikace doporučujete minimální verzi aplikace. Uživateli se zobrazí oznámení, pokud verze aplikace v zařízení nesplňuje tento požadavek. Toto oznámení je možné zavřít.<br><br>Při výběru cílových aplikací si prosím uvědomte, že aplikace mívají často odlišná schémata verzí.<br><br> | Ne | 
| **Vyžadovat minimální verzi sady SDK zásad ochrany aplikací Intune** | Zvolte **Ano**, pokud požadujete, aby tato aplikace používala minimální verzi sady SDK zásad ochrany aplikací Intune. Uživateli bude zablokován přístup, pokud verze sady SDK zásad ochrany aplikací Intune nesplňuje tento požadavek. <br> <br> Další informace o sadě SDK zásad ochrany aplikací Intune najdete v článku [Přehled sady Intune App SDK](/intune/app-sdk). <br><br> | Ne |
##  <a name="add-ins-for-outlook-app"></a>Doplňky pro aplikaci Outlook

Poměrně čerstvou novinkou v Outlooku jsou doplňky pro iOS, které umožňují integrovat oblíbené aplikace s e-mailovým klientem. Doplňky pro Outlook jsou k dispozici na webu, v systému Windows, na Macu a v Outlooku pro iOS. Vzhledem k tomu, že se doplňky spravují přes Microsoft Exchange, budou uživatelé moct sdílet data a zprávy v rámci Outlooku a nespravovaných aplikací doplňků (pokud nemají doplňky vypnuté na Exchangi).

Pokud chcete svým koncovým uživatelům používání a instalaci doplňků Outlooku zakázat (bude to mít vliv na všechny klienty Outlooku), musíte v rolích v Centru pro správu Exchange provést následující změny:

- Pokud chcete uživatelům zabránit v instalaci doplňků z Office Storu, odeberte jim roli My Marketplace (Moje tržiště).
- Pokud chcete uživatelům zabránit v instalaci doplňků bokem (mimo Store), odeberte jim roli My Custom Apps (Moje vlastní aplikace).
- Pokud chcete uživatelům zabránit v instalaci všech doplňků, odeberte jim jak roli My Custom Apps, tak roli My Marketplace.

Tyto pokyny platí pro Office 365, Exchange 2016, Exchange 2013, a to jak v Outlooku na webu, tak také v jeho verzích pro Windows, Mac a mobilní zařízení.

- Další informace o [doplňcích pro Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Přečtěte si další informace o tom [jak určit, kteří správci a uživatelé můžou instalovat a spravovat doplňky pro aplikaci Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).