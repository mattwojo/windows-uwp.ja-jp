---
author: mcleblanc
description: ユニバーサル 8.1 アプリがある場合は、そのターゲットが Windows 8.1 と Windows Phone 8.1 のどちらかであっても、両方であっても、ソース コードとスキルをスムーズに Windows 10 に移植することができます。
title: Windows ランタイム 8.x から UWP への移行&quot;
ms.assetid: ac163b57-dee0-43fa-bab9-8c37fbee3913
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 37da1d6385bf18fcf44f6425b843715e1a462379
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.locfileid: "246505"
---
# <a name="move-from-windows-runtime-8x-to-uwp"></a>Windows ランタイム 8.x から UWP への移行

\[Windows 10 の UWP アプリ向けに更新。 Windows 8.x の記事については、[アーカイブ](http://go.microsoft.com/fwlink/p/?linkid=619132)をご覧ください\]

ユニバーサル 8.1 アプリがある場合は、そのターゲットが Windows 8.1 と Windows Phone 8.1 のどちらかであっても、両方であっても、ソース コードとスキルをスムーズに Windows 10 に移植することができます。 Windows 10 では、ユニバーサル Windows プラットフォーム (UWP) アプリを作成できます。これは、どのような種類のデバイスにでもインストールできる単一のアプリ パッケージです。 Windows 10、UWP アプリ、およびこの移植ガイドで説明されているアダプティブ コードとアダプティブ UI の概念の詳しい背景については、「[UWP アプリのガイド](https://msdn.microsoft.com/library/windows/apps/dn894631)」をご覧ください。

移植を行うとき、Windows 10 では、API だけでなく、XAML マークアップ、UI フレームワーク、およびツールの大部分を以前のプラットフォームと共有しており、そのすべてが、見慣れたものであることがわかります。 以前と同様に、XAML UI フレームワークとともに使用するプログラミング言語として、C++、C#、Visual Basic のどれかを選択できます。 現在のアプリの取り扱いの詳細を計画する最初のステップは、所有するアプリとプロジェクトの種類によって異なります。 これについては、次のセクションで説明します。

## <a name="if-you-have-a-universal-81-app"></a>ユニバーサル 8.1 アプリがある場合

ユニバーサル 8.1 アプリは、8.1 ユニバーサル アプリ プロジェクトから構築されます。 たとえば、プロジェクトの名前が AppName\_81 であるとします。 これには、次のサブプロジェクトが含まれます。

-   AppName\_81.Windows。 これは、Windows 8.1 用アプリ パッケージを構築するプロジェクトです。
-   AppName\_81.WindowsPhone。 これは、Windows Phone 8.1 用アプリ パッケージを構築するプロジェクトです。
-   AppName\_81.Shared。 これは、他の 2 つのプロジェクトの両方で使われるソース コード、マークアップ ファイル、および他のアセットやリソースを含むプロジェクトです。

多くの場合、8.1 ユニバーサル Windows アプリは、Windows 8.1 と Windows Phone 8.1 の両方の形式で、同じコードとマークアップを使って、同じ機能を提供します。 このようなアプリは、ユニバーサル デバイス ファミリを対象とする 1 つの Windows 10 アプリに移植するには最適な候補です (これにより、さまざまなデバイスにインストールできます)。 基本的には、共有プロジェクトのコンテンツを移植し、他の 2 つのプロジェクトには、コンテンツがほとんどないため、ほとんど使用する必要がありません。

また、Windows 8.1 と Windows Phone 8.1 のいずれかまたは両方の形式のアプリには、独自の機能が含まれます。 または、同じ機能が含まれていますが、別のテクニックやテクノロジを使用して、これらの機能を実装します。 このようなアプリでは、ユニバーサル デバイス ファミリを対象とした 1 つのアプリに移植するか (この場合、アプリ自体がさまざまなデバイスに対応する必要があります)、または複数のアプリ (たとえば、デスクトップ デバイス ファミリを対象としたアプリとモバイル デバイス ファミリを対象としたアプリ) として移植するかを選ぶことができます。 ユニバーサル 8.1 アプリの特性に基づいて、これらの選択肢のどちらが最適かを判別できます。

1.  共有プロジェクトのコンテンツを、ユニバーサル デバイス ファミリを対象とするアプリに移植します。 該当する場合は、Windows プロジェクトと WindowsPhone プロジェクトからその他のコンテンツをすべて回収し、それを無条件にアプリで使用するか、その時点でアプリが実行されているデバイスで条件付きで使用します (後者の動作は、*アダプティブ*と呼ばれます)。
2.  WindowsPhone プロジェクトのコンテンツを、ユニバーサル デバイス ファミリーを対象とするアプリに移植します。 該当する場合は、Windows プロジェクトからその他のコンテンツをすべて回収し、それを無条件に、またはアダプティブに使用します。
3.  Windows プロジェクトのコンテンツを、ユニバーサル デバイス ファミリーを対象とするアプリに移植します。 該当する場合は、WindowsPhone プロジェクトからその他のコンテンツをすべて回収し、それを無条件に、またはアダプティブに使用します。
4.  Windows プロジェクトの内容を、ユニバーサル デバイス ファミリーまたはデスクトップ デバイス ファミリーが対象のアプリに移植し、WindowsPhone プロジェクトの内容も、ユニバーサル デバイス ファミリーまたはデスクトップ デバイス ファミリーが対象のアプリに移植します。 共有プロジェクトでソリューションを作成し、2 つのプロジェクト間で引き続き、ソース コード、マークアップ ファイル、およびその他の資産とリソースを共有することができます。 または、さまざまなソリューションを作成しながら、リンクを使用して、同じ項目を引き続き共有することもできます。

## <a name="if-you-have-a-windows-81-app"></a>Windows 8.1 アプリがある場合

プロジェクトを、ユニバーサル デバイス ファミリーまたはデスクトップ デバイス ファミリーを対象とするアプリに移植します。 ユニバーサル デバイス ファミリを選択しており、デスクトップ デバイス ファミリにのみ実装されている API を呼び出す場合は、これらの呼び出しをアダプティブ コードで保護できます。

## <a name="if-you-have-a-windows-phone-81-app"></a>Windows Phone 8.1 アプリがある場合

プロジェクトを、ユニバーサル デバイス ファミリーまたはモバイル デバイス ファミリーを対象とするアプリに移植します。 ユニバーサル デバイス ファミリを選択しており、モバイル デバイス ファミリにのみ実装されている API を呼び出す場合は、これらの呼び出しをアダプティブ コードで保護できます。

## <a name="adapting-your-app-to-multiple-form-factors"></a>複数のフォーム ファクターへのアプリの対応

前のセクションで選んだ選択肢によって、アプリが実行されるデバイスの種類が決まります。場合によっては、非常に多種多様なデバイスになることがあります。 アプリをモバイル デバイス ファミリーに制限した場合でも、さまざまな画面サイズをサポートする必要があります。 そのため、以前はサポートしていなかったフォーム ファクターでアプリが実行される場合は、これらのフォーム ファクターで UI をテストし、必要なすべての変更を加えて、UI が各フォーム ファクターに適切に対応するようにします。 これは、移植後のタスクまたは移植の拡張目標と考えることができます。これについての実践的な例が「[Bookstore2](w8x-to-uwp-case-study-bookstore2.md)」や「[QuizGame](w8x-to-uwp-case-study-quizgame.md)」のケース スタディに紹介されています。

## <a name="approaching-porting-layer-by-layer"></a>レイヤーごとの移植アプローチ

ユニバーサル 8.1 アプリを UWP アプリのモデルに移植する場合、実際には、お持ちの知識と経験をすべて役立てることができます。同様に、お使いのソース コードやマークアップ、ソフトウェアのパターンのほとんどを利用することもできます。

-   **ビュー**。 ビューは (ビュー モデルと共に)、アプリの UI を構成します。 理想的にはビューは、ビュー モデルの監視可能なプロパティに対するマークアップ バインドから成ります。 また、ビュー モデルのもう 1 つのパターンとして、UI 要素を直接操作する分離コード ファイル内の命令型コード用のビュー モデルがあります (このようなビュー モデルは一般的で使いやすいビュー モデルですが、使われるのは短期間です)。 いずれの場合でも、UI マークアップと設計、および UI 要素を操作するための命令型コードについても、移植は簡単に実行できます。
-   **ビュー モデルとデータ モデル**。 形式的な懸念事項分離パターン (MVVM など) を取り入れていなくても、ビュー モデルおよびデータ モデルの関数を実行するコードがアプリ内に必然的に存在します。 ビュー モデル コードでは、UI フレームワークの名前空間内の型を使います。 また、ビュー モデルおよびデータ モデル コードは共に、非視覚的なオペレーティング システム API および .NET Framework API を使います (データ アクセス用の API を含みます)。 これらの API は、[UWP アプリでも利用可能](https://msdn.microsoft.com/library/windows/apps/br211369)であるため、このコードの (すべてではありませんが) ほとんどが、変更なしで移植されます。
-   **クラウド サービス**。 アプリのいくつか (おそらく、その多く) が、サービスの形式でクラウド内で実行します。 クライアント デバイス上で実行する一部のアプリは、こうしたアプリに接続します。 これは、クライアント部分の移植時に、変化しない可能性が最も高い分散アプリの部分です。 まだ用意されていない場合、[Microsoft Azure のモバイル サービス](http://azure.microsoft.com/services/mobile-services/)は、UWP アプリに対する適切なクラウド サービス オプションになります。これは、ライブ タイル更新のための簡単な通知から、サーバー ファームが提供する高負荷のスケーラビリティに至るまで、アプリで一連のサービスを呼び出すことができる強力なバックエンド コンポーネントを提供します。

移植前または移植中に、同様の目的を持つコードがレイヤー内に集められ、随意に散在しないように、アプリがリファクタリングによって向上するかどうかを考慮します。 前述したように、アプリをレイヤーにファクタリングすることで、アプリの適合性、テスト、以降の読み取りと維持が容易になります。 Model-View-ViewModel ([MVVM](http://msdn.microsoft.com/magazine/dd419663.aspx)) パターンに従うと、機能をより再利用可能にすることができます。 このパターンにより、アプリのデータ部、ビジネス部、UI 部の相互の分離性が維持されます。 UI 内であっても、状態と動作を別個に維持し、視覚効果から個別にテスト可能にすることができます。 MVVM により、データおよびビジネス ロジックを 1 回記述すれば、UI に関係なく、それをすべてのデバイスで使うことができます。 各デバイスで、ビュー モデルとビュー部品の多くを再利用できる可能性があります。

| トピック | 説明 |
|-------|-------------|
| [プロジェクトの移植](w8x-to-uwp-porting-to-a-uwp-project.md) | 移植プロセスを開始するとき、2 つの方法から選ぶことができます。 1 つは、既にあるプロジェクト ファイル (アプリ パッケージ マニフェストなど) のコピーを編集する方法です。この方法については、[アプリをユニバーサル Windows プラットフォーム (UWP) へ移行する](https://msdn.microsoft.com/library/mt148501.aspx)に記載されているプロジェクト ファイルの更新に関する説明をご覧ください。 もう 1 つの方法は、Visual Studio で新しい Windows 10 プロジェクトを作成し、お使いのファイルをそのプロジェクトにコピーする方法です。 |
| [トラブルシューティング](w8x-to-uwp-troubleshooting.md) | この移植ガイドは最後まで読むことを強くお勧めしますが、早く先へ進んで、プロジェクトのビルドと実行の段階まで到達したいと思われるのも無理のないことです。 このために、重要でないコードに対してコメント アウトやスタブの挿入を行って一時的に先に進み、後でその部分に戻って対応することもできます。 このトピックには、トラブルシューティングの現象とその対処法を示す表が記載されており、以降のいくつかのトピックに示されている情報に代わるものではありませんが、この段階での作業に役立ちます。 以降のトピックを読み進む中で、いつでもこの表に戻って参考にすることができます。 |
| [XAML と UI の移植](w8x-to-uwp-porting-xaml-and-ui.md) | 宣言型 XAML マークアップ形式での UI の定義は、ユニバーサル 8.1 アプリから UWP アプリに適切に変換されます。 ほとんどのマークアップには互換性がありますが、場合によっては、使っているシステムのリソース キーやカスタム テンプレートを調整する必要があります。 |
| [入出力、デバイス、アプリ モデルの移植](w8x-to-uwp-input-and-sensors.md) | デバイス自体とそのセンサーに統合するコードには、ユーザーに対する入力と出力が含まれます。 また、データ処理を含むこともあります。 ただしこのコードは一般には、UI レイヤーまたはデータ レイヤーのいずれにも見なされません。 このコードには、振動コントローラー、加速度計、ジャイロスコープ、マイクとスピーカー (音声認識と音声合成で使います)、地理位置情報、およびタッチ、マウス、キーボード、ペンなどの入力モダリティとの統合が含まれます。 |
| [ケース スタディ: Bookstore1](w8x-to-uwp-case-study-bookstore1.md) | このトピックでは、シンプルなユニバーサル 8.1 アプリを Windows 10 UWP アプリへ移植するケース スタディについて説明します。 ユニバーサル 8.1 アプリは、Windows 8.1 用のアプリ パッケージと、Windows Phone 8.1 用の別のアプリ パッケージをビルドするアプリです。 Windows 10 では、さまざまなデバイスにユーザーがインストールできる単一のアプリ パッケージを作成できます。このようなアプリ パッケージの作成を、このケース スタディで取り上げます。 「[UWP アプリのガイド](https://msdn.microsoft.com/library/windows/apps/dn894631)」をご覧ください。 |
| [ケース スタディ: Bookstore2](w8x-to-uwp-case-study-bookstore2.md) | このケース スタディは、[SemanticZoom](https://msdn.microsoft.com/library/windows/apps/hh702601) コントロールに関する情報に基づいて作成されています。 ビュー モデルでは、Author クラスの各インスタンスが該当する著者によって書かれた書籍のグループを表します。SemanticZoom では、著者ごとにグループ化された書籍の一覧を表示したり、縮小して著者のジャンプ リストを表示したりすることができます。 |
| [ケース スタディ: QuizGame](w8x-to-uwp-case-study-quizgame.md) | このトピックでは、機能しているピア ツー ピアのクイズ ゲームに関する WinRT 8.1 サンプル アプリを、Windows 10 UWP アプリへ移植する場合のケース スタディについて説明します。 |

## <a name="related-topics"></a>関連トピック

**ドキュメント**
* [Windows ランタイム リファレンス](https://msdn.microsoft.com/library/windows/apps/br211377)
* [すべての Windows デバイスを対象としたユニバーサル Windows アプリの構築](http://go.microsoft.com/fwlink/p/?LinkID=397871)
* [アプリの UX の設計](https://msdn.microsoft.com/library/windows/apps/hh767284)