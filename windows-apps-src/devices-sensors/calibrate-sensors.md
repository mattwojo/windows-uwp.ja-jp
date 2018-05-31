---
author: muhsinking
ms.assetid: ECE848C2-33DE-46B0-BAE7-647DB62779BB
title: センサーの調整
description: デバイスの磁力計 (コンパス、傾斜計、方位センサー) に基づくセンサーは、環境の要因に応じて調整が必要になることがあります。
ms.author: jken
ms.date: 03/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c02a6ec88bcce2e81637184270b5910af15430de
ms.sourcegitcommit: cceaf2206ec53a3e9155f97f44e4795a7b6a1d78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
ms.locfileid: "1700548"
---
# <a name="calibrate-sensors"></a>センサーの調整


**重要な API**

-   [**Windows.Devices.Sensors**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**Windows.Devices.Sensors.Custom**](https://msdn.microsoft.com/library/windows/apps/Dn895032)

デバイスの磁力計 (コンパス、傾斜計、方位センサー) に基づくセンサーは、環境の要因に応じて調整が必要になることがあります。 [**MagnetometerAccuracy**](https://msdn.microsoft.com/library/windows/apps/Dn297552) 列挙値は、デバイスの調整が必要になる場合の対応策を決めるのに役立ちます。

## <a name="when-to-calibrate-the-magnetometer"></a>磁力計を調整するタイミング

[**MagnetometerAccuracy**](https://msdn.microsoft.com/library/windows/apps/Dn297552) 列挙値には、アプリが実行されているデバイスを調整する必要があるかどうかを判断するのに役立つ 4 つの値があります。 デバイスを調整する必要がある場合は、その旨をユーザーに知らせる必要があります。 ただし、あまりに頻繁に調整を行うようユーザーに促さないでください。 10 分に 1 回の間隔をお勧めします。

| 値           | 説明    |
| ----------------- | ------------------- |
| **Unknown**     | センサー ドライバーは現在の正確さを報告できませんでした。 これは、必ずしもデバイスが調整されていないことを意味するわけではありません。 **Unknown** が返された場合の最適な対応策は、開発しているアプリによって決まります。 アプリがセンサーの正確な読み取り値に依存している場合は、デバイスの調整をユーザーに促すことをお勧めします。 |
| **Unreliable**  | 現在、磁力計の正確さが大きく劣っています。 この値が最初に返された場合、アプリでは、必ずユーザーに調整を促す必要があります。 |
| **Approximate** | 特定のアプリに対してデータは十分に正確です。 ユーザーがデバイスを上下または左右に動かしたかどうかがわかればよいだけの仮想現実アプリでは、調整なしで続行できます。 指示を出すためにどの方向に進んでいるか知る必要があるナビゲーション アプリのように、絶対的な進路を必要とするアプリでは、調整を促す必要があります。 |
| **High**        | データは正確です。 拡張現実アプリ、ナビゲーション アプリなどの絶対的な進路を知る必要があるアプリでも、調整は必要ありません。 |