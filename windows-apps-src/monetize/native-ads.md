---
author: mcleanbyron
description: UWP アプリにネイティブ広告を追加する方法について説明します。
title: ネイティブ広告
ms.author: mcleans
ms.date: 03/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, 広告, Advertising, 広告コントロール, ネイティブ広告
ms.localizationpriority: medium
ms.openlocfilehash: ff7c9249989526a454ffd702f3f95d1ebc4b4566
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
ms.locfileid: "1690548"
---
# <a name="native-ads"></a>ネイティブ広告

ネイティブ広告は、コンポーネント ベースの広告形式で、各広告クリエイティブ (タイトル、画像、説明、行動喚起テキストなど) が個々の要素としてアプリに配信されます。 これらの要素は、独自のフォント、色、アニメーション、その他の UI コンポーネントを使ってアプリに統合して、アプリの外観に合った控えめなユーザー エクスペリエンスを組み込むことができるうえに、広告から高収益を獲得できます。

広告主のために、ネイティブ広告では高パフォーマンスの配置が提供されます。広告エクスペリエンスがアプリに密接に統合されることで、ユーザーがこのような種類の広告と対話しやすくなる傾向があるためです。

> [!NOTE]
> ネイティブ広告を Store 内の公開バージョンのアプリに提供するには、デベロッパー センター ダッシュボードの **[収益化]** &gt; **[アプリ内広告]** ページから、**ネイティブ**の広告ユニットを作成する必要があります。 **ネイティブ**広告ユニットを作成する機能は、現在はパイロット プログラムに参加している開発者だけが利用できますが、まもなくすべての開発者がこの機能を利用できるようにする予定です。 パイロット プログラムへの参加に関心がある方は、aiacare@microsoft.com までお問い合わせください。

> [!NOTE]
> ネイティブ広告は現在、XAML ベースの Windows 10 用 UWP アプリでのみサポートされています。 HTML と JavaScript を使って作成された UWP アプリについては、今後リリースされる Microsoft Advertising SDK でサポートされる予定です。

## <a name="prerequisites"></a>前提条件

* Visual Studio 2015 以降の Visual Studio のリリースと共に [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) をインストールします。 インストール手順については、[この記事](install-the-microsoft-advertising-libraries.md)をご覧ください。

## <a name="integrate-a-native-ad-into-your-app"></a>ネイティブ広告をアプリに統合する

次の手順に従って、ネイティブ広告をアプリに統合し、ネイティブ広告の実装によってテスト広告が表示されることを確認します。

1. Visual Studio でプロジェクトを開くか、新しいプロジェクトを作ります。
    > [!NOTE]
    > 既存のプロジェクトを使用している場合、プロジェクトの Package.appxmanifest ファイルを開き、**インターネット (クライアント)** 機能が選択されていることを確認します。 アプリでは、テスト広告やライブ広告を受信するためにこの機能が必要になります。

