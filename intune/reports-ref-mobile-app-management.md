---
title: "Správa mobilních aplikací (MAM) | Dokumentace Microsoftu"
description: "Téma referenčních informací ke kategorii Správa mobilních aplikací pro kolekce entit v rozhraní API datového skladu Intune"
keywords: "Datový sklad Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 44358d68a653760804f11668ab64d30ebf7ae9eb
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referenční informace o entitách správy mobilních aplikací (MAM)

Kategorie **Správa mobilních aplikací** obsahuje entity pro mobilní aplikace, například:

  -  Aplikace
  -  instancí
  -  Stav přihlášení
  -  Stav
  -  Stav zásad
  -  Stav zápisu
  -  Typy platformy

## <a name="mamapplication"></a>MamApplication

Entita **MamApplication** obsahuje seznam obchodních aplikací, které jsou spravované přes správu mobilních aplikací (MAM) bez registrace ve vašem podniku.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| ApplicationKey |Jedinečný identifikátor aplikace MAM v datovém skladu |123 |
| ApplicationName |Název aplikace MAM |Word |
| ApplicationId |ID aplikace pro danou aplikaci MAM |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Určuje, jestli je tento záznam aplikace MAM aktualizovaný. True – aplikace MAM má v této tabulce nový záznam s aktualizovanými poli. False – jedná se o nejnovější záznam pro tuto aplikaci MAM. |True nebo False |
| StartDateInclusiveUTC |Datum a čas ve standardu UTC, kdy se tato aplikace MAM v datovém skladu vytvořila |23.11.2016 12:00:00 |
| DeletedDateUTC |Datum a čas ve standardu UTC, kdy došlo ke změně vlastnosti IsDeleted na hodnotu True |23.11.2016 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum a čas ve standardu UTC, kdy se tato aplikace MAM v datovém skladu naposledy změnila |23.11.2016 12:00:00 |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

Entita **MamApplicationInstance** obsahuje seznam aplikací spravovaných přes správu mobilních aplikací (MAM) jako jedinečné instance pro uživatele a zařízení. Všichni uživatelé a zařízení, kteří jsou v této entitě uvedení, jsou chránění, protože mají přiřazenou aspoň jednu zásadu MAM.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| ApplicationInstanceKey |Jedinečný identifikátor instance aplikace MAM v datovém skladu – náhradní klíč |123 |
| UserId |ID uživatele, který má tuto aplikaci MAM nainstalovanou |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |Jedinečný identifikátor instance aplikace MAM – podobá se vlastnosti ApplicationInstanceKey, ale tento identifikátor představuje přirozený klíč |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |ID aplikace pro danou aplikaci MAM |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |Verze aplikace pro danou aplikaci MAM |2 |
| CreatedDate |Datum vytvoření daného záznamu instance aplikace MAM Hodnota může být null. |23.11.2016 12:00:00 |
| Platforma |Platforma zařízení, na kterém je daná aplikace MAM nainstalovaná |2 |
| PlatformVersion |Verze platformy zařízení, na kterém je daná aplikace MAM nainstalovaná |2.2 |
| SdkVersion |Verze sady SDK MAM, pomocí které byla daná aplikace MAM zabalena |3.2 |
| DeviceId |ID zařízení, na kterém je daná aplikace MAM nainstalovaná |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Název zařízení, na kterém je daná aplikace MAM nainstalovaná |MojeZařízení |
| IsDeleted |Určuje, jestli je tento záznam instance aplikace MAM aktualizovaný. True – tato instance aplikace MAM má v této tabulce nový záznam s aktualizovanými poli. False – jedná se o nejnovější záznam pro tuto instanci aplikace MAM. |True nebo False |
| StartDateInclusiveUtc |Datum a čas ve standardu UTC, kdy se tato instance aplikace MAM v datovém skladu vytvořila |23.11.2016 12:00:00 |
| DeletedDateUtc |Datum a čas ve standardu UTC, kdy došlo ke změně vlastnosti IsDeleted na hodnotu True |23.11.2016 12:00:00 |
| RowLastModifiedDateTimeUtc |Datum a čas ve standardu UTC, kdy se tato instance aplikace MAM v datovém skladu naposledy změnila |23.11.2016 12:00:00 |

## <a name="mamcheckin"></a>MamCheckin

Entita **MamCheckin** představuje data shromážděná v době, kdy se instance aplikace MAM přihlásila ke službě Intune. 

