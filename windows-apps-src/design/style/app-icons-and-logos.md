---
author: mijacobs
Description: How to create app icons/logos that represent your app in the Start menu, app tiles, the taskbar, the Microsoft Store, and more.
title: アプリのアイコンとロゴ
template: detail.hbs
ms.author: mijacobs
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 136a52cedd7d4b0599adaff08fd0860260da4ce3
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "3662688"
---
# <a name="app-icons-and-logos"></a>アプリのアイコンとロゴ 

すべてのアプリが、それを表す、アイコン/ロゴと Windows シェルの複数の場所にそのアイコンが表示されます。 

:::row:::
    :::column:::
        *、アプリ ウィンドウのタイトル バー * [スタート] メニューで、アプリの一覧 *、タスク バーとタスク マネージャー * アプリのタイル * アプリのスプラッシュ画面 * Microsoft ストア内 :::column-end:::
    :::column:::
        ![Windows 10 のスタート画面とタイル](images/assetguidance01.jpg)
    :::column-end:::
:::row-end:::

この記事では、アプリ アイコンの作成の基本を説明する必要がありますが、それらを管理し、それらを手動で管理する方法を Visual Studio を使用する方法。
 
(この記事は、具体的にはアイコンをアプリ自体を表すアイコンの一般的なガイダンスについては、[アイコン](icons.md)に関する記事を参照してください。)

## <a name="icon-types-locations-and-scale-factors"></a>アイコンの種類、場所、およびスケール ファクター

既定では、Visual Studio は、アセットのサブディレクトリに、アイコン アセットを格納します。 呼び出されたいるアイコン、表示される場所のさまざまな種類の一覧を示します。 

| アイコン名 | 表示されます。 | アセット ファイル名 |
| ---      | ---        | --- |
| 小さいタイル | スタート メニュー |  SmallTile.png  |
| 普通サイズのタイル |スタート メニューで、Microsoft Store listing\ *  |  Square150x150Logo.png |
| ワイド タイル  | スタート メニュー   | Wide310x150Logo.png |
| 大きいタイル   | スタート メニューで、Microsoft Store listing\ * |  LargeTile.png  |
| アプリのアイコン | [スタート] メニューのタスク バー、タスク マネージャーでのアプリの一覧 | Square44x44Logo.png |
| スプラッシュ画面 | アプリのスプラッシュ画面 | SplashScreen.png  |
| バッジ ロゴ | アプリのタイル | BadgeLogo.png  |
| パッケージのロゴ/ストア ロゴ | アプリ インストーラー, デベロッパー センターで、ストアでは、ストアで「レビューの書き込み」オプション「アプリを報告」オプション | StoreLogo.png  |

\ * しない限り、[アップロードされたストア内の画像のみを表示](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store)することも使用します。 

これらのアイコンに鮮明にすべての画面で表示を確認するには、複数の表示スケール ファクターの同じアイコンの複数のバージョンを作成できます。 

スケール ファクターは、テキストなどの UI 要素のサイズを決定します。 400% から 100% の要因の範囲が拡大縮小します。 値を大きくやすく高 DPI ディスプレイに表示するためより大きな UI 要素を作成します。 

:::row:::
    :::column:::
        Windows では、ディスプレイの DPI (ドット/インチ) と、デバイスの視聴距離に基づいて各ディスプレイの倍率が自動的に設定します。 

        (Users can override the default value by going to the **Settings &gt; Display &gt; Scale and layout** page.)
    :::column-end:::
    :::column:::
        ![](images/icons/display-settings-screen.png)
    :::column-end:::
:::row-end:::  


アプリ アイコン アセットはビットマップのビットマップが適切に拡大縮小されないため、お勧めしますバージョン各アイコン アセットの各スケール ファクター: 100%、125%、150%、200%、400% です。 アイコンの多くは正常です。 な Visual Studio では、簡単に生成し、これらのアイコンを更新するツールを提供します。 

## <a name="microsoft-store-listing-image"></a>Microsoft Store 登録情報の画像

「をどのように指定自分のアプリの登録情報の画像、Microsoft Store でですか?」

既定では、一部のパッケージから画像で使います、ストアでは、(その他の[申請プロセス中に提供するイメージ](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)) と共にこのページの上部にある表で説明。 ただし、Windows 10 (Xbox を含む) のユーザーに、登録情報を表示するとき、アプリのパッケージのロゴ画像を使用してから、ストアを防ぐため、代わりにアップロードした画像のみを使用して、ストア オプションがあります。 これにより、アプリの外観の詳細に制御では、ストアのさまざまな表示。 (注こと、製品では、以前の OS バージョンをサポートする場合それらのユーザー可能性があります引き続き表示イメージ、パッケージから場合でも、このオプションを使用する。)**ストア ロゴ**の提出プロセスの**ストア登録情報**の手順のセクションで、これを行うことができます。

