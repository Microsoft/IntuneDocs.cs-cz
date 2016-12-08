---
title: "Nastavení zásad Exchange ActiveSync | Microsoft Intune"
description: "Pomocí zásady Intune pro Exchange ActiveSync můžete nakonfigurovat nastavení, které vám umožní ovládat funkce v zařízeních spravovaných protokolem Exchange ActiveSync."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 770871d8cc7a32fb54ef01fb9ac84b1fdee2ec90


---

# Nastavení zásad Exchange ActiveSync v Microsoft Intune
Pomocí zásady pro Microsoft Intune **Exchange ActiveSync** můžete nakonfigurovat nastavení, které vám umožní ovládat řadu funkcí v zařízení spravovaných protokolem Exchange ActiveSync.


## Nastavení hesla

|Název nastavení|Podrobnosti
|----------------|---|
|**Vyžadovat heslo k odemknutí mobilních zařízení**|Určuje, jestli zařízení musí být zamčená s použitím hesla.<br>(Nevztahuje se na zařízení s Windows RT.)|
|**Vyžadovaný typ hesla**|Určuje typ hesla, které se bude vyžadovat, například jenom číslice nebo alfanumerické znaky.|
|**Minimální délka hesla**|Určuje minimální počet znaků, které musí heslo zařízení obsahovat.|
|**Povolit jednoduchá hesla**|Určuje, jestli můžete používat jednoduchá hesla, jako 0000 a 1234.|
|**Počet povolených opakovaných neúspěšných přihlášení, než bude zařízení vymazáno**|Určuje, kolikrát může uživatel zadat nesprávné heslo, než se zařízení vymaže.|
|**Omezená platnost hesla (ve dnech)**|Určuje počet dní, po jejichž uplynutí bude nutné změnit heslo zařízení.
|**Pamatovat si historii hesel**|Určuje, jestli má být povolené použití dříve použitých hesel.|
|**Pamatovat si historii hesel** – **Zabránit opětovnému použití předchozích hesel**|Určuje počet dříve použitých hesel, které nejde znovu použít.|
|**Počet minut nečinnosti před vyžadováním hesla**|Určuje dobu, po kterou musí být zařízení v nečinnosti, než se uzamkne jeho obrazovka.

## Nastavení šifrování

|Název nastavení|Podrobnosti|
|----------------|---|
|**Vyžadovat šifrování u mobilního zařízení**<sup>1</sup>|Vyžaduje šifrování dat na zařízení, pokud je podporované.<br><br>Pro zařízení s Windows Phone 8 je potřeba nastavit hodnotu **Ano**.<br /><br />Pokud chcete povolit šifrování na zařízeních iOS, povolte nastavení **Vyžadovat heslo k odemknutí mobilních zařízení**.|
|**Vyžadovat šifrování u paměťových karet**|Vyžaduje šifrování dat uložených v externích úložištích, jako je karta SD (u podporovaných zařízení).
<sup>1</sup> Další informace pro zařízení s Windows 8.1

-   Pokud chcete vynutit šifrování na zařízeních s Windows 8.1, musíte na každé zařízení nainstalovat [aktualizaci MDM klienta pro Windows z prosince 2014](http://support.microsoft.com/kb/3013816).

-   Pokud toto nastavení povolíte pro zařízení s Windows 8.1, všichni uživatelé zařízení musí mít účet Microsoft.

-   Pokud chcete, aby šifrování fungovalo pro zařízení s Windows 8.1, musí splňovat hardwarové požadavky certifikace Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/).

-   Pokud vynutíte šifrování na zařízení s Windows 8.1, je obnovovací klíč přístupný jenom uživatelům s účtem Microsoft, ke kterému přistupují z účtu OneDrive. Tento klíč se nedá obnovit jménem uživatele.

## Nastavení e-mailu

|Název nastavení|Podrobnosti
|----------------|---|
|**Povolit uživatelům stahovat přílohy e-mailů**|Určuje, jestli lze do zařízení stahovat přílohy e-mailu.|
|**Interval synchronizace e-mailu**|Určuje počet dnů přijatých e-mailů, které budou synchronizované v zařízení.
|**Povolit mobilním zařízením, která plně nepodporují nastavení Exchange ActiveSync, synchronizaci se serverem Exchange**|Určuje, jestli má mít Exchange povolený přístup k zařízením, která nepodporují jedno nebo více nastavení Exchange ActiveSync.

## Nastavení prohlížeče

|Název nastavení|Podrobnosti
|----------------|---|
|**Povolit webový prohlížeč**|Určuje, jestli je možné použít webový prohlížeč v zařízení.<br>(Není dostupné pro Windows RT nebo Windows Phone.)

## Nastavení hardwaru

|Název nastavení|Podrobnosti
|----------------|---|
|**Povolit fotoaparát**|Určuje, jestli je možné použít fotoaparát v zařízení.<br>(Není dostupné pro Windows RT nebo Windows Phone.)



### Související témata
[Správa nastavení a funkcí v zařízeních pomocí zásad Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Oct16_HO4-->

