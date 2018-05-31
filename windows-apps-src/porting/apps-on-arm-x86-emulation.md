---
title: ARM での x86 および ARM32 エミュレーションのしくみ
author: msatranjr
description: ARM での x86 アプリのエミュレーションの概要。
ms.author: misatran
ms.date: 02/15/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10 s, 常時接続, ARM での x86 エミュレーション
ms.localizationpriority: medium
ms.openlocfilehash: d8304bb49b1eeeea8b0aa17f7548197a360cbcf8
ms.sourcegitcommit: 11edca90aaf7856c762e68903483079d30ad3877
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
ms.locfileid: "1595159"
---
# <a name="how-x86-emulation-works-on-arm"></a>ARM での x86 エミュレーション
x86 アプリのエミュレーションにより、Win32 アプリのリッチなエコシステムが ARM で利用できるようになります。 これにより、アプリに変更を加えなくても、ユーザーが既存の x86 win32 アプリを問題なく実行できるようになります。 アプリは、固有の API ([IsWoW64Process2](https://msdn.microsoft.com/en-us/library/windows/desktop/mt804318.aspx)) を呼び出すことを除いて、ARM PC の Windows で実行されていることを認識することもありません。

Windows 10 の [WOW64](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384249(v=vs.85).aspx) レイヤーを使うと、ARM64 バージョンの Windows 10 で x86 コードを実行できます。 x86 エミュレーションは、パフォーマンスを高める最適化によって x86 命令のブロックを ARM64 命令にコンパイルすることで機能します。 サービスは、変換されたこれらのコード ブロックをキャッシュして命令変換のオーバーヘッドを減らし、コードをもう一度実行するときの最適化を実現します。 キャッシュはモジュールごとに生成されるため、他のアプリが初回起動時にそれらを使うことができます。 

これらのテクノロジについて詳しくは、[ARM 版 Windows 10](https://channel9.msdn.com/Events/Build/2017/P4171) Channel9 ビデオをご覧ください。 