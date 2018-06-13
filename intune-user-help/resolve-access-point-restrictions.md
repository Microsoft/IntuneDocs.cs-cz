---
title: Řešení omezení přístupového bodu nastavených v Intune
description: Podívejte se na tři běžné zprávy týkající se zásad omezení přístupového bodu Intune a zjistěte, jak je řešit.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.openlocfilehash: a6f5fb0ae4ab5f4f5cafbba6122c0b42e4591c4b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745121"
---
# <a name="resolve-access-point-restrictions"></a>Řešení omezení přístupového bodu

Organizace můžou omezit umístění, ze kterých zařízení můžou přistupovat k firemním datům.
Když organizace tato *omezení přístupového bodu* konfigurují, určí sadu schválených síťových umístění.  

Pokud se pokusíte připojit k nerozpoznané nebo neschválené síti, můžete obdržet jednu nebo více následujících zpráv:

* Omezení přístupového bodu nejsou nastavená.
* Nejste připojení ke schválené síti.
* Došlo k chybě a omezení přístupového bodu nešla vynutit.

 Tabulky níže obsahují jednotlivé zprávy, co znamenají a jak můžete zase získat přístup k pracovním prostředkům.

## <a name="access-point-restrictions-not-set-up"></a>Omezení přístupového bodu nejsou nastavená  
| Zpráva Portálu společnosti | Co tato zpráva znamená | Co byste měli udělat                                                               
|------------------------|--------------------------|--------------------------|
| **Omezení přístupového bodu nejsou nastavená. – Omezení přístupového bodu jsou aktivní a musí se nastavit.** | Vaše společnost nastavila pro vaše zařízení omezení přístupového bodu. Toto nastavení vyžaduje, aby aplikace Portál společnosti ověřila na vašem zařízení několik nastavení sítě. | Klepněte na **Vyřešit**. Aplikace Portál společnosti zkontroluje, jestli jste připojení k síti schválené společností. |

## <a name="not-connected-to-an-approved-network"></a>Nejste připojení ke schválené síti  

| Zpráva Portálu společnosti | Co tato zpráva znamená | Co byste měli udělat                                                                   
|------------------------|-----------------------------------|--------------------------|
| **Zařízení není připojené ke schválené síti. Připojte se ke schválené bezdrátové síti.** | Jste připojení k síti, která není schválená pro přístup k pracovním prostředkům. Pokud jste připojení k této síti, nemáte přístup k pracovním e-mailům, aplikacím a dalším chráněným firemním prostředkům. | Připojte se k síti schválené společností. Pak klepněte na **Vyřešit** a zkuste to znovu. |

## <a name="restrictions-couldnt-be-enforced"></a>Omezení nešla vynutit  

| Zpráva Portálu společnosti | Co tato zpráva znamená | Co byste měli udělat                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Omezení přístupového bodu nešla vynutit. Na Portálu společnosti došlo k chybě.** | Intune nemůže zjistit, jestli jste připojení ke schválené síti. Tato chyba může být důsledkem špatné kvality síťového připojení, nízkého stavu baterie, režimu spořiče baterie nebo chyby Portálu společnosti. | Ověřte, jestli máte silný síťový příjem. Vypněte režim spořiče baterie a ujistěte se, že zbývající výdrž baterie je alespoň 30 %. Pak klepněte na **Vyřešit** a zkuste to znovu. 

Potřebujete ještě další pomoc? Doporučujeme, abyste požádali o pomoc podporu vaší společnosti. Konkrétní kontaktní informace najdete na [webu Portál společnosti](https://portal.manage.microsoft.com/#HelpDeskDialog).