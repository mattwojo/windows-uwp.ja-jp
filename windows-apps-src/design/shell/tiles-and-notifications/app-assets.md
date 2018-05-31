---
author: mijacobs
Description: App icon assets, which appear in a variety of forms throughout the Windows 10 operating system, are the calling cards for your Universal Windows Platform (UWP) app.
title: タイルとアイコン アセット
ms.assetid: D6CE21E5-2CFA-404F-8679-36AA522206C7
label: Tile and icon assets
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: cc614f7803e7546add8ecccb7cc20dc0250d0d22
ms.sourcegitcommit: eead3c00b27d9f66f79ec08c81a97e91dc1fdb3c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
ms.locfileid: "1522791"
---
# <a name="guidelines-for-tile-and-icon-assets"></a>タイルとアイコン アセットのガイドライン

 


Windows 10 オペレーティング システム全体でさまざまな形式で表示される、アプリ アイコン アセットは、ユニバーサル Windows プラットフォーム (UWP) アプリの名刺です。 このガイドラインでは、システム内でアプリ アイコン アセットが表示される場所の詳細について説明し、最も洗練されたアイコンを作成する方法に関して詳細なデザインのヒントを提供します。

![Windows 10 のスタート画面とタイル](images/assetguidance01.jpg)

## <a name="adaptive-scaling"></a>アダプティブ スケーリング


まず、スケーリングとアセットがどのように連携しているかを深く理解するために、アダプティブ スケーリングの概要について簡単に説明します。 Windows 10 には、既存のスケーリング モデルの進化形が導入されています。 表示スケール ベクター コンテンツに加えて、さまざまな画面サイズと画面の解像度で UI 要素に一貫したサイズを提供するスケール ファクターの統合されたセットがあります。 スケール ファクターは、iOS や Android などの他のオペレーティング システムのスケール ファクターとも互換性があり、これにより、こうしたプラットフォーム間でのアセットの共有が簡単になります。

Microsoft Store では、デバイスの dpi も考慮に入れて、ダウンロードするアセットが選ばれます。 デバイスに最適なアセットのみがダウンロードされます。

## <a name="tile-elements"></a>タイル要素


スタート画面のタイルの基本コンポーネントは、バック プレート、アイコン、ブランド バー、余白、およびアプリのタイトルで構成されます。

![タイルの要素の詳細](images/assetguidance02.png)

タイルの下部にあるブランド バーは、アプリ名、バッジ、カウンター (使用する場合) が表示される場所です。

![タイルのブランド バー](images/assetguidance03.png)

ブランドのバーの高さは、表示されているデバイスの倍率に基づいています。

| 倍率 | ピクセル |
|--------------|--------|
| 100%         | 32     |
| 125%         | 40     |
| 150%         | 48     |
| 200%         | 64     |
| 400%         | 128    |

 

タイルの余白はシステムによって設定され、変更できません。 次の例で示すように、コンテンツのほとんどが余白の内側に表示されます。

![タイルの余白](images/assetguidance04.png)

余白の幅は、表示されているデバイスの倍率に基づいています。

| 倍率 | ピクセル |
|--------------|--------|
| 100%         | 8      |
| 125%         | 10     |
| 150%         | 12     |
| 200%         | 16     |
| 400%         | 32     |

 

## <a name="tile-assets"></a>タイル アセット


各タイル アセットは、配置されるタイルと同じサイズです。 アセットの 2 つの異なる表示によって、アプリのタイルをブランド化できます。

1. パディングによって中央に配置されたアイコンまたはロゴ。 この場合、バック プレートの色が透けて見えます。

![タイルとバック プレート](images/assetguidance05.png)

2. パディングのない、フルブリードのブランド化されたタイル。

![フルブリードを表示するタイル](images/assetguidance06.png)

デバイス間で一貫性を確保するために、各タイル サイズ (小、普通、ワイド、大) には独自のサイズの関係があります。 タイルの間で一貫したアイコンの配置を実現するために、以下のタイル サイズについて、パディングの基本的なガイドラインに従うことをお勧めします。 紫色の 2 つのオーバーレイが交差する領域が、アイコンの最適な面積を表しています。 アイコンがこの面積の内側に収まらない場合もありますが、アイコンの表示領域は用意されている例とほぼ同じである必要があります。

小さいタイルのサイズ調整:

![小さいタイルのサイズ調整の例](images/assetguidance07a.png)

普通サイズのタイルのサイズ調整:

![普通サイズのタイルのサイズ調整の例](images/assetguidance07b.png)

ワイド タイルのサイズ調整:

![ワイド タイルのサイズ調整の例](images/assetguidance07c.png)

大きいタイルのサイズ調整:

