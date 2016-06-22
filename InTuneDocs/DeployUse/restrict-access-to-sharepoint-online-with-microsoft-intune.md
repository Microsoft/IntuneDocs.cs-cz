---
# required metadata

title: Omezení přístupu ke službě SharePoint Online | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Omezení přístupu ke službě SharePoint Online pomocí Microsoft Intune
Pro řízení přístupu k souborům umístěným ve službě SharePoint online použijte podmíněný přístup [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)].
Podmíněný přístup má dvě součásti:
- Zásady dodržování předpisů zařízení, které zařízení musí dodržovat, aby mohlo být považované za vyhovující.
- Zásady podmíněného přístupu, kde můžete určit podmínky, které zařízení musí splňovat pro přístup ke službě.
Další informace o tom, jak podmíněný přístup funguje, najdete v tématu věnovaném [omezení přístupu k e-mailu a službám O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Když se uživatel na svém zařízení pokusí připojit k souboru pomocí podporované aplikace, jako je třeba OneDrive, dojde k následujícímu vyhodnocení:

![Diagram zobrazující průběh rozhodování, jestli má zařízení povolený přístup do služby SharePoint ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>Podmíněný přístup pro počítače PC a zařízení Windows 10 Mobile s aplikacemi využívajícími moderní ověřování není aktuálně dostupný pro všechny zákazníky využívající Intune. Pokud tyto funkce využíváte, nemusíte provádět žádnou akci. Můžete je dál používat.

>Pokud jste pro počítače nebo zařízení s Windows 10 Mobile pro aplikace využívající moderní ověřování nevytvořili zásady podmíněného přístupu a chcete to udělat, musíte odeslat žádost.  Další informace o známých problémech a o tom, jak k této funkci získat přístup, najdete na [webu Connect](http://go.microsoft.com/fwlink/?LinkId=761472).

**Dřív** než nakonfigurujete zásady podmíněného přístupu pro SharePoint Online, musíte:
- Mít předplatné **SharePointu Online** a uživatelé musí mít licenci SharePointu Online.
- Mít předplatné **Enterprise Mobility Suite** nebo **Azure Active Directory Premium**.

  Pro připojení k požadovaným souborům zařízení:
-   Musí být **zaregistrované** ve službě [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] nebo se musí jednat o počítač připojený k doméně.

-   **Zaregistrujte zařízení** v Azure Active Directory (k tomu automaticky dojde při registraci zařízení ve službě [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Musí splňovat veškeré nasazené zásady dodržování předpisů [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Stav zařízení je uložený ve službě Azure Active Directory, která uděluje nebo blokuje přístup k souborům na základě podmínek, které zadáte.

Pokud není podmínka splněná, zobrazí se uživateli při přihlášení jedna z následujících zpráv:

-   Pokud zařízení není zaregistrované v [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] nebo v Azure Active Directory, zobrazí se zpráva s pokyny pro instalaci aplikace portálu společnosti a registraci.

-   Pokud zařízení není kompatibilní, zobrazí se zpráva, která uživatele přesměruje na web portálu společnosti [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] , kde najde informace o problému a jeho řešení.

## Podpora mobilních zařízení
- iOS 7.1 nebo novější
- Android 4.0 nebo novější, Samsung Knox Standard 4.0 nebo novější
- Windows Phone 8.1 nebo novější

## Podpora počítačů
- Windows 8.1 nebo novější (při registraci v Intune)
- Windows 7.0 nebo Windows 8.1 (při připojení k doméně)

  - Pro počítače připojené k doméně musíte nastavit [automatickou registraci](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) v Azure Active Directory.
Pro zákazníky Intune a Office 365 je služba AAD DRS aktivovaná automaticky. Zákazníci, kteří už mají nasazenou službu AD FS Device Registration Service, registrovaná zařízení ve svojí místní službě Active Directory neuvidí.

  - Pokud je zásada nastavená tak, aby vyžadovala připojení k doméně, a počítač k doméně připojený není, zobrazí se zpráva, aby uživatel kontaktoval správce IT.

  - Pokud je zásada nastavená tak, aby vyžadovala připojení k doméně nebo splňování předpisů, a počítač ani jeden z těchto požadavků nesplňuje, zobrazí se zpráva s pokyny, jak nainstalovat aplikaci Portál společnosti a provést registraci.
-    [Musí být povolené moderní ověřování Office 365](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) a musí být dostupné nejnovější aktualizace Office.

    Moderní ověřování poskytuje klientům Office 2013 Windows přihlašování založené na ADAL (Active Directory Authentication Library) a umožňuje lepší zabezpečení, jako je **vícefaktorové ověřování** a **ověřování prostřednictvím certifikátu**.


## Konfigurace podmíněného přístupu pro SharePoint Online

### Krok 1: Konfigurace skupin zabezpečení služby Active Directory
Než začnete, nakonfigurujte pro skupiny zabezpečení služby Azure Active Directory zásadu podmíněného přístupu. Tyto skupiny můžete nakonfigurovat v **Centru pro správu Office 365**nebo na **Portálu účtů Intune**. Tyto skupiny se použijí k cílení nebo vyloučení uživatelů ze zásady. Pokud je uživatel cílem zásady, musí každé jím používané zařízení splňovat zásady, aby měl přístup k prostředkům.

V rámci zásad SharePointu Online můžete zadat dva typy skupin:

-   **Cílové skupiny** – Skupiny uživatelů, na které se má zásada aplikovat.

-   **Vyloučené skupiny** – Skupiny uživatelů, kteří jsou ze zásady vyloučeni.

Pokud je uživatel v obou skupinách, bude ze zásad vyloučený.

### Krok 2: Konfigurace a nasazení zásad dodržování předpisů
Pokud jste to ještě neudělali, vytvořte a nasaďte zásady dodržování předpisů pro uživatele, na které bude zásada SharePointu Online cílit.

> [!NOTE] Zásady dodržování předpisů se nasadí do skupin [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a zásady podmíněného přístupu cílí na skupiny zabezpečení služby Azure Active Directory.

Podrobnosti o konfiguraci zásad dodržování předpisů najdete v tématu věnovaném [vytvoření zásad dodržování předpisů](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT] Pokud jste zásady dodržování předpisů nenasadili, budou se zařízení považovat za vyhovující.

Až budete připravení, pokračujte **Krokem 3**.

### Krok 3: Konfigurace zásad SharePointu Online
V dalším kroku nakonfigurujte zásadu, která bude vyžadovat, aby měla k SharePointu Online přístup jenom spravovaná zařízení, která jsou v souladu s předpisy. Tato zásada bude uložená v Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

1.  V [konzole pro správu Microsoft Intune](https://manage.microsoft.com) klikněte na **Zásady** > **Podmíněný přístup** > **Zásady pro SharePoint Online**.
![Snímek stránky zásad SharePointu Online](../media/IntuneSASharePointOnlineCAPolicy.png)

2.  Vyberte **Zapnout zásady podmíněného přístupu pro SharePoint Online**.

3.  V části **Přístup k aplikaci** můžete použít zásady podmíněného přístupu na:

    -   **Všechny platformy**

        To vyžaduje, aby každé zařízení používané pro přístup k **SharePointu Online** bylo registrované v Intune a dodržovalo tyto zásady.  Všechny klientské aplikace používající **moderní ověřování** podléhají zásadám podmíněného přístupu. Pokud Intune příslušnou platformu aktuálně nepodporuje, přístup k **SharePointu Online** je zablokovaný.
        >[!TIP]
        >Pokud ještě nepoužíváte podmíněný přístup pro počítače PC, nemusí se vám tato možnost zobrazit.  Místo toho použijte možnost **Specifické platformy**. Podmíněný přístup pro počítače PC není aktuálně k dispozici všem zákazníkům Intune.   Další informace o známých problémech a o tom, jak k této funkci získat přístup, najdete na [webu Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472).

    -   **Specifické platformy**

         Zásady podmíněného přístupu se použijí na každou klientskou aplikaci, která na určených platformách zařízení používá moderní ověřování.

     Počítače s Windows musí buď připojené k doméně, nebo zaregistrované v [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a v souladu s předpisy. Můžete nastavit následující požadavky:

     -   **Zařízení musí být připojené k doméně nebo splňovat předpisy.** Tuto možnost vyberte, pokud chcete, aby počítače byly buď připojené k doméně, nebo splňovaly zásady nastavené v [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Pokud počítač některý z těchto požadavků nesplňuje, zobrazí se uživateli výzva k registraci zařízení ve službě [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Zařízení musí být připojené k doméně.** Tuto možnost vyberte, pokud chcete, aby počítače musely být pro přístup k Exchangi Online připojené k doméně. Pokud počítač není připojený k doméně, je přístup k e-mailu blokovaný a uživatel je vyzván, aby se obrátil na správce IT.

     -   **Zařízení musí splňovat předpisy.** Tuto možnost vyberte, pokud chcete, aby počítače musely být zaregistrované v [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a splňovat předpisy. Pokud počítač není zaregistrovaný, zobrazí se zpráva s pokyny, jak registraci provést.

4.  V části **Cílové skupiny**klikněte na **Upravit** a vyberte skupiny zabezpečení Active Directory, na které se zásady vztahují. Můžete cílit na všechny uživatele nebo vybrané skupiny uživatelů.

5.  V případě potřeby v části **Vyloučené skupiny**klikněte na **Upravit** a vyberte skupiny zabezpečení Azure Active Directory, na které se tyto zásady nevztahují.

6.  Po dokončení klikněte na **Uložit**.

Zásady podmíněného přístupu není potřeba nasazovat, projeví se okamžitě.

### Krok 4: Sledování dodržování předpisů a zásad podmíněného přístupu
V pracovním prostoru **Skupiny** se můžete podívat na stav svých zařízení.

Vyberte libovolnou skupinu mobilních zařízení a pak na kartě **Zařízení** vyberte jeden z následujících **filtrů**:

-   **Zařízení nezaregistrovaná v AAD:** Tato zařízení jsou na SharePointu Online blokovaná.

-   **Zařízení nevyhovující předpisům:** Tato zařízení jsou na SharePointu Online blokovaná.

-   **Zařízení zaregistrovaná v AAD a vyhovující předpisům:** Tato zařízení mají přístup k SharePointu Online.

### Související témata
[Omezení přístupu k e-mailu a službám O365 pomocí Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->