2. プロジェクトのターゲットが **[任意の CPU]** になっている場合は、アーキテクチャ固有のビルド出力 (たとえば、**[x86]**) を使うようにプロジェクトを更新します。 プロジェクトのターゲットが **[Any CPU]** (任意の CPU) になっていると、次の手順で Microsoft Advertising SDK への参照を正常に追加できません。 詳しくは、「[プロジェクトのターゲットを "任意の CPU" に設定すると参照エラーが発生する](known-issues-for-the-advertising-libraries.md#reference_errors)」をご覧ください。

3. プロジェクトで Microsoft Advertising SDK への参照を追加します。

    1. **[ソリューション エクスプローラー]** ウィンドウで、**[参照設定]** を右クリックし、**[参照の追加]** を選択します。
    2.  **[参照マネージャー]** で、**[Universal Windows]** を展開し、**[拡張]** をクリックして、**[Microsoft Advertising SDK for XAML]** (バージョン 10.0) の横にあるチェック ボックスをオンにします。
    3.  **[参照マネージャー]** で、[OK] をクリックします。

4. アプリの適切なコード ファイル (たとえば、MainPage.xaml.cs またはその他のページのコード ファイル) に、次の名前空間の参照を追加します。

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#Namespaces)]

5.  アプリの適切な場所 (たとえば、```MainPage``` またはその他のページ) で、[NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.aspx) オブジェクトと、ネイティブ広告のアプリケーション ID および広告ユニット ID を表す複数の文字列フィールドを宣言します。 次のコード例は、`myAppId` と `myAdUnitId`フィールドに、ネイティブ広告の setup-ad-units-in-your-app.md#live-ad-units を割り当てます。
    > [!NOTE]
    > 各 **NativeAdsManager** に、対応する*広告ユニット*があります。広告ユニットは、ネイティブ広告コントロールに広告を提供するためにサービスで使われます。すべての広告ユニットは、*広告ユニット ID* と*アプリケーション ID* で構成されます。 ここでは、広告ユニット ID とアプリケーション ID のテスト値をコントロールに割り当てます。 これらのテスト値は、テスト バージョンのアプリでのみ使用できます。 Microsoft Store にアプリを公開する前に、[これらのテスト値を Windows デベロッパー センターから取得した実際の値に置き換える](#release)必要があります。

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#Variables)]

6.  起動時に実行されるコード (たとえば、ページのコンストラクター) 内で、**NativeAdsManager** オブジェクトをインスタンス化し、このオブジェクトの [AdReady](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.adready.aspx) イベントと [ErrorOccurred](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.erroroccurred.aspx) イベント用のイベント ハンドラーを関連付けます。

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#ConfigureNativeAd)]

7.  ネイティブ広告を表示する準備ができたら、[RequestAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.requestad.aspx) メソッドを呼び出して、広告を取得します。

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#RequestAd)]

8.  アプリ用にネイティブ広告の準備ができたら、**AdReady** イベント ハンドラーが呼び出され、ネイティブ広告を表す [NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx) オブジェクトが *e* パラメーターに渡されます。 **NativeAd** プロパティを使ってネイティブ広告の各要素を取得し、ページ上にそれらの要素を表示します。 また、[RegisterAdContainer](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.registeradcontainer.aspx) メソッドを呼び出して、ネイティブ広告のコンテナーとして機能する UI 要素を登録してください。広告インプレッションと広告クリックを適切に追跡するために必要です。
    > [!NOTE]
    > ネイティブ広告の一部の要素は必須であり、アプリに常に表示する必要があります。 詳しくは、「[ネイティブ広告のガイドライン](ui-and-user-experience-guidelines.md#guidelines-for-native-ads)」をご覧ください。

    たとえば、アプリに次のような **StackPanel** を持つ ```MainPage``` (またはその他のページ) が含まれているとします。 この **StackPanel** には、ネイティブ広告のさまざまな要素 (タイトル、説明、画像、*スポンサー* テキスト、*行動喚起*テキストを表示するボタンなど) を表示する一連のコントロールが含まれています。

    ``` xml
    <StackPanel x:Name="NativeAdContainer" Background="#555555" Width="Auto" Height="Auto"
                Orientation="Vertical">
        <Image x:Name="AdIconImage" HorizontalAlignment="Left" VerticalAlignment="Center"
               Margin="20,20,20,20"/>
        <TextBlock x:Name="TitleTextBlock" HorizontalAlignment="Left" VerticalAlignment="Center"
               Text="The ad title will go here" FontSize="24" Foreground="White" Margin="20,0,0,10"/>
        <TextBlock x:Name="DescriptionTextBlock" HorizontalAlignment="Left" VerticalAlignment="Center"
                   Foreground="White" TextWrapping="Wrap" Text="The ad description will go here"
                   Margin="20,0,0,0" Visibility="Collapsed"/>
        <Image x:Name="MainImageImage" HorizontalAlignment="Left"
               VerticalAlignment="Center" Margin="20,20,20,20" Visibility="Collapsed"/>
        <Button x:Name="CallToActionButton" Background="Gray" Foreground="White"
                HorizontalAlignment="Left" VerticalAlignment="Center" Width="Auto" Height="Auto"
                Content="The call to action text will go here" Margin="20,20,20,20"
                Visibility="Collapsed"/>
        <StackPanel x:Name="SponsoredByStackPanel" Orientation="Horizontal" Margin="20,20,20,20">
            <TextBlock x:Name="SponsoredByTextBlock" Text="The ad sponsored by text will go here"
                       FontSize="24" Foreground="White" Margin="20,0,0,0" HorizontalAlignment="Left"
                       VerticalAlignment="Center" Visibility="Collapsed"/>
            <Image x:Name="IconImageImage" Margin="40,20,20,20" HorizontalAlignment="Left"
                   VerticalAlignment="Center" Visibility="Collapsed"/>
        </StackPanel>
    </StackPanel>
    ```

    次のコード例は、**StackPanel** のコントロールにネイティブ広告の各要素を表示してから、**RegisterAdContainer** メソッドを呼び出して **StackPanel** を登録する **AdReady** イベント ハンドラーを示しています。 このコードでは、**StackPanel** が含まれているページの分離コード ファイルから実行されることを想定しています。

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#AdReady)]

9.  **ErrorOccurred** イベントのイベント ハンドラーを定義して、ネイティブ広告に関連するエラーを処理します。 次の例では、テスト中に Visual Studio の **[出力]** ウィンドウにエラー情報を書き込みます。

    [!code-cs[NativeAd](./code/AdvertisingSamples/NativeAdSamples/cs/MainPage.xaml.cs#ErrorOccurred)]

10.  アプリをコンパイルして実行し、テスト広告が表示されることを確認します。

<span id="release" />

## <a name="release-your-app-with-live-ads"></a>ライブ広告を表示するアプリをリリースする

ネイティブ広告の実装によってテスト広告が正常に表示されることを確認したら、次の手順に従って、実際の広告を表示するようにアプリを構成し、更新したアプリをストアに提出します。

1.  ネイティブ広告の実装が[ネイティブ広告のガイドライン](ui-and-user-experience-guidelines.md#guidelines-for-native-ads)に従っていることを確認してください。

2.  デベロッパー センター ダッシュボードで、[[アプリ内広告]](../publish/in-app-ads.md) ページに移動し、[広告ユニットを作成](set-up-ad-units-in-your-app.md#live-ad-units)します。 広告ユニットの種類として、**[ネイティブ]** を指定します。 広告ユニット ID とアプリケーション ID の両方を書き留めておきます。
    > [!NOTE]
    > テスト広告ユニットとライブ UWP 広告ユニットでは、アプリケーション ID の値の形式が異なります。 テスト アプリケーション ID の値は GUID です。 ダッシュボードでライブ UWP 広告ユニットを作成する場合、広告ユニットのアプリケーション ID の値は常にアプリの Store ID に一致します (Store ID 値は、たとえば 9NBLGGH4R315 のようになります)。

3. 必要に応じて、[[アプリ内広告]](../publish/in-app-ads.md) ページの [[仲介設定]](../publish/in-app-ads.md#mediation) セクションで設定を構成することで、ネイティブ広告の広告仲介を有効にできます。 広告仲介を利用すると、複数の広告ネットワークから広告を表示して、広告収益とアプリ プロモーションの機能を最大限に引き出すことができます。

4.  コードで、広告ユニットのテスト値 ([NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.nativeadsmanager.aspx) コンストラクターの *applicationId* パラメーターと *adUnitId* パラメーター) を、デベロッパー センターで生成した実際の値に置き換えます。

5.  デベロッパー センター ダッシュボードを使用して、ストアに[アプリを申請](../publish/app-submissions.md)します。

6.  デベロッパー センター ダッシュボードで[広告パフォーマンス レポート](../publish/advertising-performance-report.md)を確認します。

## <a name="manage-ad-units-for-multiple-native-ads-in-your-app"></a>アプリで複数のネイティブ広告の広告ユニットを管理する

1 つのアプリで複数のネイティブ広告を使用することができます。 このシナリオでは、各ネイティブ広告の配置に異なる広告ユニットを割り当てることをお勧めします。 各コントロールに異なるネイティブ広告ユニットを使用することで、別々に[仲介の設定を構成](../publish/in-app-ads.md#mediation)して、個別の[報告データ](../publish/advertising-performance-report.md)を取得できます。 また、これにより、Microsoft のサービスはアプリに提供する広告を最適化できます。

> [!IMPORTANT]
> 各広告ユニットは 1 つのアプリのみで使用できます。 複数のアプリで広告ユニットを使うと、広告ユニットに広告が提供されません。

## <a name="related-topics"></a>関連トピック

* [ネイティブ広告のガイドライン](ui-and-user-experience-guidelines.md#guidelines-for-native-ads)
* [アプリ内広告](../publish/in-app-ads.md)
* [アプリの広告ユニットをセットアップする](set-up-ad-units-in-your-app.md)