![大きいタイルのサイズ調整の例](images/assetguidance07d.png)

この例では、アイコンがタイルに対して大きすぎます。

![タイルに対して大きすぎるアイコン](images/assetguidance08a.png)

この例では、アイコンがタイルに対して小さすぎます。

![タイルに対して小さすぎるアイコン](images/assetguidance08b.png)

水平方向または垂直方向のアイコンに最適なパディングの比率は次のとおりです。

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

## <a name="tile-assets-in-list-views"></a>リスト ビューでのタイル アセット


タイルはリスト ビューにも表示されます。 リスト ビューに表示されるタイル アセットのサイズ調整に関するガイドラインは、先ほど説明したタイル アセットとは少し異なります。 このセクションでは、これらのサイズ調整の詳細について説明します。

![リスト ビューでのタイル アセット](images/assetguidance16.png)

アイコンの幅と高さをタイル サイズの 75% に制限します。

![リスト ビュー タイルのアイコンのサイズ調整](images/assetguidance17.png)

垂直方向および水平方向のアイコンでは、幅と高さをタイル サイズの 75% に制限します。

![リスト ビュー タイルのアイコンのサイズ調整](images/assetguidance18.png)

重要なブランド要素のフルブリード アートワークの場合、12.5% 以上の余白を維持します。

![リスト ビュー タイルでのフルブリード アートワーク](images/assetguidance19.png)

次の例では、アイコンがタイル内で大きすぎます。

![タイルに対して大きすぎるアイコン](images/assetguidance20a.png)

次の例では、アイコンがタイル内で小さすぎます。

![タイルに対して小さすぎるアイコン](images/assetguidance20b.png)

## <a name="target-based-assets"></a>ターゲット ベースのアセット


ターゲット ベースのアセットは、Windows タスク バー、タスク ビュー、スナップ アシスト、Alt + Tab キーを押したとき、およびスタート画面のタイルの右下に表示されるアイコンおよびタイルで使用されます。 これらのアセットにパディングを追加する必要はありません。パディングは、必要に応じて Windows によって追加されます。 これらのアセットは、16 ピクセルの最小面積を占めている必要があります。 Windows タスク バーのアイコンに表示される、このようなアセットの例を以下に示します。

![Windows タスク バーのアセット](images/assetguidance21.png)

これらの UI では、既定で色付きバック プレート上でターゲット ベースのアセットが使用されますが、ターゲット ベースのプレートなしのアセットを使用することもできます。 プレートなしのアセットは、さまざまな背景色で表示される可能性があることを考慮して作成する必要があります。

![プレートなしのアセットとプレート付きのアセット](images/assetguidance22.png)

100% の倍率でのターゲット ベースのアセットのサイズに関する推奨事項を次に示します。

![100% の倍率でのターゲット ベースのアセットのサイズ調整](images/assetguidance23.png)

## <a name="splash-screen-assets"></a>スプラッシュ画面のアセット


スプラッシュ画面の画像は、画像ファイルへの直接パスまたはリソースとして指定できます。 リソース参照を使用すると、Windows がデバイスと画面の解像度に最適なサイズを選択できるように、さまざまなスケールの画像を提供できます。 アクセシビリティのためのハイ コントラスト画像や、さまざまな UI 言語に対応するローカライズされた画像を提供することもできます。

テキスト エディターで "Package.appxmanifest" を開くと、[**VisualElements**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements) 要素の子として [**SplashScreen**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-splashscreen) 要素が表示されます。 マニフェスト ファイル内の既定のスプラッシュ画面のマークアップはテキスト エディターで次のようになります。

```XML
<uap:SplashScreen Image="Assets\SplashScreen.png" /></code></pre></td>
</tr>
</tbody>
</table>
```

スプラッシュ画面のアセットは、表示されるすべてのデバイスで中央に配置されます。

![スプラッシュ画面のアセットのサイズ調整](images/assetguidance27.png)

## <a name="high-contrast-assets"></a>ハイ コントラストのアセット


ハイ コントラスト モードでは、別のハイ コントラスト白 (白の背景に黒のテキスト) とハイ コントラスト黒 (黒の背景に白のテキスト) のアセットを使用します。 アプリでハイ コントラストのアセットが提供されない場合、標準アセットが使用されます。

アプリの標準アセットをモノクロの背景にレンダリングしたときに許容できる表示エクスペリエンスが提供される場合、アプリはハイ コントラスト モードでも最低限満足できる表示になります。 標準アセットをモノクロの背景にレンダリングしたときに、許容できる表示エクスペリエンスが得られない場合は、明確にハイ コントラストのアセットを含めることを検討します。 以下の例は、2 種類のハイ コントラストのアセットを示しています。