> [!Note]  
> Pokud se instance aplikace přihlásí několikrát denně, uloží se to v datovém skladu jako jediné přihlášení.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| DateKey |Klíč data, kdy se přihlášení aplikace MAM v datovém skladu zaznamenalo | 20160703 |
| ApplicationInstanceKey |Klíč instance aplikace, který je k tomuto přihlášení aplikace MAM přidružený |2.5.1900 12:00:00 |
| UserKey |Klíč uživatele, který je k tomuto přihlášení aplikace MAM přidružený |12.1.1900 12:00:00 |
| ApplicationKey |Klíč aplikace MAM, která se přihlásila |10.1.1900 12:00:00 |
| DeviceHealthKey |Klíč pro stav, který je k tomuto přihlášení aplikace MAM přidružený |2.1.1900 12:00:00 |
| PlatformKey |Představuje platformu zařízení, které je k tomuto přihlášení aplikace MAM přidružené. |1.1.1900 12:00:00 |
| EffectiveAppliedPolicyKey |Představuje platné použité zásady, které jsou k tomuto přihlášení aplikace MAM přidružené. Platné použité zásady jsou výsledkem sloučení všech zásad, které jsou pro konkrétní aplikaci a uživatele relevantní. |2.5.1900 12:00:00 |
| LastCheckInDate |Datum a čas posledního přihlášení dané aplikace MAM Hodnota může být null. |23.11.2016 12:00:00 |

## <a name="mamdevicehealth"></a>MamDeviceHealth

Entita **MamDeviceHealth** představuje zařízení, na kterých jsou nasazené zásady správy mobilních aplikací (MAM), i když jsou tato zařízení s jailbreakem.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| DeviceHealthKey |Jedinečný identifikátor zařízení a jeho přidruženého stavu v datovém skladu – náhradní klíč |1.1.1900 12:00:00 |
| DeviceHealth |Jedinečný identifikátor zařízení a jeho přidruženého stavu – podobá se vlastnosti DeviceHealthKey, ale tento identifikátor představuje přirozený klíč |1.1.1900 12:00:00 |
| DeviceHealthName |Představuje stav zařízení. Není k dispozici – žádné informace o tomto zařízení nejsou dostupné. V pořádku – nejedná se o zařízení s jailbreakem. Není v pořádku – jedná se o zařízení s jailbreakem. |Není k dispozici, V pořádku, Není v pořádku |
| RowLastModifiedDateTimeUtc |Datum a čas ve standardu UTC, kdy se tento konkrétní stav zařízení MAM v datovém skladu naposledy změnil |23.11.2016 12:00:00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

Entita **MamEffectivePolicy** obsahuje seznam všech platných použitých zásad správy mobilních aplikací (MAM) ve vaší organizaci. Platné použité zásady jsou výsledkem sloučení všech zásad, které jsou pro konkrétní aplikaci a uživatele relevantní.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| EffectivePolicyKey |Jedinečný identifikátor platných zásad MAM v datovém skladu |2 |
| RealPolicyKey |Jedinečný identifikátor zásad MAM, které vytvořil pracovník oddělení IT |1 |
| RowCreatedDateTimeUtc |Datum a čas ve standardu UTC, kdy se tyto platné zásady MAM v datovém skladu vytvořily |23.11.2016 12:00:00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

Entita **MamGlobalApplication** obsahuje seznam aplikací pro Store, které jsou spravované přes správu mobilních aplikací (MAM) bez registrace ve vašem podniku.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| ApplicationKey |Jedinečný identifikátor aplikace pro Store v datovém skladu, který se označuje jako náhradní klíč |123 |
| ApplicationId |Jedinečný identifikátor aplikace pro Store. Tento identifikátor se podobá vlastnosti ApplicationKey, ale představuje přirozený klíč. |com.microsoft.skydrive.<ios> |
| ApplicationName |Název globální aplikace MAM |SkyDrive |
| RowLastModifiedDateTimeUtc |Datum a čas ve standardu UTC, kdy se tato konkrétní globální aplikace MAM v datovém skladu naposledy změnila |23.11.2016 12:00:00 |

## <a name="mamplatform"></a>MamPlatform

Entita **MamPlatform** obsahuje seznam názvů a typů platforem, na kterých byla aplikace MAM nainstalována.

| Vlastnost | Popis | Příklad |
|---------|------------|--------|
| PlatformKey |Jedinečný identifikátor platformy v datovém skladu – náhradní klíč |123 |
| Platforma |Jedinečný identifikátor platformy – podobá se vlastnosti PlatformKey, jedná se ale o přirozený klíč |123 |
| PlatformName |Název platformy |Není k dispozici, Žádný, Windows, IOS, Android |
| RowLastModifiedDateTimeUtc |Datum a čas ve standardu UTC, kdy se tato platforma v datovém skladu naposledy změnila |23.11.2016 12:00:00 |