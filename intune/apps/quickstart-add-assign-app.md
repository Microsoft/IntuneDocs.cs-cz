---
title: Rychlý start – přidání a přiřazení klientské aplikace
titleSuffix: Microsoft Intune
description: V tomto rychlém startu použijete Microsoft Intune k přidání a přiřazení klientské aplikace.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ed8df1f7a9edb62b5c9c8a9050031aedea7397a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497650"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Rychlý start: Přidání a přiřazení klientské aplikace

V tomto rychlém startu použijete Intune k přidání a přiřazení klientské aplikace zaměstnancům vaší firmy. Jednou z priorit správce je zajistit, aby koncoví uživatelé měli přístup k aplikacím, které potřebují ke své práci. 

Pokud nemáte předplatné Intune, [zaregistrujte si bezplatný zkušební účet](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Požadované součásti

- Abyste mohli dokončit tento rychlý start, musíte [vytvořit uživatele](../fundamentals/quickstart-create-user.md), [vytvořit skupinu](../fundamentals/quickstart-create-group.md) a [zaregistrovat zařízení](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Přihlášení k Intune

Přihlaste se k [Intune](https://aka.ms/intuneportal) jako [globální správce nebo správce služby Intune](../fundamentals/users-add.md#types-of-administrators). Pokud jste vytvořili zkušební předplatné Intune, účet, z něhož jste toto předplatné vytvořili, je globálním správcem.

## <a name="add-the-client-app-to-intune"></a>Přidání klientské aplikace do Intune

Při zahrnutí aplikace může Intune spravovat aspekty této aplikace. 

Aplikaci přidáte do Intune následujícím postupem:
1. V [Intune](https://aka.ms/intuneportal) vyberte **Klientské aplikace** > **Aplikace** > **Přidat**. 
2. V oddílu **Sada Office 365** rozevíracího seznamu **Typ aplikace** vyberte **Windows 10**.
3. Vyberte **Nakonfigurovat sadu aplikací** a vyberte aplikace Office, které se mají přiřadit uživateli Intune.
4. Kliknutím na **OK** přijměte výchozí vybrané aplikace.
5. Vyberte **Informace o sadě aplikací**.
6. Jako **Název sady** zadejte **Sada aplikací Microsoft Office 365**.
7. Jako **Popis sady**zadejte **sadu aplikací systém Microsoft Office 365** .
8. Klikněte na **Ano** vedle možnosti **Zobrazit na Portálu společnosti jako vybranou aplikaci**.
9. Klikněte na **OK**.

    ![Snímek obrazovky s přidáním informací o aplikaci](./media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

10. Vyberte **Nastavení sady aplikací**.
11. V rozevíracím seznamu **Aktualizační kanál** vyberte **Měsíčně**.
12. Klikněte na **OK** > **Přidat**.

## <a name="assign-the-app-to-a-group"></a>Přiřazení aplikace ke skupině

Po přidání aplikace do Microsoft Intune ji můžete přiřadit ke skupinám uživatelů a zařízení.

> [!NOTE]
> Tento rychlý Start staví na předchozích rychlých startech v této sérii. Podrobnosti najdete v části [Požadavky](quickstart-add-assign-app.md#prerequisites) tohoto rychlého startu.

Aplikaci přiřadíte ke skupině následujícím postupem:
1. V [Intune](https://aka.ms/intuneportal) vyberte **Klientské aplikace** > **Aplikace**. 
2. Vyberte aplikaci, kterou chcete přiřadit ke skupině.
3. Kliknutím na **Přiřazení** > **Přidat skupinu** zobrazte okno **Přidat skupinu**.
4. V rozevíracím seznamu **Typ přiřazení** vyberte **K dispozici registrovaným zařízením**. 
5. Klikněte na **Zahrnuté skupiny** > **Vybrat skupiny, které se zahrnou** > **Testeři Contoso**.
6. Kliknutím na **Vybrat** > **OK** > **OK** > **Uložit** tuto skupinu přiřaďte.

Tuto aplikaci jste teď přiřadili ke skupině **Testeři Contoso**.

## <a name="install-the-app-on-the-enrolled-device"></a>Instalace aplikace na zaregistrované zařízení

Abyste mohli nainstalovat aplikaci **Úkoly Contoso** zpřístupněnou službou Intune, musíte nainstalovat a použít aplikaci Portál společnosti. Následujícím postupem ověřte, že je tato aplikace dostupná uživateli zaregistrovaného zařízení.

1. Přihlaste se k zaregistrovanému zařízení s desktopovou verzí Windows 10.

    > [!IMPORTANT]
    > Toto zařízení musí být [zaregistrované v Intune](../quickstart-enroll-windows-device.md). K zařízení se navíc musíte přihlásit pomocí účtu obsaženého ve skupině, kterou jste přiřadili k aplikaci.

2. V nabídce **Start** otevřete **Microsoft Store**. Pak vyhledejte aplikaci **Portál společnosti** a nainstalujte ji.
3. Spusťte aplikaci **Portál společnosti**.
4. Klikněte na aplikaci, kterou jste přidali pomocí Intune. V tomto rychlém startu jste přidali aplikaci **Sada aplikací Microsoft Office 365**.

    > [!NOTE]
    > Pokud jste uživateli Intune nepřiřadili úspěšně žádné aplikace, zobrazí se následující zpráva: *Váš správce IT pro vás nezpřístupnil žádné aplikace.*

5. Klikněte na tlačítko **Nainstalovat**.

Pokud potřeby vaší firmy vyžadují, abyste aplikaci Portál společnosti přiřadili zaměstnancům, můžete aplikaci Portál společnosti pro Windows 10 přiřadit ručně přímo z Intune. Další informace najdete v článku [Ruční přidání aplikace Portál společnosti pro Windows 10 pomocí Microsoft Intune](../company-portal-app.md).

## <a name="next-steps"></a>Další kroky

V tomto rychlém startu jste do Intune přidali aplikace, přiřadili tyto aplikace ke skupině a nainstalovali je na zaregistrované zařízení s desktopovou verzí Windows 10. Další informace o správě aplikací v Intune najdete v článku [Co je správa aplikací v Microsoft Intune?](app-management.md)

Pokud chcete postupovat podle této série rychlých startů Intune, pokračujte k dalšímu rychlému startu.

> [!div class="nextstepaction"]
> [Rychlý start: Vytvoření a přiřazení zásady ochrany aplikací](quickstart-create-assign-app-policy.md)