![ハイ コントラスト比のアセットの例](images/assetguidance28.png)

ハイ コントラストのアセットを用意する場合は、黒地に白と白地に黒の両方のセットを含める必要があります。 これらのアセットをパッケージに含める場合は、黒地に白のアセット用に "contrast-black" フォルダーを、白地に黒のアセット用に "contrast-white" フォルダーを作成できます。

## <a name="asset-size-tables"></a>アセット サイズの一覧表


少なくとも、100、200、400 の倍率のアセットを提供することを強くお勧めします。 すべての倍率のアセットを提供することによって、最適なユーザー エクスペリエンスを提供できます。

<br/>

<table>
<thead>
<tr><th colspan="3">小さいタイル (Square71x71Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">倍率 100%</td>
    <td width="20%">71 x 71</td>
    <td>Square71x71Logo.scale-100.png</td>
</tr>
<tr>
    <td>倍率 125%</td>
    <td>89 x 89</td>
    <td>Square71x71Logo.scale-125.png</td>
</tr>
<tr>
    <td>倍率 150%</td>
    <td>107 x 107</td>
    <td>Square71x71Logo.scale-150.png</td>
</tr>
<tr>
    <td>倍率 200%</td>
    <td>142 x 142</td>
    <td>Square71x71Logo.scale-200.png</td>
</tr>
<tr>
    <td>倍率 400%</td>
    <td>284 x 284</td>
    <td>Square71x71Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">普通サイズのタイル (Square150x150Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">倍率 100%</td>
    <td width="20%">150 x 150</td>
    <td>Square150x150Logo.scale-100.png</td>
</tr>
<tr>
    <td>倍率 125%</td>
    <td>188 x 188</td>
    <td>Square150x150Logo.scale-125.png</td>
</tr>
<tr>
    <td>倍率 150%</td>
    <td>225 x 225</td>
    <td>Square150x150Logo.scale-150.png</td>
</tr>
<tr>
    <td>倍率 200%</td>
    <td>300 x 300</td>
    <td>Square150x150Logo.scale-200.png</td>
</tr>
<tr>
    <td>倍率 400%</td>
    <td>600 x 600</td>
    <td>Square150x150Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">ワイド タイル (Wide310x150Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">倍率 100%</td>
    <td width="20%">310 x 150</td>
    <td>Wide310x150Logo.scale-100.png</td>
</tr>
<tr>
    <td>倍率 125%</td>
    <td>388 x 188</td>
    <td>Wide310x150Logo.scale-125.png</td>
</tr>
<tr>
    <td>倍率 150%</td>
    <td>465 x 225</td>
    <td>Wide310x150Logo.scale-150.png</td>
</tr>
<tr>
    <td>倍率 200%</td>
    <td>620 x 300</td>
    <td>Wide310x150Logo.scale-200.png</td>
</tr>
<tr>
    <td>倍率 400%</td>
    <td>1240 x 600</td>
    <td>Wide310x150Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">大きいタイル (Square310x310Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">倍率 100%</td>
    <td width="20%">310 x 310</td>
    <td>Square310x310Logo.scale-100.png</td>
</tr>
<tr>
    <td>倍率 125%</td>
    <td>388 x 388</td>
    <td>Square310x310Logo.scale-125.png</td>
</tr>
<tr>
    <td>倍率 150%</td>
    <td>465 x 465</td>
    <td>Square310x310Logo.scale-150.png</td>
</tr>
<tr>
    <td>倍率 200%</td>
    <td>620 x 620</td>
    <td>Square310x310Logo.scale-200.png</td>
</tr>
<tr>
    <td>倍率 400%</td>
    <td>1240 x 1240</td>
    <td>Square310x310Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">アプリの一覧のアイコン (Square44x44Logo)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">倍率 100%</td>
    <td width="20%">44 x 44</td>
    <td>Square44x44Logo.scale-100.png</td>
</tr>
<tr>
    <td>倍率 125%</td>
    <td>55 x 55</td>
    <td>Square44x44Logo.scale-125.png</td>
</tr>
<tr>
    <td>倍率 150%</td>
    <td>66 x 66</td>
    <td>Square44x44Logo.scale-150.png</td>
</tr>
<tr>
    <td>倍率 200%</td>
    <td>88 x 88</td>
    <td>Square44x44Logo.scale-200.png</td>
</tr>
<tr>
    <td>倍率 400%</td>
    <td>176 x 176</td>
    <td>Square44x44Logo.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>

<table>
<thead>
<tr><th colspan="3">スプラッシュ画面 (SplashScreen)</th></tr>
</thead>
<tbody>
<tr>
    <td width="20%">倍率 100%</td>
    <td width="20%">620 x 300</td>
    <td>SplashScreen.scale-100.png</td>
</tr>
<tr>
    <td>倍率 125%</td>
    <td>775 x 375</td>
    <td>SplashScreen.scale-125.png</td>
</tr>
<tr>
    <td>倍率 150%</td>
    <td>930 x 450</td>
    <td>SplashScreen.scale-150.png</td>
</tr>
<tr>
    <td>倍率 200%</td>
    <td>1240 x 600</td>
    <td>SplashScreen.scale-200.png</td>
</tr>
<tr>
    <td>倍率 400%</td>
    <td>2480 x 1200</td>
    <td>SplashScreen.scale-400.png</td>
</tr>
</tbody>
</table>

<br/>
 

**ターゲット ベースのアセット**

ターゲット ベースのアセットは、複数の倍率で使用されます。 ターゲット ベースのアセットの要素名は **Square44x44Logo** です。 最低でも以下のアセットを提出することを強くお勧めします。

16 x 16、24 x 24、32 x 32、48 x 48、256 x 256

次の表は、すべてのターゲット ベースのアセットのサイズと対応するファイル名の例を示します。

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

 

\* ベースラインとしてこれらのサイズのアセットを提出します

## <a name="asset-types"></a>アセットの種類


ここでは、すべてのアセットの種類、その用途、推奨されるファイル名の一覧を示します。

**タイル アセット**

-   中央に配置されるアセットは、通常、スタート画面にアプリを表示するために使用されます。
-   ファイル名の形式: [Square\Wide]\*x\*Logo.scale-\*.png
-   影響を受けるアプリ: すべての UWP アプリ
-   用途:
    -   既定のスタート画面のタイル (デスクトップとモバイル)
    -   アクション センター (デスクトップとモバイル)
    -   タスク スイッチャー (モバイル)
    -   共有ピッカー (モバイル)
    -   ピッカー (モバイル)
    -   ストア

**プレート付きのスケーラブルな一覧のアセット**

-   これらのアセットは拡大縮小が必要なサーフェスで使われます。 アセットのバック プレートはシステムによって提供されるか、アプリに含まれている場合は独自の背景色のプレートが使用されます。
-   ファイル名の形式: Square44x44Logo.scale-\*.png
-   影響を受けるアプリ: すべての UWP アプリ
-   用途:
    -   スタート画面のすべてのアプリの一覧 (デスクトップ)
    -   スタート画面のよく使うアプリの一覧 (デスクトップ)
    -   タスク マネージャー (デスクトップ)
    -   Cortana の検索結果
    -   スタート画面のすべてのアプリの一覧 (モバイル)
    -   設定

**プレート付きのターゲット サイズの一覧のアセット**

-   これらはプレート付きで、拡大縮小されない固定サイズのアセットです。 ほとんどの場合、従来のエクスペリエンスに使用されます。 アセットはシステムによって確認されます。
-   ファイル名の形式: Square44x44Logo.targetsize-\*.png
-   影響を受けるアプリ: すべての UWP アプリ
-   用途:
    -   スタート画面のジャンプ リスト (デスクトップ)
    -   スタート画面のタイルの下隅 (デスクトップ)
    -   ショートカット (デスクトップ)
    -   コントロール パネル (デスクトップ)

**プレートなしのターゲット サイズの一覧のアセット**

-   これらは、システムによってプレートの追加や拡大縮小が行われないアセットです。
-   ファイル名の形式: Square44x44Logo.targetsize-\*\_altform-unplated.png
-   影響を受けるアプリ: すべての UWP アプリ
-   用途:
    -   タスク バーとタスク バー サムネイル (デスクトップ)
    -   タスク バーのジャンプ リスト
    -   タスク ビュー
    -   Alt + Tab キー

**ファイル拡張子アセット**

-   これらはファイル拡張子に固有のアセットです。 エクスプ ローラーで Win32 スタイルのファイルの関連付けアイコンの横に表示され、テーマに依存しません。 サイズ調整は、デスクトップ プラットフォームとモバイル プラットフォームで異なります。
-   ファイル名の形式: \*LogoExtensions.targetsize-\*.png
-   影響を受けるアプリ: ミュージック、ビデオ、フォト、Microsoft Edge、Microsoft Office
-   用途:
    -   エクスプローラー
    -   Cortana
    -   さまざまな UI サーフェス (デスクトップ)

**スプラッシュ画面**

-   アプリのスプラッシュ画面に表示されるアセット。 デスクトップとモバイルの両方のプラットフォームで自動的に拡大縮小されます。
-   ファイル名の形式: SplashScreen.scale-*.png
-   影響を受けるアプリ: すべての UWP アプリ
-   用途:
    -   アプリのスプラッシュ画面