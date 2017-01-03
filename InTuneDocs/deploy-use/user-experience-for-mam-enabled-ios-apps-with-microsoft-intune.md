---
title: "Aplikace pro iOS se zásadami MAM | Microsoft Intune"
description: "Toto téma popisuje, co máte očekávat, když je vaše aplikace pro iOS spravovaná pomocí zásad správy mobilních aplikací."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 3aa6728036ff66ea489176063af2d136bef4c7cc


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>Co očekávat, když ke správě své aplikace pro iOS používáte zásady MAM
 Toto téma popisuje činnost uživatele aplikací se zásadami správy mobilního přístupu (MAM). Zásady MAM se použijí jenom v případě, že se aplikace používají k práci: třeba když uživatel k aplikacím přistupuje pomocí pracovního účtu nebo přistupuje k souborům, které jsou uložené ve firemním umístění OneDrive.

##  <a name="access-apps"></a>Přístup k aplikacím

Pokud zařízení **není zaregistrované v Intune**, zobrazí se uživateli při prvním použití aplikace výzva k jejímu restartování.  Restartování se vyžaduje, aby se pro aplikaci mohly použít zásady MAM. Tento požadavek na restartování je vidět na snímku obrazovky z aplikace Skype:


![Snímek obrazovky zařízení s iOSem, na kterém je výzva k zadání kódu PIN](../media/appmanagement/iOS_AppPINPrompt.png)

U zařízení, která jsou **zaregistrovaná pro správu v Intune**, se uživateli zobrazí zpráva, že jeho aplikace je teď spravovaná:

![Snímek obrazovky zařízení s iOSem se zprávou, že je teď aplikace spravovaná vaší společností, a výzvou k zadání kódu PIN](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>Použití aplikací s podporou více identit

Zásady MAM se použijí jen v pracovním kontextu. Aplikace se proto můžou chovat odlišně podle toho, jestli je kontext pracovní nebo osobní.

 Uživateli se třeba při přístupu k pracovním datům zobrazí výzva k zadání kódu PIN. U **aplikace Outlook** se uživateli zobrazí výzva k zadání kódu PIN při spouštění aplikace. U **aplikace OneDrive** se uživateli zobrazí výzva k zadání kódu PIN při zadání pracovního účtu.  U aplikací Microsoft **Word**, **PowerPoint** a **Excel** se uživateli zobrazí výzva k zadání kódu PIN, když přistupuje k dokumentům uloženým v umístění OneDrive pro firmy.

##  <a name="manage-user-accounts-on-the-device"></a>Správa uživatelských účtů v zařízení

Intune podporuje nasazení zásad MAM jenom na jeden uživatelský účet v každém zařízení.

* V závislosti na aplikaci, kterou používáte, může být druhý uživatel v zařízení blokovaný. Ve všech případech ale zásady ovlivňují jenom prvního uživatele, který získá zásady MAM.
  * Aplikace **Microsoft Word**, **Excel** a **PowerPoint** druhý uživatelský účet neblokují, ale na tento druhý uživatelský účet nemají zásady MAM vliv.  

  * U aplikací **OneDrive** a **Outlook** můžete používat jenom jeden pracovní účet. U těchto aplikací nejde přidat více pracovních účtů. Na zařízení ale můžete odebrat uživatele a přidat jiného uživatele.

* Pokud zařízení obsahuje před nasazením zásad MAM více uživatelských účtů, bude zásadami MAM služby Intune spravován ten účet, do kterého se zásady MAM nasadí dříve.


Přečtěte si následující ukázkový scénář, abyste lépe pochopili, jak se pracuje s více uživatelskými účty.

Uživatel A pracuje ve dvou společnostech – ve **společnosti X** a ve **společnosti Y**. Uživatel A má pro každou společnost pracovní účet a obě společnosti používají Intune k nasazení zásad MAM. **Společnost X** nasadí zásady MAM **dřív než** **společnost Y**. Účet přidružený ke **společnosti X** získá zásady MAM, ale účet přidružený ke společnosti Y ne. Pokud chcete, aby byl účet přidružený ke společnosti Y spravován pomocí zásad MAM, musíte odebrat uživatelský účet přidružený ke společnosti X.

### <a name="add-a-second-account"></a>Přidání druhého účtu

Pokud používáte zařízení s iOSem, může se při pokusu o přidání druhého pracovního účtu na zařízení zobrazit zpráva o blokování. Účty se zobrazí a můžete zvolit účet, který chcete odebrat.

![Snímek obrazovky s dialogem obsahujícím zprávu o blokování a možnosti Ano a Ne](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>Další kroky
[Co očekávat, když ke správě své aplikace pro Android používáte zásady MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>Související témata
[Vytvoření a nasazení zásad správy mobilních aplikací pomocí Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

