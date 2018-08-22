---
author: mcleanbyron
Description: You can use the Windows Dev Center dashboard to run experiments for your Universal Windows Platform (UWP) apps with A/B testing.
title: A/B テストを使用してアプリの実験を実行する
ms.assetid: 790B4B37-C72D-4CEA-97AF-D226B2216DCC
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Microsoft Store Services SDK, A/B テスト, 実験
ms.localizationpriority: medium
ms.openlocfilehash: a4d7ef0fe9297f8e3affc908a9ba74de8bb29f3a
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "2788777"
---
# <a name="run-app-experiments-with-ab-testing"></a>A/B テストを使用してアプリの実験を実行する

Windows デベロッパー センター ダッシュ ボードを使用して、ユニバーサル Windows プラットフォーム (UWP) アプリから実行時に取得できるリモート変数を定義できます。また、それらの値のバリエーションをユーザーに対してテストし、望ましいユーザー動作を導くための最も効果的な値を識別することができます。 アプリでリモート変数を使用することで、アプリ内購入、サインアップ フロー、キャプション、広告配信などのアプリ エクスペリエンスを構成できます。

A/B テストの目標は、より魅力的なアプリ エクスペリエンスを提供することによってコンバージョン率を改善 (アプリ内購入が増えるなど) できる可能性が高いリモート変数値のバリエーションを特定することです。 有望なバリエーションを識別したら、アプリを再公開しなくても、すぐに実験を終了してデベロッパー センター ダッシュボードからユーザー全体にそのバリエーションを有効にすることができます。

## <a name="create-and-run-an-ab-test"></a>A/B テストを作成および実行する

A/B テストを作成および実行するには、次の手順に従います。

1. [プロジェクトを作成し、デベロッパー センター ダッシュボードでリモート変数を定義します](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)。 このプロジェクトには、実験の変数と、既定の変数値が含まれています。  
2. [アプリの実験用のコードを記述します](code-your-experiment-in-your-app.md)。 Microsoft Store Services SDK にある API を使用して、ダッシュボードで作成したプロジェクトからリモート変数値を取得します。次にこのデータを使用して、テストしている機能の動作を変更します。そしてビュー イベントおよびコンバージョン イベントをデベロッパー センターへ送信します。
3. [デベロッパー センター ダッシュボードで実験を定義します](define-your-experiment-in-the-dev-center-dashboard.md)。 A/B テストの固有の目標とバリエーションを定義する実験を、プロジェクト内に作成します。
4. [デベロッパー センター ダッシュボードで実験を実行および管理します](manage-your-experiment.md)。 実験をアクティブ化し、ダッシュボードを使用して実験結果を確認し、実験を完了します。

エンド ツー エンドのプロセスを示すチュートリアルについては、「[A/B テストを使用して最初の実験を作成および実行する](create-and-run-your-first-experiment-with-a-b-testing.md)」をご覧ください。

## <a name="requirements"></a>必要条件

Windows デベロッパー センターの A/B テストは、UWP アプリのみでサポートされています。

A/B テストを実行する前に、開発用コンピューターを設定する必要があります。

* [ここ](../get-started/get-set-up.md)で説明する指示に従って、UWP 開発のための開発用コンピューターを設定します。
* [Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) をインストールします。 実験用の API に加えて、この SDK は広告を表示したり、アプリのフィードバックを収集するフィードバック Hub にユーザーを誘導するなど、その他の機能のための API も提供します。

## <a name="best-practices"></a>ベスト プラクティス

最も有用な結果を得るには、A/B テストを実行しているときに、次の推奨事項に従うことをお勧めします。

* バリエーションの割り当て用に、ランダム化された 50/50 分割の配布による 2 つのみのバリエーションで実験を実行することを検討してください。
* 統計的に重要でアクション可能なデータを十分収集するために、少なくとも 2 ～ 4 週間はテストを実行します。

<span id="terms" />

## <a name="related-terms"></a>関連用語

