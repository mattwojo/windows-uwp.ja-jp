---
title: リソースの選択
description: アプリケーションの3D グラフィックスパイプラインのさまざまなステージにバインドするために最適なリソースを特定して選択する方法について説明します。
ms.assetid: 6BAD6287-2930-42F8-BF51-69A379D1D2C3
keywords:
- リソースの選択
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 69527915988136854e201b82332c17f3e0134290
ms.sourcegitcommit: 45dec3dc0f14934b8ecf1ee276070b553f48074d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2020
ms.locfileid: "89094470"
---
# <a name="choosing-a-resource"></a>リソースの選択


リソースは、3D パイプラインで使用されるデータのコレクションです。 リソースを作成してその動作を定義することが、アプリケーションをプログラミングするための第一歩になります。 このガイドでは、アプリケーションで必要なリソースの選択に関する基本的なトピックについて説明します。

## <a name="span-ididentify_bindingspanspan-ididentify_bindingspanspan-ididentify_bindingspanidentify-pipeline-stages-that-need-resources"></a><span id="Identify_Binding"></span><span id="identify_binding"></span><span id="IDENTIFY_BINDING"></span>リソースが必要なパイプラインステージの特定


最初の手順は、リソースを使用する[グラフィックス パイプライン](graphics-pipeline.md)のステージの選択です。 このとき、リソースからデータを読み込むステージだけでなく、リソースにデータを書き込むステージも特定します。 リソースを使用するパイプラインのステージを把握できれば、リソースをステージにバインドするために呼び出す API を決定できます。

次の表は、各パイプラインのステージにバインドすることのできるリソースの種類を示しています。 リソースを入力または出力としてバインドできるかどうかを示しています。

| パイプラインのステージ  | /アウトの選択 | リソース               | リソースの種類                           |
|-----------------|--------|------------------------|-----------------------------------------|
| 入力アセンブラー | /     | 頂点バッファー          | バッファー                                  |
| 入力アセンブラー | /     | インデックス バッファー           | バッファー                                  |
| シェーダー ステージ   | /     | シェーダー リソース ビュー    | バッファー、Texture1D、Texture2D、Texture3D |
| シェーダー ステージ   | /     | シェーダー定数バッファー | バッファー                                  |
| ストリーム出力   | アウト    | バッファー                 | バッファー                                  |
| 出力結合   | アウト    | レンダー ターゲット ビュー     | バッファー、Texture1D、Texture2D、Texture3D |
| 出力結合   | アウト    | 深度/ステンシル ビュー     | Texture1D、Texture2D                    |

 

## <a name="span-ididentify_usagespanspan-ididentify_usagespanspan-ididentify_usagespanidentify-how-each-resource-will-be-used"></a><span id="Identify_Usage"></span><span id="identify_usage"></span><span id="IDENTIFY_USAGE"></span>各リソースの使用方法の特定


アプリケーションが使用するパイプラインのステージ (および各ステージが必要とするリソース) を選択したら、各リソースの使用方法つまりリソースを CPU または GPU からアクセス可能にするかどうかを決定します。

アプリケーションを実行するハードウェアには、最低でも CPU と GPU が 1 つずつあります。 使用方法の値を選ぶ際には、リソースの読み取りまたは書き込みに必要なプロセッサの種類が次の選択肢のいずれになるかを検討します。

| Resource Usage | 更新の実行                    | 更新頻度 |
|----------------|--------------------------------------|---------------------|
| Default        | GPU                                  | 低頻度        |
| 動的        | CPU                                  | 高頻度          |
| ステージング        | GPU                                  | 該当なし                 |
| 変更不可      | CPU (リソースの作成時のみ) | 該当なし                 |

 

CPU によるリソースの更新が低頻度 (フレームごとに 1 回未満) であると予想される場合は、既定の使用方法を選択します。 パフォーマンス低下を避けるため、既定の使用方法では CPU からリソースに直接書き込まないことが理想的です。

CPU によるリソースの更新が比較的高頻度 (フレームごとに 1 回以上) である場合は、動的の使用方法を選択します。 動的リソースの一般的なシナリオは、動的な頂点バッファーとインデックス バッファーを作成し、ユーザーの視点から見えるジオメトリのデータを使用して、実行時にフレームごとに描画することです。 これらのバッファーは、各フレームでユーザーから見えるジオメトリのみをレンダリングするために使用されます。

ステージングの使用方法は、他のリソースとの間のコピーに使用します。 一般的なシナリオは、既定の使用方法おける (CPU がアクセスできない) リソースのデータをステージングの使用方法における (CPU がアクセス可能な) リソースにコピーすることです。

固定のリソースは、リソース内のデータが決して変更されない場合に使用します。

この問題を別の視点から見ると、アプリケーションがリソースにどのような処理を実行するか考えることになります。

| アプリケーションによるリソースの使用方法     | Resource Usage       |
|---------------------------------------|----------------------|
| 1 度だけロードし更新しない            | 固定または既定 |
| アプリケーションが頻繁にリソースに格納する | 動的              |
| テクスチャへのレンダリング                     | Default              |
| GPU データの CPU アクセス                | ステージング              |

 

どの使用法を選択すべきかよくわからない場合は、一般的なほとんどのケースに対応可能な既定の使用方法から始めてください。 シェーダー定数バッファーは、常に既定の使用方法にする必要のあるリソース タイプの 1 つです。

## <a name="span-idresource_types_and_pipeline_stagesspanspan-idresource_types_and_pipeline_stagesspanspan-idresource_types_and_pipeline_stagesspanbinding-resources-to-pipeline-stages"></a><span id="Resource_Types_and_Pipeline_stages"></span><span id="resource_types_and_pipeline_stages"></span><span id="RESOURCE_TYPES_AND_PIPELINE_STAGES"></span>パイプラインステージへのリソースのバインド


リソースは、作成時に指定された制限を満たす限り、同時に複数のパイプラインのステージにバインドすることができます。 これらの制限は、利用フラグ、バインド フラグ、CPU アクセス フラグとして指定されます。 具体的には、リソースの読み取り部分と書き込み部分の同時発生がない場合には、リソースを入力と出力に同時にバインドすることができます。

リソースをバインドするときは、CPU と GPU がリソースにどのようにアクセスするかを考えます。 多くの場合、単一の用途に設計された (複数の利用フラグ、バインド フラグ、および CPU アクセス フラグを持たない) リソースの方がより高いパフォーマンスを得られます。

たとえば、テクスチャとして複数回使用されるレンダー ターゲットを考えてください。 この場合、リソースを 2 つにする方が速くなる可能性があります (1 つのシェーダー リソースとしてレンダー ターゲットとテクスチャを使用)。 各リソースは、バインド フラグを 1 つだけ使用して、「レンダー ターゲット」または「シェーダー リソース」を示します。 データはレンダー ターゲット テクスチャからシェーダー テクスチャにコピーされます。

この例のように、シェーダー テクスチャの読み取りとレンダー ターゲットの書き込みを分離することで、パフォーマンスが向上する場合があります。 実際にどうなるかを確かめるには、アプリケーションに両方の方法を実装して、パフォーマンスの違いを測定する必要があります。

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>関連トピック


[リソース](resources.md)

 

 




