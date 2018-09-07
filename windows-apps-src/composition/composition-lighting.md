---
author: daneuber
title: コンポジションの照明
description: アプリに 3D の動的な照明を追加する、コンポジションの照明 Api を使用できます。
ms.author: jimwalk
ms.date: 07/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: e634b18fffc4f601f6512d6ceeed51efbe9c1886
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "3661015"
---
# <a name="using-lights-in-windows-ui"></a>Windows UI でのライトの使用

Windows.UI.Composition Api には、リアルタイムのアニメーションや効果を作成することが有効にします。 コンポジションの照明は、2 D のアプリケーションで 3D の照明を使用できます。 この概要では、コンポジションの照明をセットアップし、各のライトを受信する視覚効果を識別および、効果を使用して、コンテンツの素材を定義する方法の機能を実行します。

> [!NOTE]
> [XamlLight](/uwp/api/windows.ui.xaml.media.xamllight)オブジェクトを XAML Uielement を照射する[して Compositionlight](/uwp/api/Windows.UI.Composition.CompositionLight)を適用する方法を読み取り、 [XAML の照明](xaml-lighting.md)を参照してください。

コンポジションの照明を使用することを許可する UI を興味深いを作成することができます。

- 音楽再生シーンなどのイマーシブのシナリオを実現するシーン内の他のオブジェクトのライトに依存しないの変換します。
- 一緒に移動できるように、ライトを使ってオブジェクトをペアリングする機能を Fluent[表示](/design/style/reveal.md)ハイライトなどのシナリオを有効にするシーンの残りの部分の独立しました。
- 素材と深度を作成するグループとして光とシーン全体の変換します。

コンポジションの照明は次の 3 つの主要な概念をサポートしています。**光**、**ターゲット**、および**SceneLightingEffect**します。

## <a name="light"></a>Light

[CompositionLight](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlight)を使用すると、さまざまなライトを作成し、座標空間に配置できます。 これらのライトがライトによって照らさとしてを識別する視覚効果をターゲットします。

### <a name="light-types"></a>光源の種類

| 種類 | 説明 |
| --- | --- |
| [AmbientLight](/uwp/api/windows.ui.composition.ambientlight) | シーン内のすべてに表示される非方向領光を照射する光源が反映されます。 |
| [DistantLight](/uwp/api/windows.ui.composition.distantlight) | 無限に大規模な離れた場所にある光源を 1 つの方向に光を照射します。 (太陽など)。 |
| [PointLight](/uwp/api/windows.ui.composition.pointlight) | すべての方向に光を放射光のポイントのソース。 電球など。 |
| [スポットライト](/uwp/api/windows.ui.composition.spotlight) | 内部コーンおよび外部コーンの光を照射する光源を使用します。 など、しない懐中電灯します。 |

## <a name="targets"></a>ターゲット

ライトがビジュアルをターゲットと ([ターゲット](/uwp/api/windows.ui.composition.compositionlight.targets)の一覧に追加)、ビジュアル オブジェクトとすべてのサブフォルダーはの認識し、この光源に応答します。 単純なものツリーと下にあるすべての視覚効果のルートに PointLight ソースの対応、ポイント ライトの方向のアニメーションを設定できます。

**ExclusionsFromTargets**には、ターゲットを追加する場合と同様の方法でビジュアルのまたは視覚効果のサブツリー内の照明を削除することができます。 除外されるビジュアルをルート ツリー内の子がその結果点灯していません。

### <a name="sample-targets"></a>(ターゲット) のサンプル

次のサンプルでは、XAML の TextBlock を対象に、CompositionPointLight を使用します。

```cs
    _pointLight = _compositor.CreatePointLight();
    _pointLight.Color = Colors.White;
    _pointLight.CoordinateSpace = text; //set up co-ordinate space for offset
    _pointLight.Targets.Add(text); //target XAML TextBlock
```

ポイント ライトのオフセットをアニメーションを追加することで光る効果は簡単に実現されます。

```cs
_pointLight.Offset = new Vector3(-(float)TextBlock.ActualWidth, (float)TextBlock.ActualHeight / 2, (float)TextBlock.FontSize);
```

