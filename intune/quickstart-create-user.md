---
title: 'Rychlý start: Vytvoření uživatele v Intune'
description: 'Rychlý start: Vytvoření uživatele v Intune'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: b5653c67766a3312cf7ce2872e8b0cd4301b0e8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189485"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Rychlý start: Vytvoření uživatele a přiřazení licence tomuto uživateli

V tomto rychlém startu vytvoříte uživatele a potom mu přiřadíte licenci. Při používání Intune musí mít uživatelský účet každý uživatel, který má mít přístup k firemním datům. Správci Intune později můžou tyto uživatele nakonfigurovat a spravovat tak řízení přístupu.

Pokud nemáte předplatné Intune, [zaregistrujte si bezplatný zkušební účet](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Přihlášení k Intune

Přihlaste se k [Intune](https://aka.ms/intuneportal) jako [globální správce nebo jako správce služby Intune](users-add.md#types-of-administrators). Pokud jste vytvořili zkušební předplatné Intune, účet, z něhož jste toto předplatné vytvořili, je globálním správcem.

## <a name="create-a-user"></a>Vytvoření uživatele

Aby se uživatelé mohli zaregistrovat do správy zařízení Intune, musí mít uživatelský účet.

1. V Intune zvolte **Uživatelé** > **Všichni uživatelé** > **Nový uživatel**.
![Prohlížeč](media/quickstart-create-user/create-user.png)
2. Do pole **Jméno** zadejte jméno, například *Dewey Kellum*.
3. Do pole **Uživatelské jméno** zadejte identifikátor uživatele, například Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Pokud jste nenakonfigurovali název domény zákazníka, použijte název ověřené domény, kterou jste použili k vytvoření předplatného Intune (nebo [bezplatného zkušebního předplatného](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Zvolte **Zobrazit heslo** a poznamenejte si automaticky vygenerované heslo, abyste se mohli přihlásit k testovacímu zařízení.
5. Zvolte **Vytvořit**.

## <a name="assign-a-license-to-the-user"></a>Přiřazení licence uživateli

Po vytvoření uživatele musíte použít [portál Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), abyste na něm danému uživateli přiřadili licenci Intune. Bez přiřazení licence si uživatelé nemůžou svoje zařízení zaregistrovat do Intune. 

1. Přihlaste se k [portálu Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854). K přihlášení použijte stejné přihlašovací údaje jako pro Intune.
2. Zvolte **Uživatelé** > **Aktivní uživatelé** > vyberte uživatele, kterého jste právě vytvořili.
3. Vedle možnosti **Licence na produkty** vyberte **Upravit**.
4. V části **Umístění** zvolte umístění pro daného uživatele.
5. Vedle licence na Intune (případně jiné licence, kterou máte a která zahrnuje Intune) klikněte na **Zapnuto**. Zobrazený [název produktu](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** slouží jako plán služeb ve správě Azure. 

   > [!NOTE]
   > Toto nastavení použije pro tohoto uživatele jednu licenci. Pokud používáte zkušební prostředí, můžete tuto licenci později znovu přiřadit skutečnému uživateli v živém prostředí.
6. Zvolte **Uložit** > **Zavřít**.

U nového aktivního uživatele Intune se nyní zobrazí, že používá licenci **Intune**.

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud tohoto uživatele už nepotřebujete, můžete ho odstranit. Přejděte na [portál Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) a zvolte **Uživatelé** > **Aktivní uživatelé** > *vyberte uživatele ze seznamu* > **Odstranit uživatele** > **Odstranit uživatele** > **Potvrdit změny** > **Zavřít**.

## <a name="next-steps"></a>Další postup

V tomto rychlém startu jste vytvořili uživatele a přiřadili mu licenci. Další informace o přidání uživatelů do Intune najdete v článku [Přidání uživatelů a udělení oprávnění pro správu v Intune](users-add.md).

Pokud chcete postupovat podle této série rychlých startů Intune, pokračujte k dalšímu rychlému startu.

> [!div class="nextstepaction"]
> [Rychlý start: Vytvoření skupiny pro správu uživatelů](quickstart-create-group.md)