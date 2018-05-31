---
title: 光源
description: 光源は、シーン内のオブジェクトを照射するのに使われます。 各オブジェクト頂点の色は、現在のテクスチャ マップ、頂点の色、光源に基づきます。
ms.assetid: AB16CF5B-47CE-455C-A8BD-36305E54BEA9
keywords:
- 光源
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: e2750de79dbdb01081aa099ff955fcef2999dcbf
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
ms.locfileid: "1652498"
---
# <a name="lighting"></a>光源


光源は、シーン内のオブジェクトを照射するのに使われます。 各オブジェクト頂点の色は、現在のテクスチャ マップ、頂点の色、光源に基づきます。

**注**   このセクションは、固定関数パイプラインにのみ当てはまります。 プログラム可能なシェーダーは、すべての光源を明示的に実行します。

 

## <a name="span-idin-this-sectionspanin-this-section"></a><span id="in-this-section"></span>このセクションの内容


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">トピック</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="lighting-overview.md">光源の概要</a></p></td>
<td align="left"><p>Direct3D の光源を使うときは、Direct3D が照明のディテールを自動的に処理できるようにします。 詳しい知識のあるユーザーは、必要に応じて自分で光源を実行することもできます。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="light-types.md">光源の種類</a></p></td>
<td align="left"><p>光源の種類プロパティは、使う光源の種類を定義します。 Direct3D には 3 種類の光源 (ポイント ライト、スポットライト、指向性ライト) があります。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="light-properties.md">光源のプロパティ</a></p></td>
<td align="left"><p>光源のプロパティは、光源の種類 (ポイント、指向性、スポットライト)、減衰、色、方向、位置、範囲を表します。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="mathematics-of-lighting.md">光源の計算</a></p></td>
<td align="left"><p>Direct3D の照明モデルは、環境光、拡散光、反射光、放射光を扱います。 これにより、さまざまな照明の状況に十分対応することができます。 シーン内の照明の合計量は、<em>全体照明</em>と呼ばれます。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>関連トピック


[Direct3D グラフィックスの学習ガイド](index.md)

 

 