![アプリの申請プロセス中にストア ロゴを指定します。](images/app-icons/storelogodisplay.png)

このチェック ボックスをオンにすると、**ストアで表示する画像**と呼ばれる新しいセクションが表示されます。 ここでは、ストアでは、アプリのパッケージからのロゴ画像の代わりに使います 3 つのサイズの画像をアップロードすることができます。 300 x 300 ピクセル、150 x 150、71 x 71 ピクセル ピクセルです。 すべての 3 つのサイズを提供することをお勧めします 300 x 300 のサイズだけが必要です。

詳しくは、[ディスプレイがストアでのロゴ画像をアップロードのみ](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store)を参照してください。

<!-- ### Fallback images for the Store

The simplest way to control the Store listing image is to specify it during the app submission process. If you don't provide these images during the app submission process, the Store will use a tile image:

1. Large tile
2. Medium tile

If these images aren't provided, the Store will search all matching images of the same image type with a square aspect ratio, preferable with a height greated than the scaled requested height (scaled height is the machine's resolution scale factor * display height). If none of the images meet this criteria, the Store will ignore the scale factor and select an image based on height.  -->

<!-- You can provide screenshots, logos, and other art assets (such as trailers and promotional images to include in your app's Microsoft Store listing. Some of these are required, and some are optional (although some of the optional images are important to include for the best Store display).

The Store may also use your app's tile and other images that you include in your app's package. 

For more information, see [App screenshots, images, and trailers in the Microsoft Store](/windows/uwp/publish/app-screenshots-and-images). -->


## <a name="managing-app-icons-with-the-visual-studio-manifest-designer"></a>Visual Studio マニフェスト デザイナーでのアプリ アイコンを管理します。

Visual Studio では、**マニフェスト デザイナー**と呼ばれる、アプリのアイコンを管理するために非常に便利なツールを提供します。 

> Visual Studio 2017 がまだしていない場合、無料のバージョン (Visual Studio 2017 Community Edition) を含め、利用可能ないくつかのバージョンと、他のバージョンは、無料試用版を提供します。 ここでダウンロードすることができます。[https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)


マニフェスト デザイナーを起動します。
<!-- 1. Use Visual Studio to open a UWP project.
2. In the **Solution Explorer**, double-click the package.appmanifest file. 

    ![The Visual Studio 2017 Solution Explorer](images/icons/vs-solution-explorer.png)

    Visual Studio displays the manifest designer.

    ![The Visual Studio 2017 manifest designer](images/icons/vs-manfiest-designer.png)
3. Click the **Visual Assets** tab.

    ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png) -->


:::row:::
    :::column:::
        1. Visual Studio を使用して UWP プロジェクトを開きます。
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        2.**ソリューション エクスプ ローラー**で、package.appmanifest ファイルをダブルクリックします。
    :::column-end:::
    :::column:::
        ![Visual Studio 2017 のマニフェスト デザイナー](images/icons/vs-solution-explorer.png)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
            Visual Studio では、マニフェスト デザイナーが表示されます。
    :::column-end:::
    :::column:::
            ![ビジュアル資産] タブ](images/icons/vs-manfiest-designer.png)
    :::column-end:::
:::row-end:::    
:::row:::
    :::column:::
        3.**ビジュアル資産**] タブをクリックします。 :::column-end:::
    :::column:::
        ![ビジュアル資産] タブ](images/icons/vs-manfiest-designer-visual-assets.png)
    :::column-end:::
:::row-end:::        

## <a name="generating-all-assets-at-once"></a>一度にすべてのアセットの生成

**[ビジュアル資産**] タブで、**すべてのビジュアル アセット**、最初のメニュー項目はその名前が示す内容正確: ボタンを押すと、アプリが必要なすべてのビジュアル アセットが生成されます。

![Visaul Studio ですべてのビジュアル資産を生成します。](images/app-icons/all-visual-assets.png)

実行する必要があるすべてサプライ 1 つの画像は、Visaul Studio は小さいタイル、普通サイズのタイル、大きいタイル、ワイド タイル、大きいタイル、アプリ アイコン、スプラッシュ画面を生成してすべての倍率のアセットをロゴをパッケージ化します。

