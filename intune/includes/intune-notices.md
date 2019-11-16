---
title: ファイルを含める
description: ファイルを含める
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 3d49d31ed08683508d3d231521e578688dd21bac
ms.sourcegitcommit: 737ad6c675deedfc6009f792023ff95981b06582
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2019
ms.locfileid: "74125440"
---
以下の通知では、今後の Intune の変更と機能に備えるために役立つ重要な情報が提供されます。

### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Naplánování změny v Intune: Windows 10, verze 1703 Portál společnosti přesun mimo podporu<!--5026679-->
Windows 10 verze 1703 (označované také jako Windows 10, RS2) se od 8. října 2019 pro edice Enterprise a EDU přesunula mimo službu. Intune ukončí podporu pro odpovídající aplikaci Portál společnosti pro RS2/RS1 od 26. prosince 2019.

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Dál, v konkrétní verzi Portál společnosti aplikace se nezobrazí nové funkce, i když budeme dál podporovat tuto verzi aplikace Portál společnosti až do 26. prosince 2019, včetně poskytování všech aktualizací zabezpečení pro Portál společnosti aplikaci jako vyžadována. Vzhledem k tomu, že Windows 10 verze 1703 neobdrží žádné aktualizace zabezpečení po přesunutí ze údržby, důrazně doporučujeme, abyste si aktualizovali zařízení s Windows na novější verzi Windows a zajistili, že jste na nejnovější aplikaci Portál společnosti, abyste mohli dál získat nové funkce a další funkce.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
Postup závisí na tom, jak je vaše prostředí nakonfigurované. Obecně byste měli určit zařízení, která mají starší verzi operačního systému, nebo Portál společnosti na svém zařízení a aktualizovat. Pokud chcete nastavit aktualizační kanály Windows 10, přihlaste se k Intune – > aktualizace softwaru – aktualizační kanály Windows 10. Nejnovější verze Portál společnosti je 10.3.5601.0 verze. Požádejte uživatele, aby si ho získali od Microsoft Store, aby se v budoucích verzích stále dosáhlo. Intune taky můžete použít k instalaci nejnovějšího prostředí do zařízení s Windows prostřednictvím [Microsoft Store pro firmy](https://docs.microsoft.com/intune/windows-store-for-business).

#### <a name="additional-information"></a>追加情報
[Microsoft Intune を使用して Windows 10 ポータル サイト アプリを手動で追加する](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Provést akci: použití Microsoft Edge pro chráněné prostředí Intune Browser<!--5728447-->
Vzhledem k tomu, že jsme provedli sdílení v průběhu minulého roku, Microsoft Edge Mobile podporuje stejnou sadu funkcí správy jako Managed Browser a přitom nabízí mnohem lepší prostředí pro koncové uživatele. Pro zajištění robustních funkcí poskytovaných Microsoft Edgeem Intune Managed Browser vyřazení z provozu. Od 27. ledna 2020 už Intune nebude podporovat Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響 
Od 1. února 2020 už nebude Intune Managed Browser k dispozici v Obchod Google Play nebo v obchodě s aplikacemi pro iOS. V tuto chvíli budete moci do Intune Managed Browser cílit na nové zásady ochrany aplikací, i když noví uživatelé nebudou moct stáhnout Intune Managed Browser aplikaci. V systému iOS se navíc nové webové klipy, které se odešlou do zařízení zaregistrovaného na MDM, otevřou v Microsoft Edge místo Intune Managed Browser.  

Od března 31 2020 se Intune Managed Browser odebere z konzoly Azure. To znamená, že už nebudete moct vytvářet nové zásady pro Intune Managed Browser. Pokud jste zavedli existující zásady Intune Managed Browser, nebudou ovlivněny. Intune Managed Browser se v konzole zobrazí jako obchodní aplikace bez ikony a stávající zásady se budou zobrazovat jako cílené pro aplikaci. V tuto chvíli také odebereme možnost přesměrovat webový obsah do Intune Managed Browser v části Ochrana dat v zásadách ochrany aplikací.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備 
K zajištění hladkého přechodu z Intune Managed Browser na Microsoft Edge doporučujeme proaktivně provést následující kroky: 

1. Zaměřte se na Microsoft Edge pro iOS a Android pomocí zásad ochrany aplikací (také označovaných jako MAM) a nastavení konfigurace aplikace. Můžete znovu použít zásady Intune Managed Browser pro Microsoft Edge tím, že jednoduše cílíte na tyto existující zásady na Microsoft Edge.  
2. Zajistěte, aby všechny aplikace chráněné MAM ve vašem prostředí měly zásadu ochrany aplikací s nastavením omezit přenos webového obsahu s ostatními aplikacemi nastavenou na prohlížeče spravované zásadami. 
3. Zaměřte se na všechna MAM chráněná nastavením konfigurace spravované aplikace "com. Microsoft. Intune. useEdge" nastavenou na hodnotu true. Počínaje dalším měsícem s vydáním 1911 budete moct provádět kroky 2 a 3 jednoduše tak, že v části Ochrana dat v zásadách ochrany aplikací nastavíte možnost omezit přenos webových obsahu na jiné aplikace. . 

Připravujeme podporu pro webové klipy v iOS a Androidu. Až se tato podpora uvolní, budete muset změnit cílení na existující webové klipy, abyste se ujistili, že jsou otevřené v Microsoft Edge místo Managed Browser. 

#### <a name="additional-information"></a>追加情報
Další informace najdete v našich dokumentech o [používání Microsoft Edge se zásadami ochrany aplikací](../apps/manage-microsoft-edge.md) , nebo si prohlédněte náš [příspěvek blogu o podpoře](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Plánování změn: aktualizované prostředí při registraci vyhrazených zařízení s Androidem Enterprise v Intune<!--5198878-->
Od verze listopadu nebo 1911 do Intune přidáváme podporu nasazení certifikátu zařízení SCEP pro zařízení s Androidem Enterprise vyhrazená pro povolení přístupu k profilům Wi-Fi pomocí certifikátů. Tato změna zahrnuje také některé menší změny toku při registraci vyhrazených zařízení s Androidem Enterprise.

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Pokud ve svém prostředí spravujete vyhrazená zařízení s Androidem Enterprise, začnete v listopadu zobrazovat některé změny.

- Pro nové registrace zařízení se systémem Android Enterprise: koncoví uživatelé uvidí během registrace jinou sadu kroků na zařízeních. Registrace pořád spustí způsob, jakým v současné době funguje (se QR, NFC, nulou nebo identifikátorem zařízení), ale po vydání služby bude povinný krok instalace aplikace.
- Stávající zařízení s Androidem zaregistrovaná jako vyhrazená zařízení: Intune začne automaticky instalovat aplikaci Microsoft Intune do zařízení počínaje začátkem listopadu. Nemusíte provádět žádnou akci. Aplikace se automaticky stáhne a nainstaluje na zařízení. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
Měli byste naplánovat, abyste si aktualizovali pokyny pro koncové uživatele a věděli, že vám tato změna poznala helpdesk. Kliknutím na Další informace zobrazíte další podrobnosti a snímky obrazovky. Až se tato změna začne zavádět, aktualizujeme naši stránku co je nového.

#### <a name="additional-information"></a>追加情報
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>Naplánování změny: nastavení ' protokolování na straně serveru pro příkazy Siri se odebere z konzoly Intune. <!-- 5468501-->

Chystáme se odebrat nastavení protokolování na straně serveru pro příkazy Siri z konzoly Intune s aktualizací z listopadu na službu Intune. この変更により、既にこの設定が削除されている Apple との連携がもたらされます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
11 月の更新、または 11 月中旬の 1911 のロールアウトが行われると、ユーザーは、Intune コンソールで、iOS 構成プロファイルの [デバイスの制限] メニュー (組み込みアプリ) からこの設定が削除されていることを確認できます。 ポリシーと対象デバイスの管理プロファイルにこの設定が表示される場合がありますが、デバイスには影響しません。 管理プロファイルに表示されたとしても、これは現在デバイス上で機能していないため、機能に対する大きな影響はないと予測されます。

次の 2 つのパスのどちらかを選択できます。
- ポリシーからこの設定を削除したい場合は、この設定が含まれているプロファイルに移動し、小規模の編集を行ってポリシーを保存することができます。 バックエンドでポリシーが再計算され、ポリシーから設定が削除されます。
- この操作を行わないことを選んだ場合、エンド ユーザーのデバイスの管理プロファイルにこの設定が表示されますが、この設定による影響はありません。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
上記のセクションに従って対応策を取るか、ポリシーをそのままにしておくことができます。 この変更がロールアウトされたとき、Microsoft の新機能に関するページとドキュメントが更新されます。

### <a name="end-of-support-for-legacy-pc-management"></a>従来の PC 管理のサポート終了

従来の PC 管理は 2020 年 10 月 15 日にサポートが終了します。 デバイスを Windows 10 にアップグレードし、Intune による管理が継続されるように MDM デバイスとして再登録してください。

[詳細情報](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Android デバイス管理者のサポートの縮小 
Android デバイス管理者 ("従来の" Android 管理とも呼ばれ、Android 2.2 でリリースされました) は、Android デバイスを管理する方法の 1 つです。 しかし、[Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5.0 でリリース) では、強化された管理機能を使用できるようになりました。 Google では、より豊富で安全な最新のデバイス管理に移行するための努力の一環として、新しい Android リリースでのデバイス管理者のサポートを縮小させています。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Google によるこのような変更により、Intune ユーザーは次のような影響を受けます。  
- Intune では、デバイス管理者が管理する Android デバイスで、Android 10 以降 (Android Q とも呼ばれる) を稼働しているもののサポートを、2020 年夏までのみ提供できます。 これは、Android の次のメジャー バージョンのリリースが予定されている日付です。   
- 2020 年夏以降、デバイス管理者が管理するデバイスで、Android 10 以降を稼働しているものは、完全には管理できなくなります。       
- デバイス管理者が管理する Android デバイスで、Android 10 より前の Android バージョンのままであるものは影響を受けません。デバイス管理者で引き続き完全に管理できます。    
- Google では、Android 10 以降を稼働しているすべてのデバイスに対して、ポータル サイトのようなデバイス管理者の管理エージェントを使ってデバイス識別子の情報にアクセスする機能を制限しています。 これにより、Android 10 以降にデバイスを更新した後、次の Intune 機能が影響を受けます。  
    - VPN のネットワーク アクセス制御が機能しなくなる。   
    - IMEI またはシリアル番号を使用した企業所有のデバイスの識別で、デバイスが企業所有として自動的にマークされなくなる。  
    - Intune で IT 管理者に IMEI とシリアル番号が表示されなくなる。 
        > [!NOTE]
        > これが影響を与えるのは、デバイス管理者が管理するデバイスで Android 10 以降のもののみです。Android Enterprise として管理されているデバイスには影響しません。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
2020 年夏に実施される機能の縮小を回避するために、次のことをお勧めします。
- 新しいデバイスをデバイス管理者の管理にオンボードしない。
- デバイスが Android 10 への更新プログラムを受け取ることが予想される場合は、それをデバイス管理者の管理から外し、Android Enterprise 管理、アプリ保護ポリシーのいずれかまたは両方に移行する。

#### <a name="additional-information"></a>追加情報
- [デバイス管理者から Android Enterprise への移行に関する Google のガイダンス](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [デバイス管理者 API の廃止計画に関する Google のドキュメント](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android 用ポータル サイト アプリを最新バージョンに更新する <!--4536963-->
Intune では、Android 用ポータル サイト アプリに対する更新プログラムが定期的にリリースされます。 2018 年 11 月に、ポータル サイトの更新プログラムがリリースされました。これには、Google による既存の通知プラットフォームから Google の Firebase Cloud Messaging (FCM) への変更に備えるための、バックエンド スイッチが含まれていました。 Google が既存の通知プラットフォームを終了して FCM に移行したとき、エンド ユーザーは、Google Play ストアとの交信を継続するために、各自のポータル サイト アプリを少なくとも 2018 年 11 月のリリースに更新済みである必要があります。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
利用統計情報では、5.0.4269.0 よりも前のバージョンのポータル サイトを備えたデバイスがあることが示されています。 このバージョン以上のポータル サイト アプリをインストールしないと、ワイプ、パスワードのリセット、入手可能な必須アプリのインストール、証明書の登録のような、IT プロフェッショナルが開始したデバイス アクションが意図したとおりに機能しない場合があります。 ご自身のデバイスが Intune の MDM に登録されている場合は、[クライアント アプリ] – [検出されたアプリ] に移動することで、ポータル サイトのバージョンとユーザーを確認できます。 以前のバージョンのポータル サイト アプリを選択すると、どのエンド ユーザーがポータル サイト アプリを更新していないデバイスを持っているのかを確認できます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
更新していない Android デバイスを使っているエンド ユーザーに、Google Play を使ってポータル サイト アプリを更新するよう依頼します。 ユーザーがポータル サイト アプリの自動更新を維持していない場合は、ヘルプ デスクに通知します。 Google の FCM プラットフォームと変更について詳しくは、"*追加情報*" にあるリンクをご覧ください。

#### <a name="additional-information"></a>追加情報
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Intune に追加された新しい全画面のエクスペリエンス <!--4593669-->
Azure portal では、Intune に対する更新された UI 作成および編集のエクスペリエンスがロールアウトされています。 この新しいエクスペリエンスでは、1 つのブレード内にまとめられたウィザード形式のフォーマットを使用することで、既存のワークフローが簡素化されます。 この更新によって、"ブレードが無秩序に増える" ことや、ブレードを詳細にドリルダウンしていくことが求められる作成および編集のフローが回避されます。 また、作成のワークフローは、割り当て (アプリ割り当て以外) を含むように更新されます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
全画面のエクスペリエンスは、次の数か月間にわたって、portal.azure.com および devicemanagement.microsoft.com の両方で Intune にロールアウトされます。 この UI の更新は、既存のポリシーとプロファイルの機能には影響を及ぼしませんが、少し変更されたワークフローが表示されます。 たとえば、新しいポリシーを作成するときに、いくつかの割り当てをポリシーの作成後に行うのではなく、このフローの一部として設定できます。 コンソールでの新しいエクスペリエンスの外観を示したスクリーンショットは、"*追加情報*" にあるブログ投稿で確認してください。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
何らかのアクションを行う必要はありませんが、必要に応じて IT プロフェッショナル向けのガイダンスの更新を検討できます。 Microsoft では、Azure portal 上で Intune 内の各種のブレードに対してこのエクスペリエンスが公開され次第、ドキュメントを更新する予定です。

#### <a name="additional-information"></a>追加情報 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Plánování změn: sada Intune App SDK a zásady ochrany aplikací pro Android, které se přesunou na podporu Android 5,0 a vyšší v nadcházející verzi <!--4911065 -->
Intune では、今後のリリースで、Android 5.x (Lollipop) 以降のサポートが開始されます。 ラップされたすべてのアプリを最新の Intune App SDK で更新し、デバイスを更新してください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Android 用の SDK またはアプリを使用していない、または使用する予定がない場合は、この変更による影響はありません。 Intune App SDK を使用している場合は、必ず最新バージョンに更新し、またデバイスも Android 5.x 以降に更新してください。 お客様が更新を行わなかった場合、アプリで更新プログラムを受信できなくなり、時間の経過と共にそのエクスペリエンスの質が低下していきます。

Intune に登録されていて、Android バージョン 4.x を稼働している一般的なデバイスの一覧を以下に示します。 これらのデバイスのいずれかを使用している場合は、適切な手順を実行して、必ずそのデバイスで Android バージョン 5.0 以降をサポートするようにするか、それを Android バージョン 5.0 以降をサポートするデバイスに置き換えるようにしてください。 この一覧は、評価が必要なすべてのデバイスを網羅しているわけではありません。

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
最新の Intune App SDK でアプリをラップしてください。 また、[最低限の OS バージョンを必要とします (警告のみ)] という条件付き起動を設定して、個人用デバイスを使用しているエンド ユーザーにアップグレードするよう通知することもできます。

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Plán změny v Intune: blíží se konec podpory pro Windows 7.<!-- 3042987 -->
2018 年 9 月に投稿した MC148476 および 2019 年 3 月の MC176794 で再びお伝えしたとおり、Windows 7 の延長サポートは 2020 年 1 月 14 日に終了いたします。 その時点で、Windows 7 を稼働しているデバイスに対する Intune のサポートは終了します。これにより、より新しいテクノロジのサポートと、優れた新しいエンド ユーザー エクスペリエンスの提供に注力することが可能になります。 当該日付以降は、お使いの Windows 7 PC を保護するための技術的なサポートと自動更新が Intune で利用できなくなります。 もう利用できないサービスやサポートが必要になるシナリオを回避するために、2020 年 1 月より前に Windows 10 に移行することを強くお勧めします。 Windows のサポート ライフサイクルについて詳しくは、[こちら](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)をご覧ください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
このメッセージは、現在レガシ Intune PC ソフトウェア エージェントを使って Windows 7 PC を管理しているお客様に送信されます。 Windows 7 の延長サポート終了まで 1 年未満となったため、お客様の組織が、できるだけ早く Windows 10 へのアップグレードを開始することを強くお勧めします。  

PC 管理機能は Windows 10 オペレーティング システムに直接組み込まれているため、Windows 7 用の Intune ソフトウェア クライアントなどのクライアント エージェントをインストールする必要はもうありません。 Windows 8.1 以降、Microsoft では、Windows PC のプロビジョニング、構成、更新、および管理を行うためにモバイル デバイス管理 (MDM) アーキテクチャが使われています。 Intune の設定が完了したら、MDM チャネルを通じて [Intune に Windows 10 PC を登録](..\windows-enroll.md)することで、Windows の登録を簡易化できます。 この "エージェントレス" MDM 管理ソリューションを使って Windows 10 PC を管理することをお勧めします。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
お客様の組織で次のアクション プランをすぐに検討することをお勧めします。

- 2020 年 1 月 14 日より前に、一連の Windows 7 の Windows 10 へのアップグレードを計画し、実行する。
- [Windows 10 の展開サポート](https://docs.microsoft.com/windows/deployment/)に関するページを参照し、使用している Windows 7 PC 全体を Windows 10 にアップグレードする方法について詳しく学習する。
- FastTrack を通じて [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) サービスを確認する (Microsoft のアプリケーション互換性に関する約束が支援されます)。
- 既存のレガシ Intune ソフトウェア クライアントのマネージド デバイスを Microsoft 推奨のソリューションに移行し、MDM 管理を使用して Windows 10 を管理する。 すべての新しい Windows 10 PC を、Azure portal で Intune の MDM 管理を使って登録する。

さらなる情報については、[こちらのブログ投稿](https://aka.ms/Windows7_Intune)を参照してください。
