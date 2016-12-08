---
title: "Nasazení aplikací | Microsoft Intune"
description: "Toto téma vysvětluje koncepty, kterým je třeba porozumět před zahájením nasazování aplikací s Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: eedf7db0a974f9a0aa0a21b27b64ed8b4a91b378


---

# Nasazení aplikací s Microsoft Intune

Toto téma vysvětluje některé koncepty, kterým je třeba porozumět před zahájením nasazování aplikací s Microsoft Intune.


## Akce nasazení aplikace
Při nasazování aplikací můžete zvolit jednu z následujících akcí nasazení:

-   **Požadovaná instalace** – Aplikace se nainstaluje do zařízení bez nutnosti zásahu uživatele.

    > [!TIP]
    > Pro zařízení s iOS, která nejsou v dohledovém režimu, a pro všechna zařízení s Androidem, musí uživatel aplikaci před instalací přijmout.
    >
    >  Pokud uživatel odinstaluje aplikaci, kterou jste nasadili jako požadovanou instalaci, Intune ji při příštím cyklu inventáře, který obvykle probíhá každých sedm dní, znovu automaticky nainstaluje.

-   **Dostupná instalace** – Aplikace se zobrazuje na podnikovém portálu a uživatelé ji můžou instalovat na vyžádání.

-   **Odinstalace** – Aplikace se ze zařízení odinstaluje.

-   **Není k dispozici** – Aplikace se nezobrazuje na podnikovém portálu a není nainstalovaná na žádném zařízení.

#### Zjistěte, které akce nasazení jsou dostupné pro jednotlivé typy instalačních programů:

|Typ instalačního programu|Požadovaná instalace|Dostupná instalace|Odinstalovat|Není k dispozici|
|------------------|--------------------|---------------------|-------------|------------------|
|Balíček aplikací pro Windows (nasazený pro skupinu uživatelů)|Ano|Ano|Ano|Ano|
|Balíček aplikací pro Windows (nasazený pro skupinu zařízení)|Ano|Ne|Ano|Ano|
|Balíček aplikace pro mobilní zařízení (nasazený pro skupinu uživatelů)|Ano|Ano|Ano|Ano|
|Balíček aplikace pro mobilní zařízení (nasazený pro skupinu zařízení)|Ano|Ne|Ano|Ano|
|Instalační služba systému Windows (nasazené pro skupinu uživatelů)|Ne|Ano|Ne|Ano|
|Instalační služba systému Windows (nasazené pro skupinu zařízení)|Ano|Ne|Ano|Ano|
|Externí odkaz (nasazený pro skupinu uživatelů)|Ne|Ano|Ne|Ano|
|Externí odkaz (nasazený pro skupinu zařízení)|Ne|Ne|Ne|Ne|
|Spravovaná aplikace pro iOS z App Storu (nasazené pro skupinu uživatelů)|Ano|Ano|Ano|Ano|
|Spravovaná aplikace pro iOS z App Storu (nasazené pro skupinu zařízení)|Ano|Ne|Ano|Ano|
> [!TIP]
> Když nasazujete aplikace a vyberete jak skupiny uživatelů, tak zařízení, můžete aplikaci nasadit jenom s možností **Dostupná instalace**.

## Konflikty nasazení
Při dvou nasazeních platí při přijetí stejné akce nasazení na zařízení následující pravidla:

-   Nasazení pro skupinu zařízení má přednost před nasazením pro skupinu uživatelů. Pokud je ale aplikace nasazená pro skupinu uživatelů pomocí akce nasazení **Dostupné** a v případě, že je stejná aplikace nasazená taky pro skupinu zařízení pomocí akce nasazení **Není k dispozici**, aplikace bude dostupná na podnikovém portálu a uživatelé si ji můžou nainstalovat.

-   Akce instalace má přednost před akcí odinstalace.

-   Pokud zařízení přijme požadovanou i dostupnou instalaci, akce se zkombinují. Jinými slovy uživatel může nainstalovat dostupnou aplikaci z Portálu společnosti před zahájením požadované instalace.


## Další kroky

Přečtěte si, jak [nasazovat aplikace v Microsoft Intune](deploy-apps-in-microsoft-intune.md).



<!--HONumber=Oct16_HO4-->