すべてのアセットを一度に生成するには。
1. **ソース**フィールドの横にある **...** をクリックし、使用するイメージを選択します。 ビットマップ画像を使用している場合が 400 ピクセル以上 400 鋭い結果を取得することを確認します。 ベクター ベースの画像が最適です。Visual Studio では、AI (Adobe Illustrator) と PDF ファイルを使用することができます。 
2. (省略可能)**ディスプレイの設定]** セクションでは、これらのオプションを構成します。

    a.   **短い名前**: アプリの短い名前を指定します。

    b.   **表示名**: 普通、ワイド、または大きいタイルの短い名前を表示するかどうかを指定します。 

    c. **バック グラウンドのタイル**: 16 進値またはタイルの背景色の色の名前を指定します。 たとえば、`#464646` と記述します。 既定値は、`transparent` です。

    d. **画面の背景を Spash**: spash 画面の背景の 16 進値または色の名前を指定します。 

3. [**生成**] をクリックします。 

Visual Studio では、イメージ ファイルを生成し、プロジェクトに追加します。 アセットを変更する場合は、単にプロセスを繰り返します。 

拡大/縮小されたアイコン アセットは、このファイルの名前付け規則に従います。

*ファイル名*規模の*拡大縮小率*.png

例:

Square150x150Logo-スケール-100.png、Square150x150Logo-スケール-200.png、Square150x150Logo-スケール-400.png

Visual Studio が既定ではバッジ ロゴを生成しないことに注意してください。 バッジ ロゴは一意であり、おそらく、その他のアプリ アイコンに一致しないようにするためです。 詳しくは、 [UWP アプリの記事のバッジ通知](/windows/uwp/design/shell/tiles-and-notifications/badges)を参照してください。 


## <a name="more-about-app-icon-assets"></a>詳細については、アプリ アイコン アセット
Visual Studio プロジェクトに必要なすべてのアプリ アイコン アセットが生成されますが、いるその他のアプリのアセットとは異なる方法を理解して、それらをカスタマイズする場合は、できます。 

多くの場所でアプリ アイコン アセットが表示されます。 Windows タスク バー、タスク ビュー、ALT + TAB、およびスタート画面のタイルの右下隅します。 いくつか追加のサイズ変更とオプションがないその他の資産を plating があるため、非常に多くの場所でアプリ アイコン アセットが表示されたら、:「ターゲット サイズ」アセットと「プレートなし」のアセットです。 

### <a name="target-size-app-icon-assets"></a>ターゲット サイズのアプリ アイコン アセット
だけでなく、標準的なスケール ファクター サイズ ("Square44x44Logo.scale 400.png") もお勧めします「ターゲット サイズ」アセットを作成します。 これらのアセットのターゲットのサイズと呼ば 400 などの特定のスケール ファクターではなく、16 ピクセルなどの特定のサイズをターゲットにするためです。 ターゲット サイズのアセットは、スケール プラトー システムを使用していないサーフェスしています。

* スタート画面のジャンプ リスト (デスクトップ)
* スタート画面のタイルの下隅 (デスクトップ)
* ショートカット (デスクトップ)
* コントロール パネル (デスクトップ)

ターゲット サイズのアセットの一覧を以下に示します。


| アセットのサイズ | ファイル名の例                  |
|------------|------------------------------------|
| 16 x 16\*    | Square44x44Logo.targetsize-16.png  |
| 24 x 24\*    | Square44x44Logo.targetsize-24.png  |
| 32 x 32\*    | Square44x44Logo.targetsize-32.png  |
| 48 x 48\*    | Square44x44Logo.targetsize-48.png  |
| 256 x 256\*  | Square44x44Logo.targetsize-256.png |
| 20 x 20      | Square44x44Logo.targetsize-20.png  |
| 30 x 30      | Square44x44Logo.targetsize-30.png  |
| 36 x 36      | Square44x44Logo.targetsize-36.png  |
| 40 x 40      | Square44x44Logo.targetsize-40.png  |
| 60 x 60      | Square44x44Logo.targetsize-60.png  |
| 64 x 64      | Square44x44Logo.targetsize-64.png  |
| 72 x 72      | Square44x44Logo.targetsize-72.png  |
| 80 x 80      | Square44x44Logo.targetsize-80.png  |
| 96 x 96      | Square44x44Logo.targetsize-96.png  |

\ * 少なくとも、お勧めしますこれらのサイズを提供します。 

これらのアセットにパディングを追加する必要はありません。パディングは、必要に応じて Windows によって追加されます。 これらのアセットは、16 ピクセルの最小面積を占めている必要があります。 

Windows タスク バーのアイコンに表示される、このようなアセットの例を以下に示します。

![Windows タスク バーのアセット](images/assetguidance21.png)

