---
# required metadata

title: Vytvoření zásad a publikování aplikace | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vytvoření zásad a publikování aplikace
Intune nabízí nastavení, které pomáhá řídit nastavení zabezpečení na mobilních zařízeních, spravovat nastavení brány Windows Firewall a Endpoint Protection pro počítače a nasazovat aplikace. Další informace najdete v tématech [Správa nastavení a funkcí v zařízeních pomocí zásad Microsoft Intune](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) a [Pomoc se zabezpečením počítačů s Windows pomocí služby Endpoint Protection pro Microsoft Intune](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Pomocí Intune můžete provádět dva typy instalace aplikací. První je **požadovaná instalace**, která aplikaci automaticky nasadí do spravovaných počítačů. Druhá je **dostupná instalace**, která nasadí aplikaci nebo odkaz na aplikaci na portálu společnosti Intune, aby si mohli uživatelé vybrat, jestli ji chtějí mít nainstalovanou na počítači nebo na mobilním zařízení.

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

V následujícím postupu nastavíte zásady konfigurace mobilního zařízení a zásady brány firewall počítače s Windows a nakonfigurujete Skype jako instalaci dostupnou pro mobilní zařízení po jejich registraci.

> [!TIP]
> Po přidání a nasazení nových zásad zdědí všichni uživatelé nebo zařízení ve skupině, do které jste zásadu nasadili, tato nastavení jako svoje základní zásady. Podrobnosti těchto zásad můžete později kdykoli zkontrolovat nebo upravit v pracovním prostoru zásad.


## Vytvoření a nasazení zásady konfigurace mobilních zařízení

1.  Otevřete [konzolu pro správu Intune](https://manage.microsoft.com/)..

2.  V levém podokně vyberte ikonu **Zásady**.

    ![admin-console-policy-workspace](./media/policy.png)

3.  V seznamu **Úlohy** na stránce **Přehled zásad** vyberte **Přidat zásadu**..

4.  V seznamu zásad rozbalte platformu, pro kterou chcete vytvořit zásadu, pak vyberte **Všeobecná konfigurace** > **Vytvoření a nasazení zásad s doporučeným nastavením** > **Vytvořit zásadu**..

5.  Při zobrazení výzvy **Vyberte skupiny, do kterých chcete nasadit tuto zásadu** vyberte ze seznamu dostupný skupin **Uživatelé Intune** (skupina vytvořená během předchozího kroku) a vyberte **Přidat** > **OK**.

Vaše zásada se zobrazí v seznamu zásad konfigurace a byla nasazena do skupiny **Uživatelé Intune**. Nastavení zásady zobrazíte tak, že na zásadu dvakrát kliknete.

## Publikování aplikace Skype pro mobilní zařízení

1.  V [konzole pro správu Intune](https://manage.microsoft.com/) vyberte ikonu **Aplikace** a pak **Aplikace** > **Přidat aplikaci**. Po zobrazení výzvy zadejte své přihlašovací údaje do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![admin-console-apps-workspace](./media/apps.png)

    > [!NOTE]
    > Při prvním spuštění **Intune Software Publisheru** může instalace aplikace chvíli trvat.

2.  Přečtěte si upozornění zabezpečení a vyberte **Spustit**..

3.  Na stránce **Než začnete** vyberte **Další**..

4.  Na stránce **Instalace softwaru** v části **Vyberte, jakým způsobem má být tento software zpřístupněn pro zařízení** vyberte **Externí odkaz**..

5.  Zadejte externí odkaz pro software v části **Zadejte adresu URL** a vyberte **Další**. Ujistěte se, že adresa URL začíná **http://**. Pro aplikaci Skype použijte odkaz dole odpovídající platformě mobilního zařízení, kterou používáte:

    -   **iOS:**   [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 nebo Windows Phone 8.1:**  [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Na stránce **Popis softwaru** zadejte informace k softwaru, které mají uživatelé vidět na firemním portálu, a vyberte **Další**. Dostupná jsou tato nastavení (tento příklad se týká Skypu):

    -   **Vydavatel:** Zadejte název vydavatele (Microsoft).

    -   **Název:** Zadejte **Skype**

    -   **Popis:** Zadejte popis softwaru, třeba **Komunikační aplikace Skype**

    -   **Kategorie:** Vyberte kategorii, která nejlíp odpovídá tomuto softwaru, třeba **Spolupráce**

    -   **Zobrazit tuto aplikaci jako doporučenou aplikaci a zvýraznit ji na portálu společnosti:** Po výběru této možnosti bude při prohlížení na mobilních zařízeních aplikace zřetelně zobrazená na firemním portálu.

    -   **Ikona:** Vyberte, jestli chcete softwaru přiřadit ikonu. Maximální velikost volitelné ikony je 250 x 250 pixelů a doporučená velikost je 32 x 32 pixelů.

7.  Na stránce **Souhrn** zkontrolujte zadané informace o softwaru a vyberte **Odeslat**. Průvodce ukončíte výběrem **Zavřít**.

8.  V [konzole pro správu Intune](https://manage.microsoft.com/) vyberte **Aplikace** > **Aplikace** > **Skype** > **Spravovat nasazení**..

9. Na stránce **Vybrat skupiny** vyberte **Uživatelé Intune** pro nasazení softwaru do této skupiny uživatelů a potom vyberte **Přidat** > **Další**..

10. Na stránce **Akce nasazení** vyberte **Dostupná instalace** ze sloupce **Schválení** pro vaši skupinu.

11. Klikněte na **Dokončit**..

Aplikace Skype je teď dostupná k instalaci na mobilních zařízeních z portálu společnosti, ale nejdřív je potřeba nainstalovat na počítačích a mobilních zařízeních software [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].


### Další kroky
Gratulujeme! Právě jste dokončili krok 6 *úvodní příručky Intune*.

>[!div class="step-by-step"]

>[&larr; **Organizace uživatelů a zařízení**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**Přizpůsobení portálu společnosti** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=May16_HO1-->

