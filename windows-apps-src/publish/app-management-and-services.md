---
author: jnHs
Description: Manage and view details related to each of your apps in the Windows Dev Center dashboard, and configure services such as A/B testing and maps.
title: アプリの管理とサービス
ms.assetid: 99DA2BC1-9B5D-4746-8BC0-EC723D516EEF
ms.author: wdg-dev-content
ms.date: 07/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d0e4be450aa972ad8561f27a8d4749050458520a
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "2799931"
---
# <a name="app-management-and-services"></a>アプリの管理とサービス

Windows デベロッパー センター ダッシュボードで各アプリに関連する詳細を管理および表示し、通知、A/B テスト、マップなどのサービスを構成できます。

ダッシュボードでアプリを操作するとき、左側のナビゲーション メニューに **[サービス]** と **[アプリ管理]** のセクションが表示されます。 これらのセクションを展開すると、次の機能にアクセスできます。

## <a name="services"></a>サービス

**[サービス]** セクションでは、アプリのいくつかの異なるサービスを管理できます。

## <a name="xbox-live"></a>Xbox Live

ゲームを発行する場合は、このページで、 [Xbox Live の作成者のプログラム](http://xbox.com/developers/creators-program)を有効にすることができます。 これにより、構成すると、テスト、Xbox Live 機能を起動し、最終的に、Xbox Live の作成者プログラム ゲームを公開することができます。

詳しくは、 [Xbox Live の作成者プログラムの使用を開始して](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md)、 [Xbox Live の作成者のプログラムの新しいタイトルを作成しテスト環境に発行する](../xbox-live/get-started-with-creators/create-and-test-a-new-creators-title.md)を参照してください。

## <a name="experimentation"></a>Experimentation

**[Experimentation]** ページを使うと、ユニバーサル Windows プラットフォーム (UWP) アプリの試験的機能を作成し、A/B テストを実行できます。 アプリの機能の変更をすべてのユーザー向けに有効にする前に、一部のユーザーに対して変更 (またはバリエーション) の有効性を A/B テストで測定します。

詳しくは、「[A/B テストを使用してアプリの試験的機能を実行する](../monetize/run-app-experiments-with-a-b-testing.md)」をご覧ください。

## <a name="maps"></a>マップ

Windows Phone 8.1 以前を対象としたアプリでマップ サービスを使うには、アプリのコードに含めるマップ サービス アプリケーション ID とトークンが必要です。 **[マップ]** ページの **[サービス]** セクションでこのトークンを取得できます。

> [!NOTE]
> Windows 10 または Windows 8.x を対象としたアプリでマップ サービスを使うには、[Bing 地図デベロッパー センター](http://go.microsoft.com/fwlink/p/?LinkId=614880)にアクセスしてください。 詳しくは、「[マップ認証キーの要求](https://docs.microsoft.com/windows/uwp/maps-and-location/authentication-key)」をご覧ください。

詳しくは、「[マップ サービスの使用](use-map-services.md)」をご覧ください。

## <a name="product-collections-and-purchases"></a>製品のコレクションと購入

Microsoft ストア コレクション API や Microsoft ストア購入 API を使用すると、アプリとアドオンの所有者情報にアクセスして、関連するを入力する必要があります。 Azure AD クライアント Id を次のとおりです。 これらの変更が有効になるまで最大で 16 時間かかることに注意してください。

詳しくは、「[サービスから製品の権利を管理する](../monetize/view-and-grant-products-from-a-service.md)」をご覧ください。

## <a name="administrator-consent"></a>管理者の承認

f、製品、Azure AD と統合管理者の承認が必要な[アプリケーションのアクセス許可または代理アクセス権](https://developer.microsoft.com/graph/docs/concepts/permissions_reference)を要求する Api を呼び出して Azure AD クライアント ID を入力します。 これにより、その組織許可を付与することに同意したテナント内のすべてのユーザーの代理として機能するように、その製品の用のアプリを入手するには管理者です。

詳しくは、[テナントが全体の承認を要求する](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-scopes#requesting-consent-for-an-entire-tenant)を参照してください。

## <a name="app-management"></a>アプリ管理

**[アプリ管理]** セクションでは、ID とパッケージの詳細を確認したり、アプリの名前を管理したりできます。

## <a name="app-identity"></a>アプリ ID

このページには、アプリの内容へのリンクの URL など、ストア内のアプリの一意の ID に関連する詳細情報が表示されます。

詳しくは、「[アプリ ID の詳細の表示](view-app-identity-details.md)」をご覧ください。

## <a name="manage-app-names"></a>アプリ名の管理

ここでは、アプリのために予約したすべての名前を確認できます。 追加の名前の予約や、使わなくなったの名前の削除は、ここで行うことができます。

詳しくは、「[アプリ名の管理](manage-app-names.md)」をご覧ください。

## <a name="current-packages"></a>現在のパッケージ

このページでは、公開されたすべてのパッケージに関連する詳しい情報を確認することができます。

> [!NOTE]
> ここには、アプリが公開されるまで、情報は表示されません。

各パッケージの名前、バージョン、およびアーキテクチャが表示されます。 **[詳細]** をクリックすると、サポートされる言語、アプリの機能、ファイル サイズなどの詳しい情報が表示されます。 パッケージごとに表示される情報は、対象となるオペレーティング システムとその他の要因によって異なることがあります。 

OEM アクセス許可を持つ開発者は、**[現在のパッケージ]** ページから [プレインストール パッケージを生成](generate-preinstall-packages-for-oems.md) することもできます。

## <a name="wnsmpns"></a>WNS/MPNS

[ **WNS/MPNS** ] セクションを作成し、アプリのユーザーに通知を送信するためのオプションを提供します。 

> [!TIP]
> UWP アプリでは、[**通知**] オプションを使用して、ダッシュ ボードをお勧めします。 この機能では、すべてのアプリの顧客に通知を送信できます。 または、[顧客セグメント](create-customer-segments.md)で定義した条件を満たしている、Windows 10 顧客の対象となるサブセットをします。 詳しくは、「[アプリのユーザーに通知を送信する](send-push-notifications-to-your-apps-customers.md)」をご覧ください。

アプリのパッケージの種類と、特定の要件に応じて、次のいずれかを使用することも。 

-   **Windows プッシュ通知サービス (WNS)** を使うと、独自のクラウド サービスからトースト更新、タイル更新、バッジ更新、直接更新を送ることができます。 詳しくは、「[Windows プッシュ通知サービス (WNS) の概要](../design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview.md)」をご覧ください。

-   **Microsoft Azure Mobile Apps** を使うと、プッシュ通知の送信や、アプリ ユーザーの認証や管理、クラウドでのアプリ データの保存をすることができます。 詳しくは、[モバイル アプリに関するドキュメント](http://go.microsoft.com/fwlink/p/?LinkId=221116)をご覧ください。

-   **Microsoft プッシュ通知サービス (MPNS)** は、Windows Phone の .xap パッケージと一緒に使うことができます。 ここで構成を行わなくても、認証されていない通知を限られた数送信することができますが、制限が減らないように認証済みの通知を使うことをお勧めします。 MPNS を使用している場合は、 **WNS/MPNS**ページに表示されているフィールドに証明書をアップロードする必要があります。 詳しくは、「[Windows Phone 8 のプッシュ通知を送信するように認証済み Web サービスを設定する](http://go.microsoft.com/fwlink/p/?LinkId=528736)」をご覧ください。
 

 