---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "71830510"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Požadavky na přihlašovací údaje pro Azure AD a Intune

Ověřování a autorizace jsou založené na přihlašovacích údajích Azure AD a řízení přístupu na základě role (RBAC) Intune. Ve výchozím nastavení mají všichni globální správci a správci služby Intune pro vašeho tenanta přístup k datovému skladu. Role Intune můžete použít k poskytnutí přístupu pro další uživatele tak, že jim udělíte přístup k prostředku **Datový sklad Intune**.

Požadavky pro přístup k datovému skladu Intune (včetně rozhraní API) jsou:

- Uživatel musí být jedním z těchto uživatelů:
  - Globální správce Azure AD
  - Správce služby Intune
  - Uživatel s přístupem na základě role k prostředku **Datový sklad Intune**
  - Ověření bez účasti uživatele pomocí [ověřování pouze na úrovni aplikace](../developer/data-warehouse-app-only-auth.md) 
