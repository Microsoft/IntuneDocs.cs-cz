---
title: "Datový model datového skladu | Dokumentace Microsoftu"
description: "Datový sklad Intune denně vzorkuje data, aby mohl poskytovat historický přehled průběžně se měnícího mobilního prostředí."
keywords: "Datový sklad Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d56935bc2828273af28323e40d9f3b4e2bd84025
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2017
---
# <a name="data-warehouse-data-model"></a>Datový model datového skladu

Datový sklad Intune denně vzorkuje data, aby mohl poskytovat historický přehled průběžně se měnícího mobilního prostředí.

Data z vašeho tenanta se přidají do datového skladu. Sklad je sada entit a relací, které mají smysl pro typ otázek, které chcete položit. Můžete se například podívat na počet instalací interně vyvinuté aplikace pro Android za den během posledního týdne, abyste mohli vyhodnotit, jestli se jedná o rostoucí trend instalací. Struktura datového skladu umožňuje získat přehled o mobilním prostředí. Analytické nástroje, jako je například Microsoft Power BI, mohou používat datový model datového skladu k vytvoření vizualizací a dynamických řídicích panelů.

Struktura datového skladu Intune používá model hvězdicového schématu. Hvězdicové schéma organizuje fakta v dimenzi času. *Faktem* je v kontextu modelu kvantitativní míra, jako například počet zařízení, počet aplikací nebo čas registrace. *Dimenzí* je v kontextu modelu sada kategorií a jejich hierarchická relace. Dny jsou například seskupeny do měsíců a měsíce zase do let. Model hvězdicového schématu je optimalizovaný pro flexibilitu a analýzu dat, abyste mohli vytvářet sestavy potřebné k pochopení vyvíjejícího se mobilního prostředí.

Sklad zveřejňuje data v následujících kategoriích vysoké úrovně:
  -  Aplikace se zapnutou ochranou aplikací a využití
  -  Zaregistrovaná zařízení, vlastnosti a inventář
  -  Inventář aplikací a softwaru
  -  Konfigurace zařízení a zásady dodržování předpisů

**Sady entit datového modelu**

Sady entit se v datovém modelu nazývají kolekce entit. Tyto sady obsahují entity, které definují data shromážděná v modelu. Každá sada entit poskytuje přístupový bod do datového modelu datového skladu. Můžete se podívat na podrobnosti o následujících kategoriích entit:

  -  [Datum](reports-ref-date.md)
  -  [Uživatel](reports-ref-user.md)
  -  [Správa mobilních aplikací (MAM)](reports-ref-mobile-app-management.md)
  -  [Zařízení](reports-ref-devices.md)
  -  [Aplikace](reports-ref-application.md)
  -  [Zásady](reports-ref-policy.md)

<!-- ## Data Model relationships

For more information on the relationships in the data model, see [Relationships of Entities](). -->