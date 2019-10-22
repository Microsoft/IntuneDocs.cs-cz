---
title: Přehled zásad ochrany aplikací
titleSuffix: Microsoft Intune
description: Zjistěte, jak zásady ochrany aplikací Microsoft Intune pomáhají chránit firemní data a bránit únikům informací.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bb0e2ff4379c55829afc65fb99b768c9099a47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498952"
---
# <a name="app-protection-policies-overview"></a>Přehled zásad ochrany aplikací

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Zásady ochrany aplikací (aplikace) jsou pravidla, která zajistí, že data organizace zůstanou v bezpečí nebo jsou obsažená ve spravované aplikaci. Zásada může být pravidlo, které je vynuceno, když se uživatel pokusí pracovat s firemními daty nebo je přesunout, nebo sada akcí, které jsou zakázané nebo monitorované, pokud je uživatel uvnitř aplikace. Spravovaná aplikace je taková aplikace, která využívá zásady ochrany aplikací a která lze spravovat pomocí Intune.

Zásady ochrany aplikací pro správu mobilních aplikací (MAM) umožňují spravovat a chránit data vaší organizace v rámci aplikace. S **mam bez registrace** (MAM-We) je možné spravovat pracovní nebo školní aplikaci, která obsahuje citlivá data, a to téměř na jakémkoli [zařízení](app-management.md#app-management-capabilities-by-platform), včetně osobních zařízení ve scénářích **Přineste si vlastní zařízení** (BYOD). Mnoho kancelářských aplikací, například aplikace Microsoft Office, lze spravovat přes Intune MAM. Podívejte se na oficiální seznam [Microsoft Intune chráněných aplikací](apps-supported-intune-apps.md) , které jsou k dispozici pro veřejné použití.

## <a name="how-you-can-protect-app-data"></a>Způsob ochrany dat aplikací
Vaši zaměstnanci používají mobilní zařízení pro osobní a pracovní úkoly. Chcete, aby vaši zaměstnanci byli produktivní, ale chcete zabránit případným záměrným či neúmyslným ztrátám dat. Budete také chtít chránit firemní data, s kterými se pracuje ze zařízení, která nespravujete.

Můžete použít zásady ochrany aplikací Intune **nezávisle na řešení správy mobilních zařízení (MDM)** . Tato nezávislost vám pomůže s ochranou dat vaší společnosti, ať už budou zařízení registrovaná v řešení pro správu zařízení nebo ne. Implementací **zásad na úrovni aplikace** můžete omezit přístup k prostředkům společnosti a ponechat data v kompetenci IT oddělení.

### <a name="app-protection-policies-on-devices"></a>Zásady ochrany aplikací na zařízeních

Zásady ochrany aplikací lze konfigurovat pro aplikace běžící na zařízeních, která jsou:

- **Zaregistrovaná v Microsoft Intune:** Tato zařízení jsou obvykle vlastněná společností.

- **Zaregistrovaná v rámci řešení pro správu mobilních zařízení (MDM) třetích stran:** Tato zařízení jsou obvykle vlastněná společností.

  > [!NOTE]
  > Zásady správy mobilních aplikací není vhodné používat s řešeními pro správu mobilních aplikací třetích stran nebo zabezpečeného kontejneru.

- **Není zaregistrované v žádném řešení pro správu mobilních zařízení:** Tato zařízení jsou obvykle zařízení vlastněná zaměstnanci, která nejsou spravovaná ani zaregistrovaná v Intune nebo jiných řešeních MDM.

> [!IMPORTANT]
> Můžete vytvářet zásady správy mobilních aplikací pro mobilní aplikace Office, které se připojují ke službám Office 365. Přístup k místním poštovním schránkám Exchange můžete chránit také tak, že vytvoříte zásady ochrany aplikací Intune pro Outlook pro iOS a Android s hybridním moderním ověřováním. Ještě než začnete tuto funkci využívat, zkontrolujte, že splňujete [požadavky na Outlook pro iOS a Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Zásady ochrany aplikací se nepodporují pro jiné aplikace, které se připojují k místním službám Exchange nebo SharePoint.

## <a name="benefits-of-using-app-protection-policies"></a>Výhody používání zásad ochrany aplikací

Mezi důležité výhody použití zásad ochrany aplikací patří následující:

- **Ochrana firemních dat na úrovni aplikace.** Protože správa mobilních aplikací nevyžaduje správu zařízení, můžete podniková data chránit na spravovaných i nespravovaných zařízeních. Správa je zaměřená na identitu uživatele, odpadá tedy požadavek na správu zařízení.

- **Produktivita koncového uživatele není ovlivněná a zásady se při použití aplikace v osobním kontextu nepoužijí.** Zásady se použijí jenom v pracovním kontextu, což umožňuje chránit podniková data bez zásahu do osobních dat.

- **Zásady ochrany aplikací zajišťují, že jsou zavedena ochrana aplikační vrstvy.** Můžete například:
  - Vyžadovat PIN k otevření aplikace v pracovním kontextu 
  - Řídit sdílení dat mezi aplikacemi 
  - Zabránit ukládání dat firemních aplikací do osobního úložiště

- **MDM kromě mam zajišťuje ochranu zařízení**. Můžete například přístup do zařízení zabezpečit kódem PIN nebo do zařízení nasadit spravované aplikace. Do zařízení můžete aplikace nasadit také pomocí řešení MDM, čímž získáte větší kontrolu nad správou aplikací.

Použití správy mobilních zařízení se zásadami ochrany aplikací přináší další výhody, přičemž firmy můžou zásady ochrany aplikací využívat najednou se správou mobilních zařízení i bez. Představte si třeba zaměstnance, který používá firemní telefon i vlastní tablet. Firemní telefon je zaregistrovaný ve správě mobilních zařízení a chráněný zásadami ochrany aplikací, zatímco vlastní zařízení je chráněné jen zásadami ochrany aplikací.

Pokud pro uživatele použijete zásadu MAM bez nastavení stavu zařízení, uživatel získá zásadu MAM na zařízení BYOD i na zařízení spravovaném přes Intune. Můžete také použít zásadu MAM založenou na spravovaném stavu. Takže když vytvoříte zásady ochrany aplikací, zobrazí se vedle **cíle u všech typů aplikací**možnost **ne**. Pak proveďte některou z následujících akcí:
- Použijte pro zařízení spravovaná přes Intune méně přísné zásady MAM a použijte pro zařízení zaregistrovaná v MDM více omezující zásadu MAM.
- Použije zásady MAM jenom pro odregistrovaná zařízení.

## <a name="supported-platforms-for-app-protection-policies"></a>Podporované platformy pro zásady ochrany aplikací

Intune nabízí celou řadu funkcí, které vám pomůžou dostat požadované aplikace na zařízení, na kterých je chcete spouštět. Další informace najdete v tématu [Možnosti správy aplikací podle platformy](app-management.md#app-management-capabilities-by-platform).

Podpora platforem zásad ochrany aplikací Intune se zarovnává s podporou platformy mobilních aplikací Office pro zařízení s Androidem a iOS. Podrobnosti najdete v části **Mobilní aplikace** článku [Požadavky na systém pro Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Na zařízení se vyžaduje Portál společnosti Intune pro příjem zásad ochrany aplikací na Androidu. Další informace najdete v tématu [požadavky aplikace Portál společnosti Intune Access](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Jak zásady ochrany aplikací chrání data aplikací

### <a name="apps-without-app-protection-policies"></a>Aplikace bez zásad ochrany aplikací

Pokud se aplikace používají bez omezení, můžou se osobní a firemní data prolínat. Firemní data můžou být uložená v osobním úložišti nebo přenesená do aplikací mimo váš dosah, a může tím dojít ke ztrátě dat. Šipky v následujícím diagramu znázorňují neomezený pohyb dat mezi podnikovými a osobními aplikacemi a umístěními úložiště.

![Koncepční obrázek pro pohyb dat mezi aplikacemi bez jakýchkoli zásad](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Ochrana dat pomocí zásad ochrany aplikací (aplikace)

Pomocí zásad ochrany aplikací můžete zabránit ukládání firemních dat do místního úložiště zařízení (viz obrázek níže). Můžete také zamezit přesunu dat do jiných aplikací, které nejsou chráněné zásadami ochrany aplikací. Mezi nastavení zásad ochrany aplikací patří:
- Zásady přemístění dat, jako například **zabránit uložení jako**, a **Omezit vyjmutí, zkopírování a vložení**.
- Nastavení zásad přístupu, jako jsou **Vyžadovat pro přístup jednoduchý PIN kód** a **Blokovat spouštění spravovaných aplikací na zařízeních s jailbreakem nebo rootem**.

![Koncepční bitová kopie, která zobrazuje firemní data chráněná zásadami](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Ochrana dat pomocí aplikace na zařízeních spravovaných řešením MDM

Následující ilustrace znázorňuje vrstvy ochrany, které zásady ochrany MDM a ochrany aplikací nabízejí dohromady.

![Obrázek, který znázorňuje, jak zásady ochrany aplikací fungují na vlastních zařízeních uživatelů (BYOD)](./media/app-protection-policy/app-protection-policies-with-mdm.png)

Řešení MDM zvyšuje hodnotu tím, že poskytuje následující:

- Zaregistruje zařízení.
- Na zařízení nasadí aplikace.
- Zajišťuje neustálé dodržování předpisů a správu zařízení.

Zásady ochrany aplikací přidávají hodnotu tím, že poskytuje následující:

- Ochrana před únikem firemních dat do uživatelských aplikací a služeb
- Použití omezení jako *Save-as*, *Clipboard*nebo *PIN*pro klientské aplikace
- V případě potřeby vymazat firemní data z aplikací bez odebrání těchto aplikací ze zařízení

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Ochrana dat pomocí aplikace pro zařízení bez registrace

Následující diagram znázorňuje, jak fungují zásady ochrany dat na úrovni aplikace bez správy mobilních zařízení (MDM).

![Obrázek, který ukazuje, jak zásady ochrany aplikací fungují na zařízeních bez registrace (nespravovaná zařízení)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

U vlastních zařízení uživatelů nezaregistrovaných do řešení MDM můžou zásady ochrany aplikací pomoci chránit firemní data na úrovni aplikace.
Existují však určitá omezení, o kterých byste měli vědět, například:

- Aplikace nejde do zařízení nasadit. Koncový uživatel musí aplikace sám nainstalovat.
- V těchto zařízeních nejde zřídit profily certifikátů.
- V těchto zařízeních nejde zřídit firemní Wi-Fi a nastavit VPN.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Aplikace, které se dají spravovat pomocí zásad ochrany aplikací

Zásadami ochrany aplikací Intune se dá spravovat každá aplikace integrovaná sadou [Intune App SDK](../developer/app-sdk.md) nebo zabalená nástrojem [Intune App Wrapping](../developer/apps-prepare-mobile-application-management.md). Podívejte se na oficiální seznam [Microsoft Intune chráněných aplikací](apps-supported-intune-apps.md) , které jsou sestavené pomocí těchto nástrojů a jsou k dispozici pro veřejné použití.

Vývojový tým sady Intune SDK aktivně testuje a udržuje podporu pro aplikace vytvořené s nativními platformami Android, iOS (obj-C, SWIFT), Xamarin, Xamarin. Forms a Cordova. I když se někteří zákazníci dokončí s integrací sady Intune SDK s jinými platformami, jako je například reakce nativních a NativeScript, neposkytujeme explicitní pokyny ani moduly plug-in pro vývojáře aplikací, kteří používají jinou než naše podporované platformy.

[Sada Intune App SDK](../developer/app-sdk.md) používá některé pokročilé možnosti moderního ověřování z[knihoven Azure Active Directory Authentication](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) Library (ADAL) pro obě verze sady SDK od druhé strany. [Knihovna Microsoft Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) ale nefunguje dobře s mnoha našimi základními scénáři, jako je například ověřování do služby Intune App Protection a podmíněné spuštění. Vzhledem k tomu, že celkový návod od týmu identity společnosti Microsoft je přepnout na MSAL pro všechny systém Microsoft Office aplikace, [sada Intune App SDK](../developer/app-sdk.md) ji bude nakonec potřebovat k jejímu podpoře, ale ještě neexistují žádné plány.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Požadavky koncových uživatelů na používání zásad ochrany aplikací

Následující seznam uvádí požadavky koncových uživatelů na používání zásad ochrany aplikací v aplikaci spravované přes Intune:

- Koncový uživatel musí mít účet Azure Active Directory (AAD). Pokud se chcete dozvědět, jak se vytvářejí uživatelé Intune v Azure Active Directory, přečtěte si [Přidání uživatelů a udělení oprávnění pro správu v Intune](../fundamentals/users-add.md).

- Koncový uživatel musí mít ke svému účtu Azure Active Directory přiřazenou licenci pro Microsoft Intune. Informace o tom, jak se přiřazují licence Intune koncovým uživatelům, najdete v článku [Správa licencí Intune](../fundamentals/licenses-assign.md).

- Koncový uživatel musí patřit do skupiny zabezpečení, která je cílem zásady ochrany aplikace. Stejná zásada ochrany aplikace musí mít za cíl konkrétní používanou aplikaci. Zásady ochrany aplikací se dají vytvářet a nasazovat v konzole Intune na [portálu Azure](https://portal.azure.com). Skupiny zabezpečení se teď dají vytvořit v [centru pro správu Microsoft 365](https://admin.microsoft.com).

- Koncový uživatel se musí do aplikace přihlásit pomocí svého účtu AAD.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Zásady ochrany aplikací pro aplikace systém Microsoft Office

K dispozici je několik dalších požadavků, které byste měli znát při používání zásad ochrany aplikací s systém Microsoft Office aplikacemi.

### <a name="outlook-mobile-app"></a>Mobilní aplikace Outlook
Další požadavky na používání [mobilní aplikace Outlooku](https://products.office.com/outlook) jsou následující:

- Koncový uživatel musí mít v zařízení nainstalovanou mobilní aplikaci Outlook.
- Koncový uživatel musí mít poštovní schránku [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) a licenci propojenou se svým účtem Azure Active Directory.

  >[!NOTE]
  > Mobilní aplikace Outlook aktuálně podporuje pouze Intune App Protection pro Microsoft Exchange Online a [Exchange Server s hybridním moderním ověřováním](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) a nepodporuje Exchange v Office 365 Dedicated.

### <a name="word-excel-and-powerpoint"></a>Word, Excel a PowerPoint
Mezi další požadavky na používání aplikací pro [Word, Excel a PowerPoint](https://products.office.com/business/office) patří následující:

- Koncový uživatel musí mít licenci pro [Office 365 Business nebo Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) propojenou se svým účtem Azure Active Directory. Předplatné musí obsahovat aplikace Office na mobilních zařízeních a může obsahovat účet pro ukládání do cloudu přes [OneDrive pro firmy](https://onedrive.live.com/about/business/). Licence na Office 365 se dají přiřadit v [centru pro správu Microsoft 365](https://admin.microsoft.com) podle těchto [pokynů](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- Koncový uživatel musí mít spravované umístění nakonfigurované pomocí podrobné funkce Uložit jako v nastavení zásad ochrany aplikace Zakázat možnost Uložit jako. Pokud je spravovaným umístěním třeba OneDrive, musí být v aplikaci Word, Excel nebo PowerPoint koncového uživatele nakonfigurovaná aplikace [OneDrive](https://onedrive.live.com/about/).

- Pokud je spravovaným umístěním OneDrive, musí být aplikace cílem pro zásadu ochrany aplikace nasazenou pro koncového uživatele.

  >[!NOTE]
  > Mobilní aplikace Office aktuálně podporují jenom SharePoint Online a ne místní SharePoint.

### <a name="managed-location-needed-for-office"></a>Spravované umístění, které je potřeba pro Office
Spravované umístění (tj. OneDrive), které je potřeba pro Office. Intune označí všechna data v aplikaci buď jako firemní, nebo jako osobní. Data se považují za podniková, když pocházejí z firemního umístění. U aplikací Office považuje Intune za firemní následující umístění: e-mail (Exchange) nebo cloudové úložiště (aplikace OneDrive s účtem OneDrive pro firmy).

### <a name="skype-for-business"></a>Skype pro firmy
Existují další požadavky na používání Skypu pro firmy. Viz licenční požadavky [Skypu pro firmy](https://products.office.com/skype-for-business/it-pros). Informace o hybridních a místních konfiguracích Skypu pro firmy najdete v článcích [Hybridní moderní ověřování pro Skype pro firmy a Exchange bude všeobecně dostupné](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) a [Moderní ověřování pro Skype pro firmy v místním prostředí s AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910).

## <a name="app-protection-global-policy"></a>Globální zásada ochrany aplikací

Když správce OneDrivu přejde na web **admin.office.com** a vybere **Zařízení**, může nastavit ovládací prvky **správy mobilních aplikací** pro klientské aplikace OneDrivu a SharePointu. 

V tomto nastavení, které je přístupné na konzole pro správu OneDrivu, může nakonfigurovat speciální **globální** zásadu ochrany aplikací v Intune. Tato globální zásada se dá použít pro všechny uživatele v tenantovi, ale nedovoluje řídit adresování zásad. 

Jakmile ji zapnete, jsou aplikace OneDrivu a SharePointu pro iOS a Android automaticky chráněné vybraným nastavením. Odborník na IT může tuto zásadu upravit v konzole Intune, kde může přidat další cílové aplikace a změnit její nastavení. 

Implicitně smí existovat jenom jedna **globální** zásada pro tenanta. K vytvoření dalších globálních zásad pro tenanta je však možné použít [rozhraní Graph API v Intune](../developer/intune-graph-apis.md). Tento postup se ale nedoporučuje. Vytvoření dalších globálních zásad se nedoporučuje kvůli možným komplikacím při řešení potíží s implementací této zásady.

**Globální** zásada sice platí pro všechny uživatele v tenantovi, ale každá standardní zásada ochrany aplikací v Intune toto nastavení přepíše.

## <a name="app-protection-features"></a>Funkce ochrany aplikací

### <a name="multi-identity"></a>Víc identit

Podpora více identit umožňuje aplikaci podporovat více cílových skupin. Tyto cílové skupiny jsou "firemní" uživatelé i "osobní" uživatelé. Pracovní a školní účty používají podnikové publikum, zatímco osobní účty se použijí pro cílové skupiny uživatelů, například systém Microsoft Office uživatelé. Aplikaci, která podporuje více identit, se dá veřejně vydat, kde se zásady ochrany aplikací použijí jenom v případě, že se aplikace používá v kontextu Work a School ("Corporate"). Podpora více identit používá [sadu Intune App SDK](../developer/app-sdk.md) k nastavení zásad ochrany aplikací jenom na pracovní nebo školní účet přihlášený k aplikaci. Pokud se k aplikaci přihlásí osobní účet, zůstanou data nedotčená.

Pro příklad osobního kontextu zvažte, že uživatel, který spustí nový dokument ve Wordu, se považuje za osobní, takže Intune App Protection zásady se neuplatní. Až se dokument uloží na účet "Corporate", bude se považovat za "podnikový" kontext a použijí se zásady Intune App Protection.

Příklad práce nebo "firemní" kontext vám může nabídnout uživatele, který spustí aplikaci OneDrive pomocí svého pracovního účtu. V pracovním kontextu nemůže přesunout soubory do svého osobního úložiště. Pokud ale později uživatel použije OneDrive se svým osobním účtem, může kopírovat a přesouvat data ze svého osobního OneDrivu bez omezení.

Outlook obsahuje souhrnné zobrazení e-mailů osobních i firemních e-mailů. V této situaci aplikace Outlook při spuštění vyzve k zadání kódu PIN služby Intune.

Další informace o více identitách v Intune najdete v tématu [mam a multi-identity](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>PIN kód aplikace Intune

Osobní identifikační číslo (PIN) je heslo, kterým se ověřuje, že s daty organizace pracuje v aplikaci správný uživatel.

**Výzva k zadání kódu PIN**<br>
Intune vyzve uživatele k zadání PINu aplikace, když se uživatel chystá pracovat s podnikovými daty. V aplikacích s více identitami, jako je Word, Excel nebo PowerPoint, se uživateli zobrazí výzva k zadání PIN kódu při pokusu o otevření firemního dokumentu nebo souboru. V aplikacích s jedinou identitou, jako jsou obchodní aplikace spravované pomocí [Nástroje pro zabalení aplikace Intune](../developer/apps-prepare-mobile-application-management.md), se PIN kód zobrazí při spuštění, protože [sada Intune App SDK](../developer/app-sdk.md) ví, že se uživatelské prostředí v aplikaci vždycky zobrazuje jako "Podniková".

**Frekvence výzvy k zadání kódu PIN**<br>
Správce IT může v konzole pro správu Intune definovat nastavení zásad ochrany aplikací Intune znovu **ověřit požadavky na přístup po (minuty)** . Toto nastavení určuje dobu, než se v zařízení zkontrolují požadavky na přístup a znovu se zobrazí obrazovka pro kód PIN aplikace. Četnost, s jakou se budou uživateli zobrazovat výzvy, ale ovlivňují důležité detaily týkající se kódu PIN:

- **PIN kód se sdílí mezi aplikacemi stejného vydavatele, aby se zlepšila použitelnost:**<br> V systému iOS je jeden PIN kód aplikace sdílený mezi všemi aplikacemi **stejného vydavatele aplikace**. V Androidu se kód PIN jedné aplikace sdílí mezi všemi aplikacemi.
  - **Po restartování zařízení *znovu ověřit chování požadavků na přístup po (minuty)* :**<br> "Časovač kódu PIN" sleduje počet minut nečinnosti, které určují, kdy se má zobrazit kód PIN aplikace Intune. V systému iOS nemá restart zařízení na časovač kódu PIN vliv. Proto restart zařízení nemá vliv na počet minut, během kterých byl uživatel v aplikaci pro iOS se zásadou pro PIN nečinný. V systému Android restartování zařízení časovač kódu PIN vynuluje. Proto aplikace pro Android se zásadou pro PIN budou pravděpodobně **po restartu zařízení** vyžadovat PIN aplikace bez ohledu na hodnotu nastavení „Překontrolovat požadavky na přístup za (minuty)“.  
  - **Kumulovaná povaha časovače přidruženého k PIN kódu:**<br> Po zadání kódu PIN pro přístup k aplikaci (App A) a aplikace opustí na zařízení popředí (hlavní vstupní fokus), časovač PIN kódu pro tento PIN kód se obnoví. Jakákoli aplikace (aplikace B), která tento kód PIN sdílí, nevyzve uživatele k jeho zadání, protože časovač se vynuloval. Tato výzva se zobrazí znovu, jakmile je opět splněna hodnota nastavení Překontrolovat požadavky na přístup za (minuty).

Na zařízeních s iOSem platí, že i když stejný PIN používají aplikace od různých vydavatelů, zobrazí se výzva znovu po splnění hodnoty nastavení **Znovu zkontrolovat požadavky na přístup po (minuty)** u aplikace, která se nenachází v hlavním fokusu. Představte si například, že má uživatel aplikaci _A_ od vydavatele _X_ a aplikaci _B_ od vydavatele _Y_ a na obou se používá stejný PIN. Uživatel se zaměřuje na aplikaci _A_ (popředí), aplikace _B_ se minimalizuje. Když se splní hodnota **Znovu zkontrolovat požadavky na přístup po (minuty)** a uživatel přepne na aplikaci _B_, bude vyžadován PIN.

  >[!NOTE]
  > Kvůli častějšímu ověřování požadavků na přístup uživatele (například výzvy k zadání PINu) doporučujeme zmenšit hodnotu nastavení Překontrolovat požadavky na přístup za (minuty), a to především u často používaných aplikací.

**Předdefinované PIN kódy aplikací pro Outlook a OneDrive**<br>
PIN kód Intune funguje na základě časovače založeného na nečinnosti (hodnota **překontrolovat požadavky na přístup po (minuty)** ). Proto se výzvy PIN kódu Intune zobrazují nezávisle na výzvách integrovaných PIN kódů aplikace pro Outlook a OneDrive, které jsou většinou ve výchozím nastavení svázané se spuštěním aplikace. Pokud se uživateli zobrazí obě výzvy PIN kódu najednou, měl by mít přednost PIN kód Intune.

**Zabezpečení kódu PIN pro Intune**<br>
PIN slouží k tomu, aby v aplikaci povolil pracovat s daty organizace jenom správnému uživateli. Proto se koncový uživatel musí přihlásit s pracovním nebo školním účtem, aby si mohl nastavit nebo resetovat PIN pro aplikaci Intune. Toto ověřování zpracovává Azure Active Directory přes zabezpečený token Exchange a není transparentní pro [Intune App SDK](../developer/app-sdk.md). Z hlediska zabezpečení je nejlepší ochranou pracovních nebo školních dat jejich šifrování. Šifrování nesouvisí s PINem aplikace, ale jde o vlastní zásadu ochrany aplikace.

**Intune PIN – ochrana proti útokům hrubou silou**<br>
Jako součást zásady pro PIN aplikace může správce IT nastavit maximální počet pokusů, které uživatel má k ověření PINu před uzamčením aplikace. Po dosažení počtu pokusů může [sada Intune App SDK](../developer/app-sdk.md) vymazat podniková data v aplikaci.
  
**Nastavujete PIN kód dvakrát u aplikací od stejného vydavatele?**<br>
MAM (v iOS) aktuálně povoluje PIN kód na úrovni aplikace s alfanumerickými a speciálními znaky (s názvem "heslo"), které vyžadují účast aplikací (například WXP, Outlook, Managed Browser, Yammer) pro integraci [sady Intune App SDK pro iOS](../developer/app-sdk-ios.md). Bez toho se nastavení hesla pro cílové aplikace správně nevynutí. Tato funkce byla vydána v Intune SDK pro iOS verze 7.1.12.

Aby mohla být tato funkce podporována a byla zajištěna zpětná kompatibilita s předchozími verzemi sady Intune SDK pro iOS, budou se všechny kódy PIN (číselné nebo v podobě hesla) od verze 7.1.12 zpracovávat odděleně od číselných kódů PIN používaných v předchozích verzích SDK. Pokud jsou v zařízení aplikace od stejného vydavatele, které používají sadu Intune SDK pro iOS ve verzích před 7.1.12 A SOUČASNĚ po 7.1.12, bude potřeba nastavit dva kódy PIN. Tyto dva kódy PIN (pro každou aplikaci) nijak nesouvisejí (to znamená, že musí dodržovat zásady ochrany aplikací, které se pro aplikaci používají). V takovém případě může uživatel nastavit stejný kód PIN dvakrát, *pouze* Pokud aplikace a a B používají stejné zásady (s ohledem na PIN kód). 

Uvedené chování je specifické pro PIN aplikací pro iOS povolených ve správě mobilních aplikací v Intune. Jak si budou aplikace postupně osvojovat novější verze sady Intune SDK pro iOS, přestane být dvojí nastavování kódu PIN u aplikací od stejného vydavatele takový problém. V následující poznámce uvádíme příklad.

  >[!NOTE]
  > Pokud k vytvoření aplikace A byla použita verze před 7.1.12 a k vytvoření aplikace B od stejného vydavatele byla použita verze vyšší nebo rovna 7.1.12, musí koncový uživatel nastavit PIN zvlášť pro aplikaci A i B, pokud jsou na zařízení s iOSem nainstalované obě aplikace.
  > Pokud je v zařízení nainstalovaná aplikace C, která má sadu SDK verze 7.1.9, bude sdílet stejný kód PIN jako aplikace A. Aplikace sestavená pomocí 7.1.14 bude sdílet stejný kód PIN jako aplikace B.  
  > Pokud na zařízení nainstalujete jenom aplikace A a C, stačí nastavit jenom jeden PIN. To samé platí, i pokud jsou na zařízení nainstalované aplikace B a D.

### <a name="app-data-encryption"></a>Šifrování dat aplikací
Správci IT můžou nasadit zásadu ochrany aplikace, která vyžaduje šifrování dat aplikace. Jako součást této zásady může správce IT také určit, kdy se obsah bude šifrovat.

**Jak proces šifrování dat v Intune**<br> Podrobné informace o nastavení zásady ochrany aplikace šifrováním najdete v tématech [Nastavení zásad ochrany aplikací pro Android](app-protection-policy-settings-android.md) a [Nastavení zásad ochrany aplikací pro iOS](app-protection-policy-settings-ios.md).

**Data, která jsou zašifrovaná**<br>
Šifrují se jenom data označená jako podniková, a to podle zásady ochrany aplikace správce IT. Data se považují za podniková, když pocházejí z firemního umístění. Pro aplikace Office Intune považuje za obchodní umístění za tyto účely:

- E-mail (Exchange) 
- Cloudové úložiště (aplikace OneDrive s účtem OneDrivu pro firmy)

U obchodních aplikací spravovaných pomocí [Nástroje pro zabalení aplikace Intune](../developer/apps-prepare-mobile-application-management.md)se všechna data aplikací považují za podniková.

**Vzdáleně vymazat data**<br>

Intune může data aplikace vymazat třemi různými způsoby: 
- Úplné vymazání zařízení
- Selektivní vymazání pro MDM 
- Selektivní vymazání MAM

Další informace o vzdáleném vymazání pro správu mobilních zařízení (MDM) najdete v článku věnovaném [odebrání zařízení pomocí vymazání nebo vyřazení](../remote-actions/devices-wipe.md). Další informace o selektivním vymazání pomocí MAM najdete v části [Vyřazení](../remote-actions/devices-wipe.md#retire) a v článku [Jak z aplikací vymazat jenom firemní data](apps-selective-wipe.md).

[Vymazání](../remote-actions/devices-wipe.md) odebere veškerá uživatelská data a nastavení ze **zařízení** obnovením jeho výchozího továrního nastavení. Zařízení se odebere ze služby Intune.

  >[!NOTE]
  > Vymazání jde dosáhnout jen na zařízeních zaregistrovaných ve správě mobilních zařízení (MDM) Intune.

**Selektivní vymazání pro MDM**<br>
V článku [Odebrání zařízení – část Vyřazení](../remote-actions/devices-wipe.md#retire) najdete informace o odebírání firemních dat.

**Selektivní vymazání pro MAM**<br>
Selektivní vymazání pro MAM jednoduše odebere data aplikace společnosti z aplikace. Žádost se inicializuje pomocí portálu Intune Azure Portal. Informace o zahájení žádosti o vymazání najdete v článku [Jak z aplikací vymazat jenom firemní data](apps-selective-wipe.md).

Pokud uživatel používá aplikaci při zahájení selektivního vymazání, [sada Intune App SDK](../developer/app-sdk.md) každých 30 minut zkontroluje požadavek na selektivní vymazání ze služby Intune mam. Selektivní vymazání také kontroluje tehdy, když uživatel spustí aplikaci poprvé a přihlásí se pomocí pracovního nebo školního účtu.

**Pokud místní (on-Prem) služby nefungují s aplikacemi chráněnými přes Intune**<br>
Ochrana aplikací Intune závisí na identitě uživatele, aby byla konzistentní mezi aplikací a [sadou Intune App SDK](../developer/app-sdk.md). Jediná cesta, která to může zaručit, je moderní ověřování. Jsou situace, kdy aplikace můžou fungovat s místní konfigurací, ale nejsou konzistentní ani nic nezaručují.

**Zabezpečený způsob, jak otevírat webové odkazy ze spravovaných aplikací**<br>
Správce IT může nasadit a nastavit zásadu ochrany aplikace pro [aplikaci Intune Managed Browser](app-configuration-managed-browser.md), což je webový prohlížeč vyvinutý týmem Microsoft Intune, který se dá snadno spravovat přes Intune. Správce IT může vyžadovat, aby se všechny webové odkazy v aplikacích spravovaných přes Intune otvíraly v aplikaci Managed Browser.

## <a name="examples-of-app-protection-policies"></a>Příklady zásad ochrany aplikací

Další informace o příkladech zásad ochrany aplikací a zobrazení podrobných informací o jednotlivých nastaveních zásad ochrany aplikací najdete v tématu nastavení [zásad ochrany aplikací pro Android](app-protection-policy-settings-android.md) a [nastavení zásad ochrany aplikací pro iOS](app-protection-policy-settings-ios.md).

## <a name="app-protection-experience-for-ios-devices"></a>Prostředí ochrany aplikací pro zařízení s iOS

### <a name="device-fingerprint-or-face-ids"></a>Otisky prstů zařízení nebo ID tváře 
Zásady ochrany aplikací Intune umožňují řídit přístup k aplikacím jen uživatelům s licencí na Intune. Jedním ze způsobů, jak řídit přístup k aplikacím, je vyžadovat na podporovaných zařízeních Touch ID nebo Face ID od Applu. Intune se chová tak, že když se v zařízení změní databáze biometrických údajů, vyzve uživatele k zadání kódu PIN, pokud je splněna hodnota časového limitu nečinnosti. Ke změnám biometrických údajů patří přidání nebo odebrání otisku prstu nebo tváře. Pokud uživatel Intune nemá nastavený kód PIN, je nasměrován na nastavení kódu PIN pro Intune.
 
Účelem tohoto procesu je pokračovat v zachování dat vaší organizace v rámci zabezpečení a ochrany v aplikaci na úrovni aplikace. Tato funkce je dostupná jen pro iOS a vyžaduje zapojení aplikací, které integrují sadu Intune APP SDK pro iOS verze 9.0.1 nebo novější. Integrace této sady SDK je nezbytná kvůli vynucení tohoto chování u cílových aplikací. K této integraci dochází průběžně a závisí na týmech konkrétních aplikací. Mezi zapojené aplikace patří například WXP, Outlook, Managed Browser a Yammer.
  
### <a name="ios-share-extension"></a>rozšíření pro sdílení iOS
Rozšíření sdílené složky pro iOS můžete použít k otevření pracovních nebo školních dat v nespravovaných aplikacích, a to i v případě, že se zásady přenosu dat nastavily **jenom na spravované aplikace** nebo **žádné aplikace**. Zásady ochrany aplikací pro Intune nemůžou ovládat rozšíření pro sdílení v iOS, když dané zařízení nespravují. Proto Intune _**podniková data před jejich sdílením mimo příslušnou aplikaci zašifruje**_ . Toto chování šifrování můžete ověřit tak, že se pokusíte otevřít podnikový soubor mimo spravovanou aplikaci. Soubor by měl být zašifrovaný a mimo spravovanou aplikaci by ho nemělo být možné otevřít.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Více nastavení přístupu k ochraně aplikací Intune pro stejnou sadu aplikací a uživatelů
Zásady ochrany aplikací Intune pro přístup se použijí v konkrétním pořadí na zařízeních koncových uživatelů, aby se pokusily o přístup k cílové aplikaci ze svého podnikového účtu. Obecně má přednost vymazání, pak blokování, a pak upozornění, které se dá zavřít. Například pokud se aplikuje na konkrétního uživatele nebo aplikaci, nastavení minimální verze operačního systému iOS, které uživatele upozorňuje, aby svou verzi iOSu aktualizoval, se použije po nastavení minimální verze operačního systému, které uživateli zablokuje přístup. Proto ve scénáři, kde správce IT nakonfiguruje minimální operační systém iOS na 11.0.0.0 a minimální operační systém iOS (pouze upozornění) na 11.1.0.0, zatímco zařízení pokoušející se o přístup k aplikaci má iOS 10, by byl koncový uživatel zablokován na základě přísnějšího nastavení pro minimální verzi operačního systému iOS, které vede k zablokování přístupu.

Při zpracování různých typů nastavení by měl přednost požadavek na verzi Intune App SDK. Následoval by požadavek na verzi aplikace a pak požadavek na verzi operačního systému iOS. Pak se ve stejném pořadí kontrolují všechna upozornění pro všechny typy nastavení. Doporučujeme nakonfigurovat verzi Intune App SDK jenom po pokynu od produktového týmu Intune pro základní scénáře blokování.

## <a name="app-protection-experience-for-android-devices"></a>Prostředí ochrany aplikací pro zařízení s Androidem

### <a name="company-portal-app-and-intune-app-protection"></a>Portál společnosti aplikace a ochrana aplikací Intune
Většina funkcí ochrany aplikací je integrovaná do aplikace Portál společnosti. I když aplikace Portál společnosti se vždycky vyžaduje, registrace zařízení se _nevyžaduje_. Pro správu mobilních aplikací bez registrace (MAM-WE) potřebuje koncový uživatel na zařízení nainstalovanou aplikaci Portál společnosti.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Více nastavení přístupu k ochraně aplikací Intune pro stejnou sadu aplikací a uživatelů
Zásady ochrany aplikací Intune pro přístup se použijí v konkrétním pořadí na zařízeních koncových uživatelů, aby se pokusily o přístup k cílové aplikaci ze svého podnikového účtu. Obecně má přednost blokování, pak upozornění, které se dá zavřít. Například pokud se aplikuje na konkrétního uživatele nebo aplikaci, nastavení minimální verze opravy Androidu, které uživatele upozorňuje, aby provedl upgrade opravy, se použije po nastavení minimální verze opravy Androidu, které uživateli zablokuje přístup. Proto ve scénáři, kde správce IT nakonfiguruje minimální verzi opravy Androidu na 2018-03-01 a minimální verzi opravy Androidu (pouze upozornění) na 2018-02-01, zatímco zařízení pokoušející se o přístup k aplikaci má verzi opravy 2018-01-01, by byl koncový uživatel zablokován na základě přísnějšího nastavení pro minimální verzi opravy Androidu, která vede k zablokování přístupu. 

Při zpracování různých typů nastavení by měl přednost požadavek na verzi aplikace. Následoval by požadavek na verzi operačního systému Android a pak požadavek na verzi opravy Androidu. Pak se ve stejném pořadí kontrolují všechna upozornění pro všechny typy nastavení.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Zásady ochrany aplikací Intune a ověřování SafetyNet Google pro zařízení s Androidem 
Zásady ochrany aplikací Intune poskytují správcům možnost vyžadovat, aby zařízení koncových uživatelů prošla ověřováním SafetyNet Google pro zařízení s Androidem. Správce IT bude hlásit nové Google Play služby v intervalu určeném službou Intune. Četnost volání služby je způsobena omezením zatížení, takže tato hodnota je udržována interně a nelze ji konfigurovat. Veškerá akce nakonfigurovaná správcem IT pro nastavení ověřování Google SafetyNet se provede na základě posledního hlášeného výsledku služby Intune v době podmíněného spuštění. Pokud nejsou k dispozici žádná data, bude přístup povolen v závislosti na neúspěšných kontrolách nepodmíněných spuštění a Google Play služby zpětného vyhledávání pro určení výsledků ověření identity začne v back-endu a uživatel se vyzve k asynchronnímu přihlášení, pokud se zařízení nezdařilo. Pokud jsou k dispozici zastaralá data, přístup se zablokuje nebo povolí v závislosti na posledním zaznamenaném výsledku, a podobně Google Play služby zpětného dotazování pro určení výsledků ověření identity zahájí a uživatele se vyzve k asynchronnímu přihlášení, pokud se zařízení nezdařilo.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Zásady ochrany aplikací Intune a rozhraní API pro ověřování aplikací Google pro zařízení s Androidem
Zásady Intune App Protection poskytují správcům možnost vyžadovat od zařízení koncových uživatelů, aby odesílali signály přes rozhraní API pro zařízení s Androidem prostřednictvím rozhraní Google pro ověřování aplikací. Pokyny k tomu, jak to udělat, se mírně liší podle zařízení. Obecný proces zahrnuje Obchod Google Play a pak kliknutí na **Moje aplikace & hry**. Kliknutím na výsledek poslední kontroly aplikace přejdete do nabídky Play Protect. Zajistěte, aby byl přepínač pro **kontrolu zařízení pro bezpečnostní hrozby** přepnut na zapnuto.

### <a name="googles-safetynet-attestation-api"></a>Rozhraní API pro ověření identity SafetyNet Google 
Intune využívá Google Play ochraně rozhraní API pro SafetyNet, aby se přidaly k existujícím kontrolám zjišťování kořenu pro nezaregistrovaná zařízení. Google vyvinula a zachovala tuto sadu rozhraní API pro aplikace pro Android, aby se mohla přijmout, pokud nechtějí spouštět jejich aplikace na zařízení root. Aplikace pro platby v Androidu tento příklad zahrnula. I když Google nesdílí veřejně celou řadu kontrol kořenového zjišťování, ke kterým dojde, očekáváme, že tato rozhraní API zjišťují uživatele, kteří mají svá zařízení root. Tito uživatelé jim pak můžou zablokovat přístup nebo se jejich firemní účty vymažou z aplikací s povolenými zásadami. **Podívejte se na základní integritu** a dozvíte se o obecné integritě zařízení. Zařízení s rootem, emulátory, virtuální zařízení a zařízení se znaménkem neoprávněného selhání základní integrity. **Kontrola základní integrity & certifikovanými zařízeními** se dozvíte o kompatibilitě zařízení s službami Google. Tuto kontrolu můžou předat jenom nezměněná zařízení, která získala certifikace od společnosti Google. Zařízení, která selžou, budou zahrnovat následující:

- Zařízení, která nevyhověla základní integritě
- Zařízení s odemčeným nástrojem pro spouštění
- Zařízení s vlastní bitovou kopií systému/ROM
- Zařízení, u kterých výrobce nepoužil, nebo předávat certifikát Google
- Zařízení s bitovou kopií systému vytvořenou přímo ze zdrojových souborů programu Open Source v Androidu
- Zařízení se systémovou imagí beta/vývojář verze Preview

Technické podrobnosti najdete v [dokumentaci Google na SafetyNet Attestation](https://developer.android.com/training/safetynet/attestation) .

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Nastavení ověření zařízení SafetyNet a nastavení zařízení s jailbreakem/rootem
Google Play chránit SafetyNet rozhraní API vyžaduje, aby koncový uživatel byl online, a to alespoň po dobu, kdy se spustí "zpětný" čas pro určení výsledků ověření identity. Pokud je koncový uživatel offline, může správce IT stále očekávat, že se výsledek vynutil z nastavení **zařízení s jailbreakem/rootem** . V případě, že je koncový uživatel příliš dlouhý offline, hodnota **období odkladu v režimu offline** přijde do hry a veškerý přístup k pracovním nebo školním datům se po dosažení hodnoty časovače zablokuje, dokud nebude k dispozici přístup k síti. Zapnutím obou nastavení umožníte vrstveným přístupům v dobrém stavu zařízení koncových uživatelů, což je důležité v případě, že koncoví uživatelé přistupují k pracovním nebo školním datům na mobilních zařízeních.

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play chránit rozhraní API a Služby Google Play
Nastavení zásad ochrany aplikací, které využívají Google Play chránit rozhraní API, vyžaduje Služby Google Play funkce. Nastavení **ověřování zařízení SafetyNet**i **Kontrola hrozeb u aplikací** vyžadují, aby správně fungovala verze služby služby Google Play ve verzi Google. Vzhledem k tomu, že se jedná o nastavení, která spadají do oblasti zabezpečení, bude koncový uživatel zablokován, pokud je s těmito nastaveními cílen a nesplňuje příslušnou verzi Služby Google Play nebo nemá přístup k Služby Google Play.

## <a name="next-steps"></a>Další kroky

[Jak vytvořit a nasadit zásady ochrany aplikací pomocí Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Související témata
Aplikace jiných firem, například mobilní aplikace Salesforce, fungují s Intune specifickým způsobem, aby chránily podniková data. Další informace o tom, jak konkrétně aplikace Salesforce funguje s Intune (včetně nastavení konfigurace aplikace MDM), najdete v článku [Aplikace Salesforce a Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).