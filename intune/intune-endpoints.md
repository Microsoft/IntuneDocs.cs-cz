---
title: Koncové body sítě pro Microsoft Intune
titleSuffix: ''
description: Projděte si koncové body pro Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 026536b1f0c059808220273ccffefacc28b80ae0
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031609"
---
# <a name="network-endpoints-for-microsoft-intune"></a>Koncové body sítě pro Microsoft Intune

Tato stránka obsahuje seznam IP adres a nastavení portu potřebné pro nastavení proxy serveru v nasazení Intune.

Jako čistě cloudovou službu Intune nevyžaduje místní infrastrukturu, jako jsou servery nebo brány.

Ke správě zařízení za bránami firewall nebo proxy servery, je nutné povolit komunikaci pro Intune.

- Proxy server musí podporovat **HTTP (80)** a **HTTPS (443)** vzhledem k tomu, že klienti Intune používají oba protokoly. Windows Information Protection používá port 444.
- Pro některé úlohy (jako je stahování aktualizací softwaru pro agenta pro klasické počítače), vyžaduje Intune přístup k neověřenému proxy serveru na adresu manage.microsoft.com

Můžete upravit nastavení proxy serveru na jednotlivých klientských počítačích. Nastavení zásad skupiny můžete také změnit nastavení pro všechny klientské počítače umístěné za zadaným proxy serverem.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Spravovaná zařízení musí být nakonfigurovaná tak, aby **všichni uživatelé** měli přístup ke službám přes brány firewall.

Následující tabulky obsahují seznam portů a služeb, ke kterým přistupuje klient Intune:

|**Domény**|**IP adresa**|
|---------------------|-----------|
|login.microsoftonline.com | Další informace: [Office 365 –adresy URL a rozsahy IP adres](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|


### <a name="network-requirements-for-powershell-scripts-and-win32-apps"></a>Požadavky na síť pro skripty prostředí Powershell a aplikace Win32
Pokud Intune používáte k nasazení Powershellových skriptů nebo aplikací Win32, budete také muset udělit přístup ke koncovým bodům, ve kterých se aktuálně nachází vašeho tenanta.

|ASU | Název úložiště | CDN |
| --- | --- |--- |
| AMSUA0601 | prodmsua06data | https:\//prodmsua06data.azureedge.net |
| AMSUA0602 | prodamsua0602data | https:\//prodamsua0602data.azureedge.net |
| AMSUA0101 | prodmsua01data | https:\//prodmsua01data.azureedge.net |
| AMSUA0201 | prodmsua02data | https:\//prodmsua02data.azureedge.net |
| AMSUA0202 | Prodmsua0202rcdata | https:\//prodamsua0202data.azureedge.net/ |
| AMSUA0401 | prodmsua04data | https:\//prodmsua04data.azureedge.net |
| AMSUA0402 | Prodmsua0402rcdata | https:\//prodamsua0402data.azureedge.net/ |
| AMSUA0501 | prodmsua05data | https:\//prodmsua05data.azureedge.net |
| AMSUA0502 | prodmsua0502data | https:\//prodmsua0502data.azureedge.net |
| AMSUB0101 | prodmsub01data | https:\//prodmsub01data.azureedge.net |
| AMSUB0102 | prodamsub0102data | https:\//prodamsub0102data.azureedge.net |
| AMSUB0201 | prodmsub02data | https:\//prodmsub02data.azureedge.net |
| AMSUB0202 | Prodmsub0202rcdata | https:\//prodamsub0202data.azureedge.net |
| AMSUB0301 | Prodmsub03data2 | https:\//prodmsub03data2.azureedge.net |
| AMSUB0302 | Prodmsub0302rcdata | https:\//prodamsub0302data.azureedge.net |
| AMSUB0501 | prodmsub05data | https:\//prodmsub05data.azureedge.net |
| AMSUC0101 | prodmsuc01data | https:\//prodmsuc01data.azureedge.net |
| AMSUC0201 | prodmsuc02data | https:\//prodmsuc02data.azureedge.net |
| AMSUC0301 | prodmsuc03data | https:\//prodmsuc03data.azureedge.net |
| AMSUC0501 | prodmsuc05data | https:\//prodmsuc05data.azureedge.net |
| AMSUA0701 | pemsua07rcdata | https:\//pemsua07data.azureedge.net |

### <a name="windows-push-notification-services-wns"></a>Služby nabízených oznámení Windows (WNS)
Pro zařízení s Windows spravovaných pomocí Intune spravovat pomocí správy mobilních zařízení (MDM) akce zařízení a dalších okamžité aktivit vyžaduje použití sady Windows Push Notification Services (WNS). Další informace najdete v části [oznámení Windows umožňuje provoz přes brány firewall organizace](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).    

### <a name="delivery-optimization-port-requirements"></a>Požadavky na porty optimalizace doručení

#### <a name="port-requirements"></a>Požadavky na porty
Pro provoz peer-to-peer optimalizace doručení pro protokol TCP/IP nebo 3544 pro přecházení NAT (volitelně Teredo) používá 7680. Pro komunikaci klienta služby používá protokol HTTP nebo HTTPS přes port 80 a 443.

#### <a name="proxy-requirements"></a>Požadavky na proxy serveru
Pokud chcete používat optimalizace doručení, musíte také povolit požadavky na zjištění rozsahu bajtů. Další informace najdete v tématu [požadavky na proxy serveru pro Windows Update](https://docs.microsoft.com/windows/deployment/update/windows-update-troubleshooting).

#### <a name="firewall-requirements"></a>Požadavky na bránu firewall
Povolte u následujících názvů hostitele přes bránu firewall pro podporu optimalizace doručení.
Pro komunikaci mezi klienty a cloudové službě optimalizace doručení:
- *.do.dsp.mp.microsoft.com

Pro metadata z optimalizace doručení:
- *.dl.delivery.mp.microsoft.com
- *.emdl.ws.microsoft.com

### <a name="apple-device-network-information"></a>Informace o síti pro zařízení Apple


|Používá pro|Hostname (IP address/subnet)|Protocol|Port|
|-----|--------|------|-------|
|Načítání a zobrazování obsahu ze serverů společnosti Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Komunikaci se servery pro služby APN|#-courier.push.apple.com<br>"#" je náhodné číslo od 0 do 50.|    TCP     |  5223 a 443  |
|Různé funkce, včetně přístupu k webu, iTunes storu, obchodu s aplikacemi s macOS, Icloudu, zasílání zpráv, atd. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 nebo 443   |

Další informace najdete v tématu společnosti Apple [porty TCP a UDP používané softwarové produkty společnosti Apple](https://support.apple.com/en-us/HT202944), [o macOS, iOS a iTunes připojení k serveru hostitele a iTunes pozadí procesy](https://support.apple.com/en-us/HT201999), a [Pokud vaše klienty se systémy iOS a macOS nedaří získat nabízených oznámení Apple](https://support.apple.com/en-us/HT203609).