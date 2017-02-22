---
title: "Správa multilicenčních aplikací pro iOS | Intune Azure Preview | Dokumentace Microsoftu"
description: "Intune Azure Preview: Zjistěte, jak aplikace zakoupené v rámci multilicenčního programu z App Storu pro iOS zařízení synchronizovat s Intune a jak následně spravovat a sledovat jejich používání."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87250baede6c86e7ac5c402e79026908e712f48c
ms.openlocfilehash: 809fe8d8eea7e472d80f6ee22e26c1f376e870eb

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program"></a>Jak spravovat aplikace pro iOS zakoupené prostřednictvím multilicenčního programu


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

App Store pro iOS umožňuje pro aplikace, které chcete spouštět ve vaší společnosti, nakoupit víc licencí. Můžete tak snížit administrativní režii při sledování několika kopií koupených aplikací.

Microsoft Intune vám pomůže spravovat aplikace, které jste koupili prostřednictvím tohoto programu, importováním licenčních informací z App Storu, sledováním, kolik licencí jste už použili, a zabráněním instalace více aplikací, než na kolik máte licence.

> [!Important]
> V současné době Intune přiřazuje licence aplikací iOS typu VPP (Volume Purchase Program for Business) uživatelům, nikoli zařízením. Z tohoto důvodu musí koncoví uživatelé před instalací aplikace zadat své Apple ID a heslo.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Správa hromadně koupených aplikací pro zařízení s iOS
Více licencí k aplikacím pro iOS můžete zakoupit prostřednictvím programu [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) nebo [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). Součástí této operace je vytvoření účtu Apple VPP na webu Apple a odeslání tokenu Apple VPP do Intune.  Potom je možné synchronizovat informace o hromadném nákupu s Intune a sledovat využití aplikací, které jste tímto způsobem koupili.

## <a name="before-you-start"></a>Než začnete
Než začnete, musíte od společnosti Apple získat token VPP a odeslat ho do svého účtu Intune. Dále byste měli mít na paměti následující:

* Ke svému účtu Intune můžete přidružit několik tokenů multilicenčního programu.
* Pokud jste už dřív použili token VPP s jiným produktem, musíte pro Intune vygenerovat nový token.
* Tokeny mají platnost jeden rok.
* Ve výchozím nastavení se Intune synchronizuje se službou Apple VPP dvakrát denně. Ruční synchronizaci můžete spustit kdykoli.
* Po naimportování tokenu VPP do Intune neimportujte stejný token do žádného jiného řešení správy zařízení. Pokud byste to udělali, mohli byste ztratit přiřazení licence a uživatelských záznamů.
* Než začnete používat iOS VPP s Intune, odeberte všechny existující uživatelské účty VPP vytvořené pomocí jiných řešení správy zařízení (MDM). V rámci bezpečnostních opatření nebude Intune synchronizovat tyto uživatelské účty do Intune. Intune bude synchronizovat jen ta data ze služby Apple VPP, která byla vytvořená pomocí Intune.
* Aplikace iOS VPP se nedají přiřadit k zařízením zaregistrovaným pomocí programu DEP (Device Enrollment Protocol).

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Získání a odeslání tokenu Apple VPP

1. Přihlaste se k portálu Azure Portal.
2. Zvolte **Další služby** > **Jiné** > **Intune**.
3. V okně **Intune** zvolte **Spravovat aplikace**.
1.  V úloze **Spravovat aplikace** zvolte **Nastavení** > **Tokeny VPP pro iOS**.
2.  V okně se seznamem tokenů VPP klikněte na **Přidat**.
3.  V okně Nový token VPP zadejte následující informace:
    - **Soubor tokenu VPP** – pokud jste to ještě neudělali, zaregistrujte se v rámci programu Volume Purchase Program for Business nebo Volume Purchase Program for Education. Po zaregistrování si stáhněte token Apple VPP pro svůj účet a vyberte ho tady.
    - **Apple ID** – zadejte Apple ID účtu přidruženého k multilicenčnímu programu.
    - **Typ účtu VPP** – zvolte jednu z možností: **Obchodní** nebo **Vzdělávání**.
4. Po dokončení klikněte na **Nahrát**.

Token se zobrazí v okně se seznamem tokenů.


Data ukládaná společností Apple můžete kdykoli synchronizovat s Intune výběrem položky **Synchronizovat nyní**.

## <a name="to-assign-a-volume-purchased-app"></a>Přiřazení aplikace zakoupené v rámci multilicenčního programu

1. V úloze **Spravovat aplikace** zvolte **Spravovat** > **Licencované aplikace**.
2. V okně se seznamem aplikací zvolte aplikaci, kterou chcete přiřadit, a pak zvolte tlačítko se třemi tečkami (**...**). > **Přiřadit skupiny**.
3. V okně <*název aplikace*> – **Přiřazené skupiny** zvolte **Spravovat** > **Přiřazené skupiny**.
4. Zvolte **Přiřadit skupiny** a potom v okně **Vybrat skupiny** zvolte skupiny Azure AD, ke kterým chcete aplikaci přiřadit.
Musíte zvolit akci přiřazení **Povinné**. Instalace typu Dostupná se v současnosti nepodporují.
5. Až to budete mít, zvolte **Uložit**.

Informace, s kterými budete moct lépe sledovat přiřazování aplikací, najdete v článku [Jak sledovat přiřazení aplikací](monitor-apps.md).

## <a name="further-information"></a>Další informace

Když přiřazujete aplikaci s typem instalace **Požadovaná**, každý uživatel, který aplikaci nainstaluje, využije jednu licenci.

Když chcete licenci získat zpět, musíte nastavit akci přiřazení na **Odinstalovat**. Až se aplikace odinstaluje, licence se uvolní.

Když se uživatel s oprávněným zařízením poprvé pokusí o instalaci aplikace VPP, požádá se o připojení k programu Apple Volume Purchase. To je třeba provést před instalací aplikace.



<!--HONumber=Feb17_HO2-->

