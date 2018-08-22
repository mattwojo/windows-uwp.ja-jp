---
author: mcleblanc
ms.assetid: 83b4be37-6613-4d00-a48a-0451a24a30fb
title: データ バインディング
description: データ バインディングは、アプリの UI でデータを表示し、必要に応じてそのデータとの同期を保つ方法です。
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 9af7c4a3bf5cfacf8fcdddc276c4cff127ae9ea8
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.locfileid: "243038"
---
# <a name="data-binding"></a>データ バインディング

\[Windows 10 の UWP アプリ向けに更新。 Windows 8.x の記事については、[アーカイブ](http://go.microsoft.com/fwlink/p/?linkid=619132)をご覧ください。\]

データ バインディングは、アプリの UI でデータを表示し、必要に応じてそのデータとの同期を保つ方法です。 データ バインディングによって、UI の問題からデータの問題を切り離すことができるため、概念的なモデルが簡素化されると共に、アプリの読みやすさ、テストの容易性、保守容易性が向上します。 マークアップでは、[{{x:Bind}} マークアップ拡張](https://msdn.microsoft.com/library/windows/apps/Mt204783)と [{{Binding}} マークアップ拡張](https://msdn.microsoft.com/library/windows/apps/Mt204782)のいずれを使うかを選ぶことができます。 また、同じアプリや同じ UI 要素で、この 2 つを組み合わせて使うこともできます。 {x:Bind} は Windows 10 の新機能で、パフォーマンスが向上しています。

| トピック | 説明 |
|-------|-------------|
| [データ バインディングの概要](data-binding-quickstart.md) | このトピックでは、ユニバーサル Windows プラットフォーム (UWP) アプリで、コントロール (または他の UI 要素) を単一の項目にバインドする方法や、項目コントロールを項目のコレクションにバインドする方法を説明します。 また、項目のレンダリングを制御する方法、選択内容に基づいて詳細ビューを実装する方法、表示するデータを変換する方法も紹介します。 詳しくは、「[データ バインディングの詳細](data-binding-in-depth.md)」をご覧ください。 | 
| [データ バインディングの詳細](data-binding-in-depth.md) | このトピックでは、データ バインディングの機能について詳しく説明します。 |
| [デザイン サーフェイス上のサンプル データとプロトタイプを作るためのサンプル データ](displaying-data-in-the-designer.md) | (アプリのレイアウト、テンプレート、その他の視覚的なプロパティを操作するため) Visual Studio デザイナーでコントロールにデータを設定できるように、さまざまな方法で設計時のサンプル データを使うことができます。 サンプル データは、スケッチ (プロトタイプ) アプリを開発する場合にも便利で、時間の節約になります。 スケッチやプロトタイプで実行時にサンプル データを使うと、実際のライブ データに接続しなくてもアイデアを実証できます。 |
| [階層データをバインドしてマスター/詳細ビューを作る方法](how-to-bind-to-hierarchical-data-and-create-a-master-details-view.md) | チェーン内でバインドされた [<strong>CollectionViewSource</strong>](https://msdn.microsoft.com/library/windows/apps/BR209833) インスタンスに項目コントロールをバインドすることによって、階層データの複数レベルのマスター/詳細 (リスト/詳細とも呼ばれる) ビューを作成することができます。 |
