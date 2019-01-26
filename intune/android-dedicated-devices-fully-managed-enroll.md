---
title: Registrace zařízení s Androidem vyhrazené nebo plně spravovaných zařízeních v Intune
titlesuffix: Microsoft Intune
description: Zjistěte, jak zaregistrovat zařízení s Androidem enterprise vyhrazené nebo fulluy spravovaných zařízení v Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 0366a4394f5046d72c7cf01d2848974d225597a6
ms.sourcegitcommit: d757c907af6c3c1b20823ffa4fda3acbaa8ecd9f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2019
ms.locfileid: "54444553"
---
# <a name="enroll-your-android-dedicated-devices-or-fully-managed-devices-preview"></a>Registrace zařízení s Androidem vyhrazené nebo plně spravovaná zařízení (Preview)

Po nastavení vašeho [vyhrazená zařízení s Androidem](android-kiosk-enroll.md) nebo [plně spravovaná zařízení](android-fully-managed-enroll.md) v Intune, můžete tato zařízení zaregistrovat. Způsob registrace zařízení s Androidem závisí na operačním systému.

| Způsob registrace | Minimální verze operačního systému Android pro vyhrazená zařízení. | Minimální verze operačního systému Android pro plně spravovaná zařízení |
| ----- | ----- | ----- |
| Bezkontaktní komunikace (NFC) | 5.1 | 6.0 |
| Zadání tokenu | 6.0 | 6.0 |
| Kód QR | 7.0 | 7.0 |
| Zero Touch  | 8.0\* | 8.0\* |

\* Na zúčastněných výrobci.

### <a name="enroll-by-using-near-field-communication-nfc"></a>Registrace pomocí bezkontaktní komunikace (NFC)

Pro zařízení, které podporují NFC můžete zřizovat zařízení tak, že vytvoříte speciálně formátovaného značky NFC. Můžete použít svou vlastní aplikaci nebo nástroj pro vytváření značek NFC. Další informace najdete v tématu [registrace zařízení na základě jazyka C s Androidem Enterprise v Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) a [dokumentaci rozhraní API správy systému Android od Googlu](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Registrace pomocí tokenu

U zařízení s Androidem 6 a vyšším můžete k registraci zařízení použít token. Android verze 6.1 a novější můžete taky využít naskenovat kód QR. při použití **afw #setup** metodu registrace.

1. Zapněte vymazané zařízení.
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

> [!Note]
> Zvětšení v prohlížeči může způsobit, že zařízení nebudou moct naskenovat kód QR. Tento problém se dá vyřešit zvýšením zvětšení v prohlížeči.

1. Čtení kódu QR spustíte na zařízení s Androidem tak, že několikrát klepnete na první obrazovku, kterou uvidíte po vymazání.
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


## <a name="next-steps"></a>Další postup
- [Nasadit aplikace pro Android](apps-deploy.md)
- [Přidání zásad konfigurace pro Android](device-profiles.md)