詳細については WindowUIDevLabs サンプル ゲラビューで[テキストちらついて](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2014393/TextShimmer)の完全なサンプルを参照してください。

## <a name="restrictions"></a>制限

CompositionLight によって照らさ コンテンツを決定する際に考慮するいくつかの要因があります。

概念 | 詳細
--- | ---
**環境光** | 以外環境光をシーンに追加すると、既存のすべての光を有効になります。  非環境光が対象としないアイテムは黒く表示されます。  自然な方法でライトによって発信周囲の視覚効果を照射するには、他のライトと組み合わせて、環境光を使用します。
**ライトの数** | 任意の組み合わせで、2 つの非アンビエント コンポジション ライトを使用すると、UI をターゲットにすること。 アンビエント照明ではありません。スポット、点、および遠くライトです。
**有効期間** | CompositionLight 有効期間の条件が発生する可能性があります (例: が使用する前に、ガーベジ コレクターはライト オブジェクトをリサイクル可能性があります)。  アプリケーションの有効期間を管理できるようにするにはメンバーとして照明を追加することで、ライトへの参照を保持することをお勧めします。
**変換** | ライトは、ノード上では、[視点の変換](/design/layout/3-d-perspective-effects.md)と同様に、効果、視覚的構造を適切に描画する UI に配置する必要があります。
**ターゲットと座標空間** | CoordinateSpace は、ビジュアルの領域のすべてのライトのプロパティを設定する必要があります。 CompositionLight.Targets は CoordinateSpace ツリー内である必要があります。

## <a name="lighting-properties"></a>光源のプロパティ

、使用される光源の種類に応じて、光の減衰と空間プロパティことができます。 すべての種類の光源がすべてのプロパティを使うわけではありません。

