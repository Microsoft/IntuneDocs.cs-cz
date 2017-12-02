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
ms.openlocfilehash: a0d6bcb4ccac3563dd642ec0ad621645b7053dea
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/20/2017
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

## <a name="odata-custom-client"></a>Vlastní klient OData

Datový model datového skladu Intune můžete zpřístupnit přes koncové body RESTful. Aby váš klient získal přístup k datům, musí se vůči službě Azure Active Directory (Azure AD) autorizovat protokolem OAuth 2.0. Nejprve nastavíte webovou aplikaci a klientskou aplikaci v Azure a udělíte oprávnění klientovi. Když místní klient získá autorizaci, může komunikovat s koncovými body datového skladu.

Další informace najdete v článku [Získání dat z rozhraní API datového skladu pomocí klienta REST](reports-proc-data-rest.md).

> [!Note]  
> Ukázky kódu najdete v [úložišti datového skladu Intune](https://github.com/Microsoft/Intune-Data-Warehouse) na GitHubu.

## <a name="interacting-with-the-api"></a>Interakce s rozhraním API

Rozhraní API vyžaduje autorizaci pomocí Azure AD. Azure AD používá OAuth 2.0. Po autorizaci můžete získat data z rozhraní API pomocí příkazu HTTP GET a kontaktovat zveřejněné kolekce entit. Podrobnosti najdete v tématech:

 -  [Autorizace](reports-api-url.md)
 -  [Struktura adresy URL rozhraní API](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Datový model datového skladu Intune

OData definuje abstraktní datový model a protokol, který umožní jakémukoli klientovi přistupovat k informacím zveřejněným jakýmkoli zdrojem dat. Téma dokumentace týkající se datového modelu obsahuje vysvětlení oborů názvů, entit a návratových objektů v datovém modelu datového skladu Intune. Další informace najdete v tématu [Datový model datového skladu](reports-ref-data-model.md).

## <a name="next-steps"></a>Další kroky

Další informace o práci s Azure AD najdete v článku o [scénářích ověřování pro Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

Prostředky OData najdete na [odata.org](http://www.odata.org).
  
Standard OData verze 4.0 je popsaný na stránce [OData verze 4.0] (http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  