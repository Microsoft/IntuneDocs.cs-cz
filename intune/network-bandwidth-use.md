---
title: "Využití šířky pásma Intune"
description: "využití šířky pásma Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 030aa380a1491eb3be4fd8f480b0ddc9a7860448
ms.contentlocale: cs-cz
ms.lasthandoff: 06/08/2017


---

# <a name="intune-network-bandwidth-use"></a>Využití šířky pásma Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Tyto pokyny pomůžou správcům Intune porozumět požadavkům služby Intune na síť. Tyto informace můžete použít k pochopení požadavků na šířku pásma a nastavení IP adres a portů potřebných k nastavení proxy serverů.

## <a name="average-network-traffic"></a>Průměrné zatížení sítě
Tabulka uvádí přibližnou velikost a četnost u nejčastějšího obsahu přenášeného po síti u každého klienta.

> [!NOTE]
> Aby mohly počítače a mobilní zařízení přijímat potřebné aktualizace a obsah ze služby Intune, musí se pravidelně připojovat k Internetu. Čas potřebný k přijetí aktualizací nebo obsahu se bude lišit. Obecně ale platí, že by počítače a mobilní zařízení měly být trvale připojené k Internetu každý den alespoň jednu hodinu.

|Typ obsahu|Přibližná velikost|Četnost a podrobnosti|
|----------------|--------------------|-------------------------|
|Instalace klienta Intune<br /><br />**K instalaci klienta Intune se přidávají ještě tyto požadavky**|125 MB|**Jednou**<br /><br />Velikost souborů klienta ke stažení se liší podle operačního systému klientského počítače.|
|Registrační balíček klienta|15 MB|**Jednou**<br /><br />Další stahování je možné, pokud jsou pro tento typ obsahu dostupné aktualizace.|
|Agent Endpoint Protection|65 MB|**Jednou**<br /><br />Další stahování je možné, pokud jsou pro tento typ obsahu dostupné aktualizace.|
|Agent Operations Manageru|11 MB|**Jednou**<br /><br />Další stahování je možné, pokud jsou pro tento typ obsahu dostupné aktualizace.|
|Agent zásad|3 MB|**Jednou**<br /><br />Další stahování je možné, pokud jsou pro tento typ obsahu dostupné aktualizace.|
|Agent Vzdálené pomoci prostřednictvím nástroje Microsoft Easy Assist|6 MB|**Jednou**<br /><br />Další stahování je možné, pokud jsou pro tento typ obsahu dostupné aktualizace.|
|Denní operace klienta|6 MB|**Denně**<br /><br />Klient Intune na základě pravidelné komunikace se službou Intune kontroluje aktualizace a zásady a informuje službu o stavu klienta.|
|Aktualizace definicí malwaru Endpoint Protection|Je to různé.<br /><br />Obvykle 40 KB až 2 MB|**Denně**<br /><br />Až třikrát denně|
|Aktualizace modulu Endpoint Protection|5 MB|**Měsíčně**|
|Aktualizace softwaru|Je to různé.<br /><br />Velikost závisí na nasazených aktualizacích.|**Měsíčně**<br /><br />Aktualizace softwaru se obvykle vydávají k druhému úterý v měsíci.<br /><br />Nově zaregistrovaný nebo nasazený počítač může používat větší šířku pásma sítě při stahování celé sady dříve vydaných aktualizací.|
|Aktualizace Service Pack|Je to různé.<br /><br />Velikost se liší u každé nasazené aktualizace Service Pack.|**Je to různé.**<br /><br />Závisí na tom, kdy aktualizace Service Pack nasadíte.|
|Distribuce softwaru|Je to různé.<br /><br />Velikost závisí na nasazeném softwaru.|**Je to různé.**<br /><br />Závisí na tom, kdy software nasadíte.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Způsob snížení využití šířky pásma sítě
Ke snížení využití šířky pásma sítě pro klienty Intune můžete použít jeden nebo více těchto způsobů.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Používání proxy serveru pro ukládání požadavků obsahu do mezipaměti
Použitím proxy serveru, který může ukládat do mezipaměti obsah, můžete snížit počet duplicitních souborů ke stažení a snížit využití šířky pásma sítě klienty, kteří požadují obsah z Internetu.