プロパティ | 説明
--- | ---
**Color** | 光の[色](/uwp/api/windows.ui.color)。 照明の適用色の値は、 [D3D](https://docs.microsoft.com/windows/uwp/graphics-concepts/light-properties)拡散、環境、放射される色を定義するスペキュラによって定義されます。 照明は、ライトの RGBA 値を使用します。アルファ色コンポーネントは使われません。
**Direction** | 光の方向です。 その[CoordinateSpace](/uwp/api/windows.ui.composition.distantlight.coordinatespace) Visual を基準とした、光をポイントする方向が指定されます。
**座標空間** | すべての Visual では、暗黙的な 3D の座標空間があります。 X 方向は、左から右です。 Y 方向は、上から下です。 Z 方向は、平面外ポイントです。 この座標の元のポイントは、ビジュアルの左上隅と、単位は、デバイス依存しないピクセル (DIP)。 この座標で定義されている光のオフセットです。
**内部および外部コーン** | スポットライトは、明るい内部コーンと外部コーンの 2 つの部分を持つ光のコーンを放射します。 コンポジションでは、内部および外部コーン角度と色を制御できます。
**Offset** | その座標空間 Visual を基準とした、光源のオフセットです。

> [!NOTE]
> 複数の照明ヒット同じ視覚、または光の色の値が 1.0 を超過するのに十分な大きさに取得されるたびに、ライトの色チャネルのクランプがあるため、光の色が変更できます。

### <a name="advanced-lighting-properties"></a>高度なライティング プロパティ

プロパティ | 説明
--- | ---
**強さ** | 光の明るさを制御します。
**減衰** | 減衰は、範囲プロパティによって指定された最大距離にいたるまでに光の強さがどのように弱くなっていくかを制御します。  定数、Quadradic と線形減衰プロパティことができます。

## <a name="getting-started-with-lighting"></a>照明の概要

照明を追加する一般的な手順に従います。

- 作成し、ライトを配置します。 ライトを作成すると、指定された座標空間に配置します。
- ライトへのオブジェクトを識別する: 関連する視覚効果に光をターゲットにします。
- (省略可能)個々 のオブジェクトを定義ライトへの対応: 光が反射 SpriteVisual を表示するためのカスタマイズ、EffectBrush で使うのために SceneLightingEffect します。 反射の既定値は、光源の CoordinateSpace の子の照明をサポートします。  描画するために SceneLightingEffect と共に visual は、そのビジュアルの既定の照明を上書きします。

## <a name="scenelightingeffect"></a>SceneLightingEffect

[SpriteVisual](/uwp/api/Windows.UI.Composition.SpriteVisual) [CompositionLight](/uwp/api/windows.ui.composition.compositionlight)によってターゲットの内容に適用される既定の照明を変更する[ために SceneLightingEffect](/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect)表示されます。

[SceneLightingEffect](/uwp/api/Windows.UI.Composition.Effects.SceneLightingEffect)は、素材の作成によく使用されます。 ために SceneLightingEffect とは、画像のプロパティを反映したものを有効にするや、法線マップ、奥行き感を提供するようより複雑なものを実現するために必要なときに使用する効果です。 ために SceneLightingEffect 反射および拡散の量などの照明のプロパティを使用して、UI をカスタマイズする機能を提供します。 個別にブレンドし、コンテンツのさまざまな照明反応できる効果パイプラインの残りの部分で照明効果をカスタマイズすることができます。

> [!NOTE]
> シーンの照明はシャドウを生成しません。2D レンダリングに重点を置いて効果です。  実際の照明モデルでは、シャドウをなどが含まれるの配慮の一 3D 照明シナリオには実行されません。


プロパティ | 説明
--- | ---
**通常のマップ** | NormalMaps では、位置、光の方向に通常のポイントは明るくなりますができ、法線を指している離れた調光のテクスチャの効果を作成します。 対象となる visual の NormalMap を追加するには、 [CompositionSurfaceBrush](/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) LoadedImageSurface を使って読み込む NormalMap アセットを使用します。
**環境光** | 環境光のプロパティは、全体的な色のリフレクションを制御するほとんど使用されます。
**反射** | 反射光では、オブジェクト、光沢のある表示したりすることにハイライトを作成します。 反射光のレベルと輝きのレベルを制御することができます。  これらのプロパティは、光沢金属または光沢のあるホワイト ペーパーなどのマテリアルの効果を作成する操作されます。
**拡散** | 拡散されたリフレクションでは、すべての方向に光を拡散します。
**反射率モデル** | [反射率モデル](/uwp/api/windows.ui.composition.effects.scenelightingeffectreflectancemodel)では、 [Blinn フォン](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-phong-shader)と Blinn フォンを物理的に基づくを選択することができます。  反射光が縮小する場合は、Blinn フォンを物理的に基づくを選択します。

### <a name="sample-scenelightingeffect"></a>サンプル (SceneLightingEffect)

次のサンプルでは、通常のマップするために SceneLightingEffect を追加する方法を示します。

```cs
CompositionBrush CreateNormalMapBrush(ICompositionSurface normalMapImage)
{
    var colorSourceEffect = new ColorSourceEffect()
    {
        Color = Colors.White
    };
    var sceneLightingEffect = new SceneLightingEffect()
    {
        NormalMapSource = new CompositionEffectSourceParameter("NormalMap")
    };

    var compositeEffect = new ArithmeticCompositeEffect()
    {
        Source1 = colorSourceEffect,
        Source2 = sceneLightingEffect,
    };

    var factory = _compositor.CreateEffectFactory(sceneLightingEffect);

    var normalMapBrush = _compositor.CreateSurfaceBrush();
    normalMapBrush.Surface = normalMapImage;
    normalMapBrush.Stretch = CompositionStretch.Fill;

    var brush = factory.CreateBrush();
    brush.SetSourceParameter("NormalMap", normalMapBrush);

    return brush;
}
```

## <a name="related-articles"></a>関連記事

- [ビジュアル レイヤーの素材とライトを作成します。](https://blogs.windows.com/buildingapps/2017/08/04/creating-materials-lights-visual-layer/)
- [光源の概要](https://docs.microsoft.com/windows/uwp/graphics-concepts/lighting-overview)
- [CompositionCapabilities API](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositioncapabilities)
- [光源の計算](https://docs.microsoft.com/windows/uwp/graphics-concepts/mathematics-of-lighting)
- [SceneLightingEffect](https://docs.microsoft.com/uwp/api/windows.ui.composition.effects.scenelightingeffect)
- [WindowsUIDevLabs GitHub リポジトリ](https://github.com/Microsoft/WindowsUIDevLabs)