|  用語  |  説明  |
|--------|--------------|
| プロジェクト    |   Microsoft Store Services SDK を使ってアプリからアクセスできる、既定値を持ったリモート変数のコレクションです。 プロジェクトには、同じリモート変数を共有する 1 つ以上の実験を含めることもできます。  |
| 実験    |   A/B テストを定義する一連のパラメーターです。これらはユーザーによって受信されます。 実験はプロジェクトの範囲内で定義されます。各実験は次の要素で構成されます。 <p></p><ul><li>実験の一部であるバリエーションをユーザーが最初に表示するタイミングを示す*ビュー イベント*。</li><li>1 つ以上の目標と、いつ目標に達したかを示す*コンバージョン イベント*。</li><li>実験で使用する変数データを定義する、1 つ以上の*バリエーション*。 *コントロール* バリエーションでは、実験用のプロジェクトで定義されている既定の変数値が使用されます。 通常、実験には、コントロール バリエーションに加えて、実験に固有の変数値を持つ追加バリエーションが少なくとも 1 つあります。 </li></ul>          |
| プロジェクト ID    |   アプリをデベロッパー センターアカウントのプロジェクトに関連付ける一意の ID です。 この ID を使用して、アプリ コード内の A/B テスト サービスに接続し、バリエーション データを受信して、ビュー イベントとコンバージョン イベントをデベロッパー センターに報告する必要があります。 詳しくは、「[アプリの実験用のコードを記述する](code-your-experiment-in-your-app.md)」をご覧ください。<p></p><p>各プロジェクト (およびプロジェクト内のすべての実験) は、1 つのプロジェクト ID のみに関連付けられます。 プロジェクト ID を使用することで、さまざまな実験のセットを区別しやすくなります。 たとえば、ある実験のセットは社内のテスターにリリースし、別の実験のセットは外部のアプリ ユーザーにのみリリースするという場合があります。  アプリが実験を複数実装している場合は、アプリから複数のプロジェクト ID を参照できます。</p>         |
| バリエーション    |   実験でテストする 1 つ以上の変数のコレクションです。 いずれの実験でも、少なくとも 1 つの変数と 2 つのバリエーション (コントロールなど) があります。 実験には、最大 5 つのバリエーションを定義できます。           |
| 変数    |  プロパティや、アプリ内のその他の値を初期化するためにアプリで使用される値です。 実験の実行中、変数の値は、バリエーションに従って変化します。 実験が終了したら、すべてのアプリ ユーザーにリリースするバリエーションの値を変数に割り当てます。 変数には、文字列型、ブール値型、倍精度浮動小数点数型、または整数型を含めることができます。
| ビュー イベント    |  実験の一部であるバリエーションのチェックをユーザーが開始するときのアクティビティを表す任意の文字列です。 通常、これはコード内のイベントの名前です。 ユーザーがバリエーションのチェックを開始すると、このビュー イベント文字列がアプリ コードによってデベロッパー センターに送信されます。 詳しくは、「[アプリの実験用のコードを記述する](code-your-experiment-in-your-app.md)」をご覧ください。
| コンバージョン イベント    |  実験の目標を表す任意の文字列です。 通常、これはコード内のイベントの名前です。 ユーザーが目標に到達すると、このコンバージョン イベント文字列がアプリ コードによってデベロッパー センターに送信されます。 詳しくは、「[アプリの実験用のコードを記述する](code-your-experiment-in-your-app.md)」をご覧ください。  

## <a name="related-topics"></a>関連トピック

* [プロジェクトを作成し、デベロッパー センター ダッシュボードでリモート変数を定義する](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [アプリの実験用のコードを記述する](code-your-experiment-in-your-app.md)
* [デベロッパー センター ダッシュボードで実験を定義する](define-your-experiment-in-the-dev-center-dashboard.md)
* [デベロッパー センター ダッシュボードで実験を管理する](manage-your-experiment.md)
* [A/B テストを使用して最初の実験を作成および実行する](create-and-run-your-first-experiment-with-a-b-testing.md)