---
author: mcleanbyron
ms.assetid: bb105fbe-bbbd-4d78-899b-345af2757720
description: アプリをストアに提出する前に、Windows デベロッパー センター ダッシュ ボードからアプリケーション ID と広告ユニット ID の値をアプリに追加する方法について説明します。
title: アプリの広告ユニットをセットアップする
ms.author: mcleans
ms.date: 10/04/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, 広告, Advertising, 広告ユニット, テスト
ms.localizationpriority: medium
ms.openlocfilehash: 6473d571ed44f60f8001b8a565d70c58d43407d1
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
ms.locfileid: "1654661"
---
# <a name="set-up-ad-units-in-your-app"></a>アプリの広告ユニットをセットアップする

ユニバーサル Windows プラットフォーム (UWP) アプリ内の各広告コントロールには、対応する*広告ユニット*があります。広告ユニットは、コントロールに広告を提供するためにサービスで使用されます。 各広告ユニットは、*広告ユニット ID* と*アプリケーション ID* があり、これらをアプリ内で [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)、[InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)、[NativeAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativead.aspx) に割り当てる必要があります。

テスト中にテスト広告がアプリに表示されていることを確認するために使用できる[テスト広告ユニット値](#test-ad-units)が用意されています。 これらのテスト値は、テスト バージョンのアプリでのみ使用できます。 いったん公開したアプリでテスト用の値を使うと、ライブ アプリで広告は表示されません。

UWP アプリのテストが終了し、Windows デベロッパー センターに提出する準備ができたら、Windows デベロッパー センター ダッシュボードの [[アプリ内広告]](../publish/in-app-ads.md) ページから[ライブ広告ユニットを作成](#live-ad-units)し、この広告ユニットのアプリケーション ID と広告ユニット ID の値を使うようにアプリ コードを更新する必要があります。

<span id="test-ad-units" />

## <a name="test-ad-units"></a>広告ユニットをテストする

アプリを開発しているときには、このセクションに示されているテスト用のアプリケーション ID と広告ユニット ID の値を使って、テスト時にアプリでどのように広告がレンダリングされるかを確認します。

### <a name="banner-ads-using-the-adcontrol-class"></a>バナー広告 (AdControl クラスを使用)

* 広告ユニット ID: ```test```
* アプリケーション ID:  ```3f83fe91-d6be-434d-a0ae-7351c5a997f1```

    > [!IMPORTANT]
    > **AdControl** では、ライブ広告のサイズは **Width** プロパティと **Height** プロパティによって定義されます。 最善の結果を得るには、コード内の **Width** プロパティと **Height** プロパティが、[バナー広告でサポートされている広告サイズ](supported-ad-sizes-for-banner-ads.md)のいずれかであることを確認します。 **Width** プロパティと **Height** プロパティは、ライブ広告のサイズに基づいて変更されません。

### <a name="interstitial-ads-and-native-ads"></a>スポット広告やネイティブ広告

* 広告ユニット ID: ```test```
* アプリケーション ID:  ```d25517cb-12d4-4699-8bdc-52040c712cab```

<span id="live-ad-units" />

## <a name="live-ad-units"></a>ライブ広告ユニット

デベロッパー センター ダッシュボードからライブ広告ユニットを取得し、アプリで使用するには、次の手順を実行します。

1.  ダッシュボードの **[アプリ内広告]** ページで、[広告ユニットを作成](../publish/in-app-ads.md#create-ad-unit)します。 アプリで使用している広告コントロールに合わせて、適切な種類の広告ユニットを指定してください。
    > [!NOTE]
    > 必要に応じて、[[仲介設定]](../publish/in-app-ads.md#mediation) セクションで設定を構成することで、広告ユニットの広告仲介を有効にできます。 広告仲介を使うと、複数の広告ネットワークから広告を表示して、広告収益とアプリ プロモーションの機能を最大限に引き出すことができます。表示される広告には、他の有料広告ネットワークからの広告や、Microsoft のアプリ プロモーション キャンペーン用の広告などが含まれます。 既定では、アプリがサポートする市場全体で広告の収益を最大化できるように、機械学習アルゴリズムを使った仲介設定が自動的に構成されますが、必要に応じて仲介設定を手動で構成することができます。

2.  新しい広告ユニットを作成したら、**[収益化]** &gt; **[アプリ内広告]** ページにある利用可能な広告ユニットの表で、作成した広告ユニットの**アプリケーション ID** と**広告ユニット ID** を取得します。
    > [!NOTE]
    > テスト広告ユニットとライブ UWP 広告ユニットでは、アプリケーション ID の値の形式が異なります。 テスト アプリケーション ID の値は GUID です。 ダッシュボードでライブ UWP 広告ユニットを作成する場合、広告ユニットのアプリケーション ID の値は常にアプリの Store ID に一致します (Store ID 値は、たとえば 9NBLGGH4R315 のようになります)。

3.  アプリのコードで、**アプリケーション ID** と**広告ユニット ID** の値を割り当てます。

    * アプリにバナー広告を表示する場合は、これらの値を [AdControl](https://msdn.microsoft.com/library/mt313154.aspx) オブジェクトの [ApplicationId](https://msdn.microsoft.com/library/mt313174.aspx) プロパティと [AdUnitId](https://msdn.microsoft.com/library/mt313171.aspx) プロパティに割り当てる必要があります。 詳しくは、「[XAML および .NET の AdControl](../monetize/adcontrol-in-xaml-and--net.md)」、または「[HTML5 および JavaScript の AdControl](../monetize/adcontrol-in-html-5-and-javascript.md)」をご覧ください。

    * アプリでスポット広告を表示する場合は、[InterstitialAd](https://msdn.microsoft.com/library/mt313189.aspx) オブジェクトの [RequestAd](https://msdn.microsoft.com/library/mt313192.aspx) メソッドにこれらの値を渡します。 詳しくは、「[スポット広告](../monetize/interstitial-ads.md)」をご覧ください。

    * アプリにネイティブ広告が表示される場合、それらの値を [NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.nativeadsmanager.aspx) コンストラクターの *applicationId* パラメーターと *adUnitId* パラメーターに渡します。 詳しくは、「[ネイティブ広告](../monetize/native-ads.md)」をご覧ください。

<span id="manage" />

## <a name="manage-ad-units-for-multiple-ad-controls-in-your-app"></a>アプリで複数の広告コントロールの広告ユニットを管理する

1 つのアプリに複数のバナー広告コントロール、スポット広告コントロール、ネイティブ広告コントロールを使用できます。 このシナリオでは、各コントロールに異なる広告ユニットを割り当てることをお勧めします。 各コントロールに異なる広告ユニットを使用することで、別々に[仲介の設定を構成](../publish/in-app-ads.md#mediation)して、個別の[報告データ](../publish/advertising-performance-report.md)を取得することが可能です。 また、これにより、Microsoft のサービスはアプリに提供する広告を最適化できます。

> [!IMPORTANT]
> 各広告ユニットは 1 つのアプリのみで使用できます。 複数のアプリで広告ユニットを使うと、広告ユニットに広告が提供されません。

## <a name="related-topics"></a>関連トピック

* [XAML および .NET の AdControl](adcontrol-in-xaml-and--net.md)
* [HTML 5 および Javascript の AdControl](adcontrol-in-html-5-and-javascript.md)
* [スポット広告](interstitial-ads.md)
* [ネイティブ広告](native-ads.md)


 

 