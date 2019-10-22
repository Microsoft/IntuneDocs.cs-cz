---
title: Xamarinové vazby sady Microsoft Intune App SDK
description: Xamarinové vazby sady Intune App SDK umožňují v aplikacích pro iOS a Android vytvořených v Xamarinu povolit zásady ochrany aplikací Intune.
keywords: SDK, Xamarin, Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19202d4387635b7cd1f7e4604d755fb8a213d327
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503436"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Xamarinové vazby sady Microsoft Intune App SDK

> [!NOTE]
> Možná si budete chtít nejdřív přečíst článek [Začínáme s Intune App SDK](app-sdk-get-started.md), který vysvětluje postup přípravy integrace na jednotlivých podporovaných platformách.

## <a name="overview"></a>Overview
[Xamarinové vazby sady Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) umožňují v aplikacích pro iOS a Android vytvořených v Xamarinu povolit [zásady ochrany aplikací Intune](../apps/app-protection-policy.md). Tyto vazby umožňují vývojářům jednoduše do aplikací založených na Xamarinu začlenit funkce ochrany aplikace Intune.

Xamarinové vazby sady Microsoft Intune App SDK umožňují začlenit do vašich aplikací vyvíjených v Xamarinu zásady ochrany aplikací Intune (také označované jako zásady APP nebo MAM). Aplikace s povolenou funkcí MAM je integrovaná se sadou Intune App SDK. Správci IT můžou zásady ochrany aplikací nasadit do vaší mobilní aplikace, když Intune tuto aplikaci aktivně spravuje.

## <a name="whats-supported"></a>Co se podporuje