### <a name="unplated-assets"></a>プレートなしのアセット
既定では、Windows は、既定で色付きバック プレート上のターゲット ベースのアセットを使用します。 する場合は、ターゲット ベースのプレートなしのアセットを提供することができます。 「プレートなし」は、透明な背景に表示されるアセットを意味します。 これらのアセットは、さまざまな背景色で表示されることに留意してください。 

![プレートなしのアセットとプレート付きのアセット](images/assetguidance22.png)

プレートなしのアプリ アイコン アセットを使用するサーフェスを以下に示します。
* タスク バーとタスク バー サムネイル (デスクトップ)
* タスク バーのジャンプ リスト
* タスク ビュー
* Alt + Tab キー


### <a name="target-and-unplated-sizing"></a>ターゲットとプレートなしのサイズ調整

倍率 100% のターゲット ベースのアセットのサイズの推奨事項を以下に示します。

![100% の倍率でのターゲット ベースのアセットのサイズ調整](images/assetguidance23.png)


## <a name="more-about-splash-screen-assets"></a>詳細については、スプラッシュ画面のアセット
スプラッシュ画面について詳しくは、 [UWP のスプラッシュ画面の記事](/windows/uwp/launch-resume/splash-screens)をご覧ください。

## <a name="more-about-badge-logo-assets"></a>詳細についてはバッジ ロゴのアセット

既定ではバッジ ロゴを理由生成しない理由を必要となるすべてのアセットを生成するアセット ジェネレーターを使用する場合に: している他のアプリのアセットとは大きく異なります。 バッジ ロゴは、通知であり、アプリのタイルに表示されるステータス イメージです。 

詳しくは、 [UWP アプリの記事のバッジ通知](/windows/uwp/design/shell/tiles-and-notifications/badges)を参照してください。


## <a name="customizing-asset-padding"></a>アセットのパディングをカスタマイズします。

既定では、Visual Studio アセット ジェネレーターには、任意の画像に、推奨されるパディングが適用されます。 イメージが既にパディングを含めるや、タイルの末尾に拡張フルブリード イメージの場合場合、**適用パディングを推奨**] チェック ボックスをオフにしてこの機能を無効にできます。 

### <a name="tile-padding-recommendations"></a>タイルの余白の推奨事項
独自のパディングを提供する場合は、タイルの推奨事項を示します。 

ある 4 つのタイル サイズ: 小 (71 x 71) 中 (150 x 150)、全体 (150 x 310)、大規模な (310 x 310)。 

各タイル アセットは、配置されるタイルと同じサイズです。

![タイル表示フルブリード](images/app-icons/tile-assets1.png)

アイコン タイルの端まで拡張しない場合は、パディングを作成する、アセットで透明のピクセルを使用することができます。 

![タイルとバック プレート](images/assetguidance05.png)

小さいタイルでは、アイコンの幅と高さをタイル サイズの 66% に制限します。

![小さいタイルのサイズの比率](images/assetguidance09.png)

普通サイズのタイルでは、アイコンの幅をタイル サイズの 66% に、高さをタイル サイズの 50% に制限します。 これによって、ブランド バー内の要素と重ならないようにします。

![普通サイズのタイルのサイズの比率](images/assetguidance10.png)

ワイド タイルでは、アイコンの幅をタイル サイズの 66% に、高さをタイル サイズの 50% に制限します。 これによって、ブランド バー内の要素と重ならないようにします。

![ワイド タイルのサイズの比率](images/assetguidance11.png)

大きいタイルでは、アイコンの幅をタイル サイズの 66% に、高さをタイル サイズの 50% に制限します。

![大きいタイルのサイズの比率](images/assetguidance12.png)

水平方向または垂直方向にデザインされたアイコンがある一方で、ターゲット サイズの正方形に収まらない、より複雑な形状のアイコンもあります。 中央に配置されるアイコンの一方の辺に重みを付けることができます。 この場合、アイコンの視覚的な重みが正方形に収まるアイコンと同じであれば、アイコンの一部が推奨される面積の外側にはみ出していてもかまいません。

![中央に配置された 3 つのアイコン](images/assetguidance13.png)

フルブリード アセットでは、要素が余白およびタイルの端の内側に接するように考慮します。 タイルの高さまたは幅の 16% 以上の余白を維持します。 この割合は、最小タイル サイズでの余白の幅の 2 倍を表しています。

![余白のあるフルブリード タイル](images/assetguidance14.png)

次の例では、余白が狭すぎます。

![余白が小さすぎるフルブリード タイル](images/assetguidance15.png)








