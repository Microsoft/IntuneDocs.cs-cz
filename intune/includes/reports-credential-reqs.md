<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Požadavky na přihlašovací údaje pro Azure AD a Intune

Ověřování a autorizace jsou založené na přihlašovacích údajích Azure AD a řízení přístupu na základě role (RBAC) Intune. Ve výchozím nastavení mají všichni globální správci a správci služby Intune pro vašeho tenanta přístup k datovému skladu. Role Intune můžete použít k poskytnutí přístupu pro další uživatele tak, že jim udělíte přístup k **prostředku generování sestav**.

Požadavky pro přístup k datovému skladu Intune (včetně rozhraní API) jsou:

  -  Licence Intune musí být přiřazená uživateli.
  -  Uživatel musí být jedním z těchto uživatelů:
      -  Globální správce Azure AD
      -  Správce služby Intune
      -  Uživatel s přístupem na základě role k prostředku **Sestavy**