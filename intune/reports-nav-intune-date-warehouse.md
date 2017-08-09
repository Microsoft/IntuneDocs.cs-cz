---
title: "Rozhraní API datového skladu Intune | Dokumentace Microsoftu"
description: "Rozhraní API můžete používat k vytváření sestav poskytujících přehled o podnikovém mobilním prostředí."
keywords: "Datový sklad Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5f03fd3a1557ef5d013fe695016ed0e3b119ee62
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2017
---
#  <a name="intune-data-warehouse-api"></a>Rozhraní API datového skladu Intune

Rozhraní API datového skladu Intune umožňuje přistupovat k datům Intune ve strojově čitelném formátu pro použití ve vašem oblíbeném analytickém nástroji. Rozhraní API můžete používat k vytváření sestav poskytujících přehled o podnikovém mobilním prostředí. Rozhraní API používá protokol OData, který dodržuje standardní vzory pro:

  -   Hlavičky žádostí a odpovědí
  -   Stavové kódy
  -   Metody HTTP
  -   Konvence URL
  -   Typy médií
  -   Formáty datových částí
  -   Možnosti dotazu

OData (Open Data Protocol) je standard organizace OASIS (Organization for the Advancement of Structured Standards), který definuje osvědčené postupy pro vytváření a využívání rozhraní API RESTful. Datový sklad Intune používá OData verze 4.0.

Tato část s referenčními informacemi obsahuje přehled koncových bodů, podporovaných metod HTTP, formátů návratových datových částí a dokumentace datového modelu datového skladu Intune.

> [!Important]  
> Nejnovější funkce datového skladu můžete vyzkoušet pomocí beta verze. Pokud chcete použít beta verzi, musí adresa URL obsahovat parametr dotazu `api-version=beta`. Beta verze nabízí funkce dřív, než budou všeobecně dostupné jako podporované služby. S tím, jak Intune přidává nové funkce, se může měnit chování a kontrakty dat beta verze. Jakýkoli vlastní kód nebo nástroje pro vytváření sestav závislé na beta verzi můžou přestat v probíhajících aktualizacích fungovat. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

<!-- ## OData custom client

You can access the Intune Data Warehouse data model through RESTful endpoints. To gain access to your data, your client must authorize with Microsoft Azure Active Directory (Azure AD) using OAuth 2.0. You first set up a web app and a client app in Azure, grant permissions to the client. Your local client will get authorization, can then communicate with the Data Warehouse endpoints.

For more information, see [Get data from the Data Warehouse API with a REST client](Get-data-REST.md) -->

## <a name="interacting-with-the-api"></a>Interakce s rozhraním API

Rozhraní API vyžaduje autorizaci pomocí Azure AD. Azure AD používá OAuth 2.0. Po autorizaci můžete získat data z rozhraní API pomocí příkazu HTTP GET a kontaktovat zveřejněné kolekce entit. Podrobnosti najdete v tématech:

 -  [Autorizace](reports-api-url.md)
 -  [Struktura adresy URL rozhraní API](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Datový model datového skladu Intune

OData definuje abstraktní datový model a protokol, který umožní jakémukoli klientovi přistupovat k informacím zveřejněným jakýmkoli zdrojem dat. Téma dokumentace týkající se datového modelu obsahuje vysvětlení oborů názvů, entit a návratových objektů v datovém modelu datového skladu Intune. Další informace najdete v tématu [Datový model datového skladu](reports-ref-data-model.md).

## <a name="for-more-information"></a>Další informace

[Scénáře ověřování pro Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData verze 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  