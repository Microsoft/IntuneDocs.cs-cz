---
title: 'Kurz: Použití Autopilotu k registraci zařízení v Intune'
titleSuffix: Microsoft Intune
description: V tomto kurzu nastavíte Windows Autopilot pro registraci zařízení v Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39ea8b3859d3d2525433c4cafdf566e7a2c8d2ab
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509195"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Kurz: Použití Autopilotu k registraci zařízení s Windows v Intune

Windows Autopilot zjednodušuje registraci zařízení. S Microsoft Intune a Autopilotem můžete nová zařízení koncovým uživatelům poskytovat, aniž by bylo nutné vlastní image operačního systému vytvářet, udržovat a aplikovat.

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Přidat zařízení do Intune
> * Vytvořit skupinu zařízení Autopilot
> * Vytvořit profil nasazení Autopilotu
> * Přiřadit profil nasazení Autopilotu ke skupině zařízení
> * Distribuovat zařízení s Windows uživatelům

Pokud nemáte předplatné Intune, [zaregistrujte si bezplatný zkušební účet](../fundamentals/free-trial-sign-up.md).

Přehled výhod, scénáře a požadavky Autopilotu najdete v [přehledu Windows Autopilotu](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Požadované součásti
- [Nastavení automatické registrace Windows](../quickstart-setup-auto-enrollment.md)
- [Předplatné Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Přidání zařízení

Prvním krokem při nastavení Windows Autopilotu je přidání zařízení s Windows do Intune. Nemusíte dělat nic více, než vytvořit soubor CSV a naimportovat ho do Intune.

1. V libovolném textovém editoru vytvořte seznam hodnot oddělených čárkami (CSV), které identifikují zařízení s Windows. Použijte tento formát:
    
    *sériové číslo*, *Windows-ID produktu*, *hardware-hash*, *volitelná-Group-tag*
    
    První tři položky jsou povinné, ale značka skupiny (dříve známé "ID objednávky") je volitelná.

2. Soubor CSV uložte.

3. V [Intune na portálu Azure Portal](https://aka.ms/intuneportal) vyberte **Registrace zařízení** > **Registrace zařízení s Windows** > **Zařízení** > **Importovat**.

    ![Snímek obrazovky se zařízeními Windows Autopilot](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device.png)

4. V části **Přidat zařízení Windows Autopilot** vyhledejte uložený soubor CSV.

    ![Snímek obrazovky s přidáním zařízení Windows Autopilot](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. Pomocí **Importovat** zahajte import informací o zařízeních. Import může trvat několik minut.

4. Po dokončení importu vyberte možnost **registrace zařízení** > **registrace Windows** > **Windows autopilot** > **zařízení** > **Sync**. Zobrazí se zpráva, že synchronizace probíhá. Dokončení procesu může trvat několik minut v závislosti na tom, kolik zařízení synchronizujete.

5. Aktualizováním zobrazení zobrazte nová zařízení.

## <a name="create-an-autopilot-device-group"></a>Vytvořit skupinu zařízení Autopilot

Dále vytvořte skupinu zařízení a přidejte do ní zařízení Autopilot, která jste právě načetli.

1. V [Intune na portálu Azure Portal](https://aka.ms/intuneportal) zvolte **Skupiny** > **Nová skupina**.
2. V okně **Skupina**:
    1. Pro **Typ skupiny** zvolte **Zabezpečení**.
    2. Jako **Název skupiny** zadejte *Skupina Autopilot*. Jako **Popis skupiny** zadejte *Testovací skupina pro zařízení Autopilot*.
    3. Pro **Typ členství** zvolte **Přiřazeno**.
3. V okně **Skupina** zvolte **Členové** a do skupiny přidejte zařízení Autopilot. Zařízení Autopilot, která ještě nejsou zaregistrovaná, jsou zařízení, jejichž název se rovná sériovému číslu zařízení.
4. Zvolte **Vytvořit**.  

## <a name="create-an-autopilot-deployment-profile"></a>Vytvořit profil nasazení Autopilotu

Po vytvoření skupiny zařízení musíte vytvořit profil nasazení, abyste mohli zařízení Autopilot nakonfigurovat.

1. V [Intune na portálu Azure Portal](https://aka.ms/intuneportal) vyberte **Registrace zařízení** > **Registrace zařízení s Windows** > **Profily nasazení** > **Vytvořit profil**.
2. Na stránce **základy** zadejte **název**systému do pole *autopilot Profile*. Jako **Popis skupiny** zadejte *Testovací profil pro zařízení Autopilot*.
3. Nastavte možnost **Převést všechna cílová zařízení na Autopilot** na **Ano**. Toto nastavení zajistí, že všechna zařízení v seznamu se zaregistrují pomocí služby nasazení Autopilot. Vyřízení registrace trvá 48 hodin.
4. Vyberte **Další**.
5. Na stránce spouštěné při **prvním spuštění počítače (OOBE)** pro **režim nasazení**vyberte možnost **řízeno uživatelem**. Zařízení s tímto profilem se přidruží k uživateli, který zařízení registruje. Při registraci zařízení se musí zadat přihlašovací údaje uživatele.
6. V poli **Připojit k Azure AD jako** zvolte **Připojeno k Azure AD**.
7. Nakonfigurujte následující možnosti a nechte výchozí nastavení pro ostatní:
    - **Licenční smlouva s koncovým uživatelem (EULA)** : **Skrýt**
    - **Nastavení ochrany osobních údajů**: **Zobrazit**
    - **Typ uživatelského účtu**: **Standard**
8. Vyberte **Další**.
9. Na stránce **přiřazení** vyberte **vybrané skupiny** pro **přiřazení**.
10. Zvolte **Vybrat skupiny, které se mají zahrnout**, a pak zvolte **Skupina autopilot**.
11. Vyberte **Další**.
12. Na stránce **Revize + vytvořit** vyberte **vytvořit** a vytvořte profil.

## <a name="distribute-devices-to-users"></a>Distribuce zařízení uživatelům

Nyní můžete distribuovat zařízení s Windows uživatelům. Při prvním přihlášení systém Autopilot automaticky zařízení zaregistruje a nakonfiguruje. 

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud už nechcete používat zařízení autopilotu, můžete je odstranit.

1. Pokud jsou zařízení registrována v Intune, musíte je nejdřív [odstranit z portálu služby Azure Active Directory](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. V [Intune na portálu Azure Portal](https://aka.ms/intuneportal), vyberte **Registrace zařízení** > **Registrace zařízení s Windows** > **Zařízení**.

3. V části **Zařízení Windows Autopilot** vyberte zařízení, která chcete odstranit, a pak vyberte **Odstranit**.

4. Potvrďte odstranění pomocí **Ano**. Odstranění může trvat několik minut.

## <a name="next-steps"></a>Další kroky

Můžete si přečíst další informace o dalších možnostech dostupných pro Windows Autopilot.

> [!div class="nextstepaction"]
> [Článek s podrobnými informacemi o registraci pomocí Autopilotu](enrollment-autopilot.md)

