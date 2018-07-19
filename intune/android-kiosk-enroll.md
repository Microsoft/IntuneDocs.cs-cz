---
title: Registrace zařízení s Androidem Enterprise v beznabídkovém režimu v Intune
titlesuffix: Microsoft Intune
description: Zjistěte, jak v Intune zaregistrovat zařízení s Androidem Enterprise v beznabídkovém režimu.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cd6aee30a88906c3f6ae078e338732589d88a5f0
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909129"
---
# <a name="set-up-enrollment-of-android-enterprise-kiosk-devices"></a>Nastavení registrace zařízení s Androidem Enterprise v beznabídkovém režimu

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android podporuje prostřednictvím svého řešení COSU (Corporate-Owned, Single-Use) zařízení v beznabídkovém režimu. Taková zařízení se používají k jednomu účelu, například jako zobrazovací zařízení na veřejných místech, k tisku vstupenek nebo k evidenci zásob. Správci omezí použití zařízení na omezenou sadu aplikací a webových odkazů. Uživatelé zároveň nemůžou na tomto zařízení přidávat jiné aplikace ani provádět jiné akce.

Intune vám pomůže nasadit do zařízení s Androidem v beznabídkovém režimu aplikace a nastavení. Konkrétní podrobnosti o Androidu Enterprise najdete v tématu [Požadavky na Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Zařízení, která se spravují tímto způsobem, jsou v Intune zaregistrovaná bez uživatelského účtu a nejsou přidružená k žádnému koncovému uživateli. Nejsou určená pro osobní používání aplikací, které závisejí na datech spojených s účtem konkrétního uživatele, jako je Outlook nebo Gmail.

## <a name="device-requirements"></a>Požadavky na zařízení

Aby zařízení bylo možné spravovat jako zařízení s Androidem Enterprise v beznabídkovém režimu, musí splňovat následující požadavky:

- Verze operačního systému Android 5.1 a vyšší
- Zařízení musí používat distribuci Androidu s připojením ke službě GMS (Google Mobile Services). Zařízení musí mít dostupnou službu GMS a musí být schopna se k této službě připojit.

## <a name="set-up-android-kiosk-management"></a>Nastavení správy Androidu v beznabídkovém režimu

Správu Androidu v beznabídkovém režimu nastavíte takto:

1. Při přípravě na správu mobilních zařízení musíte [nastavit autoritu pro správu mobilních zařízení (MDM) na **Microsoft Intune**](mdm-authority-set.md) podle pokynů. Tato možnost se nastavuje jenom jednou při prvním nastavování Intune pro správu mobilních zařízení.
2. [Propojte účet tenanta Intune s účtem Androidu Enterprise](connect-intune-android-enterprise.md).
3. [Vytvořte registrační profil](#create-an-enrollment-profile).
4. [Vytvořte skupinu zařízení](#create-a-device-group).
5. [Zaregistrujte zařízení v beznabídkovém režimu](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>Vytvoření registračního profilu

Kvůli registraci zařízení v beznabídkovém režimu musíte vytvořit registrační profil. Po vytvoření poskytne tento profil registrační token (náhodný řetězec) a kód QR. V závislosti na operačním systému Android a verzi zařízení můžete k [registraci zařízení v beznabídkovém režimu](#enroll-the-kiosk-devices) použít buď token, nebo kód QR.

1. Přejděte na [portál Intune](https://portal.azure.com) a zvolte **Registrace zařízení** > **Registrace Androidu** > **Beznabídkový režim a registrace zařízení úloh**.
2. Zvolte **Vytvořit** a vyplňte požadovaná pole.
    - **Název**: Zadejte název, který použijete při přiřazení tohoto profilu k dynamické skupině zařízení.
    - **Datum vypršení platnosti tokenu**: Datum, kdy vyprší platnost tokenu. Google vynucuje maximálně 30 dnů.
3. Uložte profil pomocí tlačítka **Vytvořit**.

### <a name="create-a-device-group"></a>Vytvoření skupiny zařízení

Aplikace a zásady můžete cílit buď na přiřazené, nebo dynamické skupiny zařízení. Následujícím postupem nakonfigurujete dynamické skupiny zařízení služby AAD tak, aby se automaticky naplnily zařízeními, která se zaregistrují s konkrétním registračním profilem:

1. Přejděte na [portál Intune](https://portal.azure.com) a zvolte **Skupiny** > **Všechny skupiny** > **Nová skupina**.
2. V okně **Skupina** vyplňte požadovaná pole následujícím způsobem:
    - **Typ skupiny**: Zabezpečení
    - **Název skupiny**: Zadejte výstižný název (například Zařízení závodu 1).
    - **Typ členství**: Dynamické zařízení
3. Zvolte **Přidat dynamický dotaz**.
4. V okně **Pravidla dynamického členství** vyplňte pole následujícím způsobem:
    - **Přidat dynamické pravidlo členství**: Jednoduché pravidlo
    - **Přidat zařízení, kde**: Název registračního profilu
    - V prostředním poli zvolte **Shoda**.
    - Do posledního pole zadejte název dříve vytvořeného registračního profilu.
5. Zvolte **Přidat dotaz** > **Vytvořit**.

### <a name="replace-or-remove-tokens"></a>Nahrazení nebo odebrání tokenů

Tokeny a kódy QR můžete nahradit nebo odebrat.

- **Nahrazení tokenu**: Příkazem Nahradit token můžete vygenerovat nový token nebo kód QR, pokud brzy vyprší platnost stávajícího.
- **Odvolání tokenu**: Platnost tokenu nebo kódu QR můžete nechat okamžitě vypršet. Od tohoto okamžiku nebude token nebo kód QR použitelný. Tuto možnost můžete použít, pokud:
    - Omylem nasdílíte token nebo kód QR s neautorizovanou stranou
    - Dokončíte všechny registrace a token nebo kód QR už nepotřebujete

Nahrazení nebo odvolání tokenu/kódu QR nebude mít žádný vliv na zařízení, která už jsou zaregistrovaná.

1. Přejděte na [portál Intune](https://portal.azure.com) a zvolte **Registrace zařízení** > **Registrace Androidu** > **Beznabídkový režim a registrace zařízení úloh**.
2. Zvolte profil, se kterým chcete pracovat.
3. Zvolte **Token**.
4. Pokud chcete token nahradit, zvolte **Nahradit token**.
5. Pokud chcete token odvolat, zvolte **Odvolat token**.

## <a name="enroll-the-kiosk-devices"></a>Registrace zařízení v beznabídkovém režimu

Po vytvoření registračního profilu a dynamické skupiny zařízení můžete zařízení v beznabídkovém režimu zaregistrovat. Způsob registrace zařízení s Androidem závisí na operačním systému.

| Způsob registrace | Minimální podporovaná verze operačního systému Android |
| ----- | ----- |
| Bezkontaktní komunikace (NFC) | 5.1 |
| Zadání tokenu | 6.0 |
| Kód QR | 7.0 |
| Zero Touch | 8.0 u zapojených výrobců |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Registrace pomocí bezkontaktní komunikace (NFC)

Zařízení s Androidem 5.1 a vyšším, která podporují bezkontaktní komunikaci (NFC), můžete zřídit vytvořením speciálně naformátované značky NFC. Můžete použít svou vlastní aplikaci nebo nástroj pro vytváření značek NFC. Další informace najdete v [dokumentaci Googlu k rozhraní Android Management API](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Registrace pomocí tokenu

U zařízení s Androidem 6 a vyšším můžete k registraci zařízení použít token.

1. Uveďte zařízení do režimu obnovení továrního nastavení.
2. Na **uvítací** obrazovce vyberte svůj jazyk.
3. Připojte se k **Wi-Fi** síti a zvolte **DALŠÍ**.
4. Přijměte podmínky a ujednání Googlu a zvolte **DALŠÍ**.
5. Na obrazovce pro přihlášení ke Googlu zadejte místo účtu Google text **afw#setup** a zvolte **DALŠÍ**.
6. U aplikace **Android Device Policy** zvolte **NAINSTALOVAT**.
7. Pokračujte v instalaci těchto zásad.  Některá zařízení můžou vyžadovat přijetí dodatečných podmínek. 
8. Na obrazovce **Zaregistrovat toto zařízení** umožněte zařízení naskenovat kód QR nebo zvolte ruční zadání tokenu.
9. Podle pokynů na obrazovce dokončete registraci. 

### <a name="enroll-by-using-a-qr-code"></a>Registrace pomocí kódu QR

Zařízení s Androidem 7 a vyšším můžete zaregistrovat naskenováním kódu QR z registračního profilu.

1. Čtení kódu QR spustíte na zařízení s Androidem tak, že několikrát klepnete na první obrazovku, kterou uvidíte po obnovení továrního nastavení.
2. U zařízení s Androidem 7 a 8 budete vyzváni k instalaci čtečky kódů QR. Zařízení s Androidem 9 a vyšším už mají čtečku kódů QR nainstalovanou.
3. Pomocí čtečky kódů QR naskenujte kód QR registračního profilu a podle pokynů na obrazovce se zaregistrujte.

### <a name="enroll-by-using-google-zero-touch"></a>Registrace pomocí systému Google Zero Touch

Abyste mohli použít systém Zero Touch od Googlu, musí ho zařízení podporovat a být spřažené s dodavatelem, který je součástí této služby.  Další informace najdete na [webu věnovaném systému Zero Touch od Googlu](https://www.android.com/enterprise/management/zero-touch/). 


1. Vytvořte novou konfiguraci v konzole Zero Touch.
2. V rozevíracím seznamu EMM DPC zvolte **Microsoft Intune**.
3. V konzole Zero Touch zkopírujte a vložte následující JSON do pole DPC extras. Řetězec *YourEnrollmentToken* nahraďte registračním tokenem, který jste vytvořili jako součást registračního profilu. Nezapomeňte registrační token uzavřít do dvojitých uvozovek.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Zvolte **Použít**.

## <a name="managing-apps-on-android-kiosk-devices"></a>Správa aplikací na zařízeních s Androidem v beznabídkovém režimu

Na zařízení s Androidem v beznabídkovém režimu lze instalovat jen aplikace, jejichž Typ přiřazení [je nastavený na Povinné](apps-deploy.md#to-assign-an-app). Aplikace se instalují ze spravovaného obchodu Google Play stejným způsobem jako u zařízení s pracovním profilem Androidu.

Když vývojář aplikace publikuje aktualizaci do obchodu Google Play, aktualizují se aplikace na spravovaných zařízeních automaticky.

Pokud chcete ze zařízení s Androidem v beznabídkovém režimu odebrat aplikaci, můžete použít jeden z těchto způsobů:
-   Odstranění nasazení povinné aplikace
-   Vytvoření nasazení odinstalace pro tuto aplikaci


## <a name="next-steps"></a>Další kroky
- [Nasazení aplikací Androidu v beznabídkovém režimu](apps-deploy.md)
- [Přidání zásad konfigurace Androidu v beznabídkovém režimu](device-profiles.md)