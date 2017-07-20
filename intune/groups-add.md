---
title: "Nastavení omezení registrace v Intune"
titleSuffix: Intune on Azure
description: "Omezení registrace podle platformy a nastavení limitu počtu zařízení pro registraci zařízení v Intune \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2c9d10e4e2a1d2a745b9e327bf9a8a9cd99e5ce4
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2017
---
# <a name="add-groups-in-intune"></a>Přidání skupin do Intune
Služba Intune používá ke správě zařízení a uživatelů skupiny Azure Active Directory (AD). Jako správce Intune můžete nastavit skupiny tak, aby odpovídaly potřebám vaší organizace. Vytvořte skupiny, které uživatele nebo zařízení uspořádají podle zeměpisné polohy, oddělení nebo vlastností hardwaru. Skupiny použijte ke spravování úloh se škálováním. Například můžete nastavit zásady pro mnoho uživatelů nebo nasadit aplikace řadě zařízení.

Toto téma vysvětluje, jak do Intune přidat skupiny, které se mají používat.

Můžete přidat následující typy skupin:
- **Přiřazené skupiny** – Přidejte uživatele nebo zařízení do statické skupiny ručně.
- **Dynamické skupiny** – (Azure Active Directory Premium) Umožňují vám vytvořit skupiny pro uživatele nebo zařízení definované jednoduchými nebo pokročilými pravidly.

## <a name="add-a-new-group"></a>Přidání nové skupiny

Pomocí následujícího postupu vytvořte novou skupinu.
1. Na portálu Intune přejděte na **Skupiny** a potom v okně **Všechny skupiny** zvolte **Nová skupina**.
  ![Snímek obrazovky portálu Intune s vybranou možností Nová skupina](./media/groups-add-new.png)
2. Zadejte **název** a **popis** nové skupiny. Tyto vlastnosti se objeví pouze na portálu Intune a uživatelům se nezobrazí.

3. Zvolte **typ členství**:
  - **Přiřazené** – vytvoří skupinu z ručně přiřazených členů. Další informace o [přiřazených skupinách Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
  - **Dynamický uživatel** – vytvoří skupinu uživatelů definovanou **dynamickým dotazem**.
  - **Dynamické zařízení** – vytvoří skupinu zařízení definovanou **dynamickým dotazem**.

  ![Snímek obrazovky vlastností skupiny Intune s názvem, popisem, typem členství, možností povolení funkcí Office a členy](./media/groups-add-properties.png)

  Azure AD vám umožňuje vytvořit dynamické skupiny na základě pravidel, která definují členství. Naučte se [vytvářet dynamické skupiny podle atributů](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

4. Pokud chcete dát členům skupiny uživatelů přístup ke sdíleným aplikacím Office 365, můžete vybrat **Povolit funkce Office**.
5. Novou skupinu přidáte tlačítkem **Vytvořit**.

## <a name="see-also"></a>Související témata
[Správa přístupu k prostředkům pomocí skupin Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
[Začínáme se skupinami](groups-get-started.md)