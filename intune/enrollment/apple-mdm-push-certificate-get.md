---
title: Získání certifikátu Apple MDM push Certificate pro Intune
titleSuffix: ''
description: Získání certifikátu Apple MDM push Certificate pro správu zařízení s iOS pomocí Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d15fd73a608c799745c92c4b07df4b9705d00106
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490319"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Získání certifikátu Apple MDM Push Certificate

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pro správu zařízení s iOSem a macOS potřebuje Intune certifikát Apple MDM Push. Po přidání certifikátu do Intune si uživatelé můžou zaregistrovat zařízení pomocí:

- aplikace Portál společnosti,

- nástrojů hromadné registrace Apple, jako je Program registrace zařízení, Apple School Manager nebo Apple Configurator.

Další informace o možnostech registrace najdete v článku o [způsobech registrace zařízení s iOSem](ios-enroll.md).

Když platnost certifikátu Push vyprší, je nutné ho obnovit. Při obnovování je třeba použít stejné Apple ID jako při prvním vytvoření certifikátu Push.


## <a name="steps-to-get-your-certificate"></a>Kroky k získání certifikátu
Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), zvolte **registrace zařízení** > **registrace Apple** > **Apple MDM push Certificate**a pak postupujte podle těchto kroků v [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>Krok 1: Udělte Microsoftu oprávnění k odesílání informací o uživatelích a zařízeních společnosti Apple.
Vyberte možnost **Souhlasím.** a udělte tak Microsoftu oprávnění posílat data do Applu.

![Obrazovka Konfigurace certifikátu MDM Push Certificate s nenastaveným certifikátem MDM Push](./media/apple-mdm-push-certificate-get/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>Krok 2: Stáhněte si žádost o podepsání certifikátu (CSR) pro Intune, která je potřebná k vytvoření certifikátu Apple MDM Push Certificate.
Vyberte **Stáhnout CSR** a uložte si soubor žádosti .csr místně. Soubor slouží k vyžádání certifikátu vztahu důvěryhodnosti z portálu Apple Push Certificates Portal.

### <a name="step-3-create-an-apple-mdm-push-certificate"></a>Krok 3: Vytvořte certifikát Apple MDM Push Certificate.
Vyberte **Vytvořit certifikát MDM Push Certificate**. Tím přejdete na Apple Push Certificates Portal. Přihlaste se pomocí Apple ID společnosti a potom klikněte na **Vytvořit certifikát**. Vyberte **Vybrat soubor**, procházením vyhledejte soubor žádosti o podepsání certifikátu a potom zvolte **Nahrát**. Na stránce Potvrzení vyberte **Stáhnout**, stáhněte soubor certifikátu (.pem) a uložte ho do místního umístění.

> [!NOTE]
> Certifikát je přidružený k Apple ID, pomocí kterého byl vytvořen. Osvědčeným postupem je použití Apple ID společnosti pro úlohy správy a zajištění toho, že je poštovní schránka monitorována více osobami jako distribuční seznam. Nikdy nepoužívejte svoje osobní Apple ID.

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>Krok 4: Zadejte Apple ID, které jste použili k vytvoření certifikátu Apple MDM Push Certificate.
Poznamenejte si toto ID jako připomenutí na dobu, kdy bude třeba obnovit tento certifikát.

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>Krok 5: Procházením vyhledejte certifikát Apple MDM Push Certificate, který chcete nahrát.
Přejděte k souboru certifikátu (.pem), zvolte **Otevřít** a pak zvolte **Nahrát**. Pomocí certifikátu Push Certificate může Intune zaregistrovat a spravovat zařízení Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Obnovení certifikátu Apple MDM Push Certificate
Certifikát Apple MDM Push Certificate je platný po dobu jednoho roku a je potřeba ho každý rok obnovit, aby nedošlo k přerušení správy zařízení s iOSem a macOS. Pokud platnost certifikátu vyprší, nelze zaregistrovaná zařízení Apple kontaktovat.

Certifikát je přidružený k Apple ID, pomocí kterého byl vytvořen. Obnovte MDM Push Certificate pomocí stejného Apple ID, které jste použili k jeho vytvoření.

1. Přihlaste se k [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), zvolte **registrace zařízení** > **registrace Apple**a pak zvolte dlaždici **Apple MDM push Certificate** v oblasti Podrobnosti.
2. Vyberte **Stáhnout CSR** a uložte si soubor žádosti .csr místně. Soubor slouží k vyžádání certifikátu vztahu důvěryhodnosti z portálu Apple Push Certificates Portal.
3. Vyberte **Vytvořit certifikát MDM Push Certificate**. Tím přejdete na Apple Push Certificates Portal. Najděte certifikát, který chcete obnovit, a vyberte **Obnovit**.
4. Na obrazovce **Prodloužit platnost certifikátu MDM Push Certificate** zadejte poznámky, které vám v budoucnosti pomůžou certifikát identifikovat, vyberte **Zvolit soubor**, přejděte na nový soubor žádosti, který jste stáhli, a zvolte **Nahrát**.
   > [!TIP]
   > Certifikát je možné identifikovat podle jeho UID. Identifikátor GUID, který je součástí identifikátoru UID, najdete v podrobnostech certifikátu v **ID subjektu**. Můžete také na zaregistrovaném zařízení s iOSem přejít na **Nastavení** > **Obecné** > **Správa** **zařízení** > **Profil správy** > **Další podrobnosti** > **Profil správy**. Položka na druhém řádku, **Téma**, obsahuje jedinečný identifikátor GUID, který můžete porovnat s certifikátem na portálu Apple Push Certificates.
 
6. Na obrazovce **Potvrzení** vyberte **Stáhnout** a uložte si soubor .pem místně.
7. V [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)vyberte ikonu procházení **Apple MDM push Certificate** , vyberte soubor. pem stažený od společnosti Apple a zvolte **nahrát**.

Apple MDM Push Certificate se zobrazí se stavem **Aktivní** a do vypršení jeho platnosti zbývá 365 dnů.