### <a name="developer-machines"></a>Počítače pro vývojáře
* Windows (Visual Studio verze 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Platformy pro mobilní aplikace
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Scénáře Správy mobilních aplikací Intune

* Intune APP-WE (bez registrace zařízení)
* Zařízení zaregistrovaná v Intune MDM
* Zařízení zaregistrovaná v EMM třetích stran

Xamarinové aplikace vytvořené xamarinovými vazbami sady Intune App SDK přijímají zásady ochrany aplikací Intune na zařízeních zaregistrovaných ve správě mobilních zařízení (MDM) Intune i na neregistrovaných zařízeních.

## <a name="prerequisites"></a>Požadované součásti

Přečtěte si [licenční podmínky](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Vytisknout a uchovat pro své záznamy kopii licenčních podmínek. Stažením a použitím xamarinových vazeb sady Intune App SDK přijímáte tyto licenční podmínky. Pokud je nepřijímáte, software nepoužívejte.

Intune SDK se spoléhá na [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) pro své scénáře [ověřování](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) a podmíněného spuštění, které vyžadují konfiguraci aplikací pomocí [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Pokud je vaše aplikace už nakonfigurovaná tak, aby používala ADAL nebo MSAL, a má vlastní ID klienta, které se používá k ověření pomocí Azure Active Directory, zajistěte, aby vaše oprávnění aplikace Xamarin poskytovala službě Intune Mobile Application Management (MAM). uplatnil. Postupujte podle pokynů v části "[poskytnutí přístupu aplikace ke službě Intune App Protection](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" v tématu [Začínáme s Intune SDK](app-sdk-get-started.md).



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Povolení zásad ochrany aplikací Intune v mobilní aplikaci pro iOS
1. Do svého projektu Xamarin.iOS přidejte [balíček NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS).
2. Při integraci sady Intune App SDK do mobilní aplikace pro iOS dodržujte obecné pokyny. Začněte od 3. kroku popsaného v [příručce pro vývojáře k sadě Intune App SDK pro iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Poslední krok v této části spuštění nástroje IntuneMAMConfigurator můžete přeskočit, protože tento nástroj je součástí balíčku Microsoft.Intune.MAM.Xamarin.iOS a spustí se automaticky při sestavení.
    **Důležité:** Povolení sdílení klíčenky aplikace je v sadě Visual Studio trochu jiné než v Xcode. Otevřete soubor Entitlements.plist aplikace a zkontrolujte, že je povolená možnost „Enable Keychain“ (Povolit klíčenku) a že jsou do oddílu přidané odpovídající skupiny pro sdílení klíčenky. Zkontrolujte, že je v poli „Custom Entitlements“ (Vlastní oprávnění) v možnostech podepsání sady prostředků aplikace pro iOS zadaný soubor Entitlements.plist, a to pro všechny kombinace konfigurace a platformy, které připadají v úvahu.
3. Jakmile přidáte vazby a aplikaci správně nakonfigurujete, může aplikace začít používat rozhraní API sady Intune SDK. Aby to bylo možné, musíte přidat následující obor názvů:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Aby aplikace mohly začít přijímat zásady ochrany, musíte je zaregistrovat do služby Intune MAM. Pokud vaše aplikace nepoužívá k ověřování uživatelů knihovnu [ADAL](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (Azure Active Directory Authentication Library) ani [MSAL](https://www.nuget.org/packages/Microsoft.Identity.Client) (Microsoft Authentication Library) a chtěli byste ověřování svěřit sadě Intune SDK, měla by aplikace poskytovat metodě LoginAndEnrollAccount třídy IntuneMAMEnrollmentManager hlavní název uživatele (UPN):

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      Aplikace mohou předat hodnotu null, pokud hlavní název uživatele není v době volání známý. V takovém případě budou uživatelé vyzváni k zadání e-mailové adresy a hesla.
      
      Pokud vaše aplikace už k ověřování uživatelů používá knihovnu ADAL nebo MSAL, můžete mezi aplikací a sadou Intune SDK nakonfigurovat jednotné přihlašování. Nejprve budete muset nakonfigurovat knihovnu ADAL/MSAL tak, aby se tokeny ukládaly ve stejné přístupové skupině řetězce klíčů, kterou používají xamarinové vazby pro iOS (com.microsoft.adalcache). Pro ADAL to můžete udělat [nastavením vlastnosti iOSKeychainSecurityGroup třídy AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access). Pro MSAL budete muset [nastavit vlastnost iOSKeychainSecurityGroup pro PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access). Dále budete muset přepsat výchozí nastavení služby AAD používaná sadou Intune SDK těmi, která používá vaše aplikace. Můžete to udělat prostřednictvím slovníku IntuneMAMSettings v souboru Info.plist aplikace podle popisu v [příručce pro vývojáře k sadě Intune App SDK pro iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) nebo můžete použít vlastnosti přepisu AAD v instanci IntuneMAMPolicyManager. Způsob se souborem Info.plist se doporučuje použít u aplikací se statickým nastavením ADAL. Vlastnosti přepisu se doporučují použít u aplikací, které tyto hodnoty zjišťují za běhu. Po konfiguraci všech nastavení jednotného přihlašování by vaše aplikace měla metodě RegisterAndEnrollAccount třídy IntuneMAMEnrollmentManager po úspěšném ověření poskytnout hlavní název uživatele (UPN):

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      Aplikace mohou určit výsledek pokusu o registraci implementací metody EnrollmentRequestWithStatus v podtřídě IntuneMAMEnrollmentDelegate a nastavením vlastnosti Delegate třídy IntuneMAMEnrollmentManager na instanci této třídy. 

      Po úspěšné registraci mohou aplikace určit hlavní název uživatele zaregistrovaného účtu (pokud předtím nebyl známý) dotazem na následující vlastnost: 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>Ukázkové aplikace
Ukázkové aplikace zvýrazňování MAM funkcí v aplikacích Xamarin. iOS jsou k dispozici na [GitHubu](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

> [!NOTE] 
> Pro iOS není k dispozici nástroj pro přemapování. Integrace do aplikace Xamarin.Forms by měla být stejná jako u normálního projektu Xamarin.iOS. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Povolení zásad Intune App Protection v mobilní aplikaci pro Android
1. Do svého projektu Xamarin.Android přidejte [balíček NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android).
    1. V případě aplikace Xamarin. Forms přidejte do projektu Xamarin. Android také [balíček NuGet Microsoft. Intune. mam. remapper. Tasks. Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) . 
2. Postupujte podle obecných kroků nezbytných pro [integraci sady Intune App SDK](app-sdk-android.md) do mobilní aplikace pro Android a při odkazování na tento dokument, kde najdete další podrobnosti.

### <a name="xamarinandroid-integration"></a>Integrace Xamarin.Android

Úplný přehled integrace sady Intune App SDK najdete v [příručce pro vývojáře sady Microsoft Intune App SDK pro Android](app-sdk-android.md). Jak si přečtete příručku a integrujte sadu Intune App SDK s vaší aplikací Xamarin. následující oddíly mají za cíl zvýraznit rozdíly mezi implementací nativní aplikace pro Android vyvinuté v jazyce Java a aplikací Xamarin vyvinutou v C#. Tyto části by se měly považovat za doplňkové a nemůžou fungovat jako náhrada za celý průvodce.

#### <a name="remapper"></a>Remapper
Od verze 1.4428.1 se balíček `Microsoft.Intune.MAM.Remapper` dá přidat do aplikace Xamarin. Android jako [Nástroj pro vytváření](app-sdk-android.md#build-tooling) , který umožňuje přemístit mam třídu, metodu a služby Systems. Pokud je přemapování zahrnuto, MAM ekvivalentní části přejmenovaných metod a oddílů aplikace MAM budou automaticky provedeny při sestavení aplikace.

Chcete-li vyloučit třídu z MAM-sjednocení přemapováním, lze do projektu přidat následující vlastnost `.csproj` souboru.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> V tuto chvíli problém s opětovným zamapováním brání ladění v aplikacích Xamarin. Android. Ruční integrace je doporučena pro ladění aplikace, dokud tento problém nebude vyřešen.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Přejmenované metody](app-sdk-android.md#renamed-methods)
V mnoha případech je metoda dostupná ve třídě Androidu označená v náhradní třídě MAM jako finální. Náhradní třída MAM pak poskytuje metodu s podobným názvem (s příponou `MAM`), kterou byste měli přepsat místo toho. Třeba při odvozování od třídy `MAMActivity` musí `Activity` místo přepsání `OnCreate()` a volání `base.OnCreate()` přepsat `OnMAMCreate()` a volat `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Aplikace MAM](app-sdk-android.md#mamapplication)
Vaše aplikace musí definovat třídu `Android.App.Application`. Pokud manuálně integruje MAM, musí dědit z `MAMApplication`. Zkontrolujte, že podtřída je správně doplněna o atribut `[Application]` a že přepisuje konstruktor `(IntPtr, JniHandleOwnership)`.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> Problém s MAMmi vazbami Xamarin může způsobit chybu aplikace při nasazení v režimu ladění. Alternativním řešením je, že atribut `Debuggable=false` musí být přidán do třídy `Application` a příznak `android:debuggable="true"` musí být odebrán z manifestu, pokud byl ručně nastaven.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Povolení funkcí, které vyžadují účast aplikace](app-sdk-android.md#enable-features-that-require-app-participation)
Příklad: Určení, jestli aplikace vyžaduje PIN

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Příklad: Určení primárního uživatele Intune

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Příklad: Určení, jestli je povoleno ukládání na zařízení nebo do cloudového úložiště

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Zaregistrujte se na oznámení ze sady SDK.](app-sdk-android.md#register-for-notifications-from-the-sdk)
Vaše aplikace se musí zaregistrovat pro oznámení ze sady SDK vytvořením `MAMNotificationReceiver` a registrací pomocí `MAMNotificationReceiverRegistry`. To se provádí tím, že poskytne přijímač a typ oznámení požadovaného v `App.OnMAMCreate`, jak ukazuje následující příklad:

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Správce registrace MAM](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Integrace Xamarin.Forms

U aplikací `Xamarin.Forms` balíček `Microsoft.Intune.MAM.Remapper` provádí nahrazení třídy MAM automaticky vložením tříd `MAM` do hierarchie tříd běžně používaných tříd `Xamarin.Forms`. 

> [!NOTE]
> Integraci Xamarin. Forms je třeba provést společně s výše podrobnější integrací Xamarin. Android. Remapovače se chová jinak pro aplikace Xamarin. Forms, takže ruční MAM nahrazení bude stále potřeba provést.

Po přidání remapovače do projektu budete muset provést přemístění ekvivalenty MAM. Například `FormsAppCompatActivity` a `FormsApplicationActivity` lze nadále používat ve vaší aplikaci, které přepíší do `OnCreate` a `OnResume` se nahrazují ekvivalenty MAM `OnMAMCreate` a `OnMAMResume` v uvedeném pořadí.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

Pokud nejsou náhrady provedeny, může dojít k následujícím chybám při kompilaci, dokud neprovedete náhrady:
* [Chyba kompilátoru CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Tato chyba se běžně zobrazuje v tomto formátu ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
To je očekáváno, protože když přemapování mění dědění tříd Xamarin, budou provedeny určité funkce `sealed` a místo toho je přidána nová varianta MAM k přepsání.
* [Chyba kompilátoru CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Tato chyba se běžně zobrazuje v tomto formuláři ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Pokud přemapování změní dědění některých tříd Xamarin, budou některé členské funkce změněny na `public`. Pokud přepíšete některou z těchto funkcí, budete muset změnit tyto modifikátory přístupu, aby tato přepsání byla také `public`.

> [!NOTE]
> Remapper znovu zapíše závislost, kterou Visual Studio používá pro automatické dokončování IntelliSense. Proto může být nutné znovu načíst a znovu sestavit projekt při přidání nového mapování pro technologii IntelliSense, aby byly změny správně rozpoznány.

#### <a name="troubleshooting"></a>Odstraňování potíží
* Pokud při spuštění aplikace narazíte na prázdnou bílou obrazovku, možná budete muset vynutit, aby se volání navigace spouštěla v hlavním vlákně.
* Vazby Xamarin sady Intune SDK nepodporují aplikace, které používají architekturu pro víc platforem, jako je například MvvmCross, z důvodu konfliktů mezi MvvmCross a třídami MAM Intune. I když někteří zákazníci mohou mít po přesunu svých aplikací do jednoduchých Xamarin. Forms úspěch s integrací, neposkytujeme pro vývojáře aplikací explicitní pokyny a moduly plug-in, které používají MvvmCross.

### <a name="company-portal-app"></a>Aplikace Portál společnosti
Vazby Xamarin sady Intune SDK spoléhají na přítomnost [portál společnosti](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) aplikace pro Android na zařízení, aby se povolily zásady ochrany aplikací. Portál společnosti načítá zásady ochrany aplikací ze služeb Intune. Při inicializaci načte aplikace z Portálu společnosti zásadu a kód, který ji vynucuje. Uživatel nemusí být přihlášený.

> [!NOTE]
> Když aplikace Portál společnosti není na zařízení s **Androidem** , chová se aplikace spravovaná v Intune stejně jako běžná aplikace, která nepodporuje zásady ochrany aplikací Intune.

U ochrany aplikací bez registrace zařízení _**nemusí**_ uživatel registrovat zařízení přes aplikaci Portál společnosti.

### <a name="sample-applications"></a>Ukázkové aplikace
Ukázkové aplikace zvýrazňování MAM funkcí v aplikacích Xamarin. Android a Xamarin. Forms jsou dostupné na [GitHubu](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Support
Pokud je vaše organizace stávajícím zákazníkem Intune, obraťte se na svého zástupce podpory Microsoftu, aby otevřel lístek podpory a [na stránce problémů na GitHubu](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)vytvořil problém. Pomůžeme vám, jakmile budeme. 