Proxy server s možností ukládání do mezipaměti přijme požadavky na obsah z klientských počítačů ve vaší síti, načte tento obsah z Internetu a potom uloží odpovědi HTTP a binární soubory ke stažení do mezipaměti. Tento server využívá informace uložené v mezipaměti k odpovědi na následné žádosti z klientských počítačů Intune.

Tady jsou obvyklá nastavení proxy serveru, který do mezipaměti ukládá obsah pro klienty Intune.

|Nastavení|Doporučená hodnota|Podrobnosti|
|-----------|---------------------|-----------|
|Velikost mezipaměti|5 GB až 30 GB|Hodnota se liší podle počtu klientských počítačích v síti a používaných konfigurací. Aby se soubory neodstranily příliš brzy, upravte velikost mezipaměti pro vaše prostředí.|
|Velikost jednotlivých souborů mezipaměti|950 MB|Toto nastavení nemusí být dostupné na všech proxy serverech s ukládáním do mezipaměti.|
|Typy objektů do mezipaměti|HTTP<br /><br />HTTPS<br /><br />BITS|Balíčky Intune jsou soubory CAB stažené Službou inteligentního přenosu na pozadí (BITS) přes HTTP.|
Informace o používání proxy serveru k ukládání obsahu do mezipaměti najdete v dokumentaci k vašemu řešení proxy serveru.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Používání Služby inteligentního přenosu na pozadí na počítačích
Intune podporuje používání Služby inteligentního přenosu na pozadí (BITS) na počítačích s Windows ke snížení šířky pásma sítě po dobu, kterou nakonfigurujete. Na stránce **Šířka pásma sítě** zásady agenta Intune můžete pro službu BITS nakonfigurovat zásady.

Další informace o službě BITS a počítačích s Windows najdete v části [Služba inteligentního přenosu na pozadí](http://technet.microsoft.com/library/bb968799.aspx) v knihovně TechNet.

### <a name="use-branchcache-on-computers"></a>Používání BranchCache na počítačích
Klienti Intune můžou díky BranchCache omezit přenos v síti WAN. Tyto operační systémy, které jsou podporované jako klienti, taky podporují BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Abyste mohli BranchCache používat, musíte na klientském počítači povolit BranchCache a pak ho nakonfigurovat pro **režim distribuované mezipaměti**.

Ve výchozím nastavení jsou BranchCache a režim distribuované mezipaměti při instalaci klienta Intune na počítači povolené. Pokud už ale klient má zásady skupiny zakazující BranchCache, Intune nemůže tyto zásady přepsat a služba BranchCache zůstane na tomto počítači zakázaná.

Pokud používáte BranchCache, měli byste komunikovat s ostatními správci ve vaší organizaci, kteří spravují zásady skupiny a zásady brány firewall pro Intune, a zajistit, aby nenasazovali zásady zakazující BranchCache nebo výjimky brány firewall. Další informace o BranchCache najdete v tématu [BranchCache – přehled](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Požadavky na síťovou komunikaci

Musíte povolit síťovou komunikaci mezi zařízeními, která spravujete a používáte ke správě předplatného Intune, a weby požadovanými pro cloudové služby.

Intune nepoužívá místní infrastrukturu, jako jsou servery se softwarem Intune, ale existují možnosti používání místní infrastruktury včetně nástrojů pro synchronizaci Exchange a Active Directory.

Abyste mohli spravovat počítače, které jsou za bránami firewall nebo proxy servery, je potřeba nastavit brány firewall a proxy servery a povolit komunikaci pro Intune. Pokud chcete spravovat počítače, které jsou za proxy serverem, mějte na paměti následující okolnosti:

-   Proxy server musí podporovat **HTTP (80)** i **HTTPS (443)**, protože klienti Intune používají oba protokoly.
-   Intune podporuje neověřené proxy servery.

Nastavení proxy serveru můžete upravit na jednotlivých klientských počítačích, nebo můžete nastavení změnit pomocí zásad skupiny u všech klientských počítačů, které jsou umístěné za zadaným proxy serverem.

Spravovaná zařízení musí být nakonfigurovaná tak, aby **všichni uživatelé** měli přístup ke službám přes brány firewall.

Následující tabulky obsahují seznam portů a služeb, ke kterým přistupuje klient Intune:

|**Domény**|**IP adresa**|
|---------------------|-----------|
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
