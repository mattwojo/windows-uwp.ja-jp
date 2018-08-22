---
ms.assetid: 4b0c86d3-f05b-450b-bf9c-6ab4d3f07d31
description: このロードマップでは、Windows 10 およびユニバーサル Windows プラットフォーム (UWP) アプリの主要なエンタープライズ機能の概要について説明します。
title: エンタープライズ
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 28d005d76fa8d412eb283e409ea7f5d673bfd857
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.locfileid: "243316"
---
# <a name="enterprise"></a>エンタープライズ


\[Windows 10 の UWP アプリ向けに更新。 Windows 8.x の記事については、[アーカイブ](http://go.microsoft.com/fwlink/p/?linkid=619132)をご覧ください。\]

このロードマップでは、Windows 10 ユニバーサル Windows プラットフォーム (UWP) の主要なエンタープライズ機能の概要について説明します。 Windows 10 では、アプリを 1 回記述するだけで、すべてのデバイスに展開できます。つまり、すべてのデバイスに対応した 1 つのアプリを作成できます。 これにより、企業が必要とするセキュリティ、管理、構成をコントロールしながら、ユーザーが求めるすばらしいエクスペリエンスを構築できます。

**注**  この記事は、エンタープライズ UWP アプリを作成する開発者を対象としています。 一般的な UWP 開発については、「[Windows 10 アプリに関するハウツー ガイド](https://msdn.microsoft.com/library/windows/apps/mt244352)」をご覧ください。 WPF、Windows フォーム、Win32 開発については、[デスクトップのデベロッパー センター](https://dev.windows.com/desktop)をご覧ください。 IT 担当者向けのリソース (Windows 10 の展開やエンタープライズ セキュリティ機能の管理など) については、TechNet の「[Windows 10](https://msdn.microsoft.com/library/dn986868)」をご覧ください。

 

## <a name="security"></a>セキュリティ


Windows 10 には、一連のセキュリティ機能が用意されています。これらのセキュリティ機能を利用することで、アプリ開発者は、ユーザーの個人情報、企業ネットワークのセキュリティ、デバイスに保存されているビジネス データを保護することができます。 Windows 10 の新機能として、Microsoft Passport があります。これにより、従来のパスワードに代わる 2 要素のパスワードを簡単に展開することができます。2 要素のパスワードは、PIN や Windows Hello を使って利用することができ、エンタープライズ レベルのセキュリティを実現し、指紋認識、顔認識、虹彩認識をサポートしています。

| トピック | 説明 |
|-------|-------------|
| [安全な Windows アプリの開発について](https://msdn.microsoft.com/library/windows/apps/mt622741) | この概要記事では、認証、移動中データ、および保存データの各段階におけるさまざまな Windows のセキュリティ機能について説明します。 また、これらの段階をアプリに統合する方法についても説明します。 ここでは、さまざまなトピックを取り上げており、ユニバーサル Windows プラットフォーム アプリを短時間で簡単に作成するための Windows の機能を、アプリの設計者が詳しく理解できるようにすることを主な目的としています。 |
| [認証とユーザー ID](https://msdn.microsoft.com/library/windows/apps/mt270184) | この記事では、UWP アプリで利用できるユーザー認証のためオプションを説明します。 企業向けには、新しい Microsoft Passport 機能を強くお勧めします。 Microsoft Passport では、既存の資格情報を確認して、生体認証または PIN ベースのユーザー ジェスチャで保護されるデバイス固有の資格情報を作成することで、パスワードを強力な 2 要素認証 (2FA) に置き換えます。これにより、便利で安全性の高いエクスペリエンスが実現されます。 |
| [暗号化](https://msdn.microsoft.com/library/windows/apps/mt270191) | 「暗号化」セクションでは、UWP アプリで利用できる暗号化の機能の概要を説明します。 この記事では、重要なビジネス データを簡単に暗号化する方法についての入門用チュートリアルから、暗号化キーの操作や MAC、ハッシュ、署名の使用などの高度なトピックまでを取り上げています。 |
| [Windows 情報保護 (WIP)](wip-hub.md) | ここでは、Windows 情報保護 (WIP) と、ファイル、バッファー、クリップボード、ネットワーク、バックグラウンド タスク、ロックの背後でのデータ保護との関係についての開発者向けの詳しい情報について説明します。 |

 

## <a name="data-binding-and-databases"></a>データ バインディングとデータベース


データ バインディングは、データベースなどの外部ソースからのデータをアプリの UI で表示する方法であり、必要に応じてそのデータとの同期を維持することもできます。 データ バインディングによって、UI の問題からデータの問題を切り離すことができるため、概念的なモデルが簡素化されると共に、アプリの読みやすさ、テストの容易性、保守容易性が向上します。

| トピック | 説明 |
|-------|-------------|
| [データ バインディングの概要](https://msdn.microsoft.com/library/windows/apps/mt269383) | このトピックでは、ユニバーサル Windows プラットフォーム (UWP) アプリで、コントロール (または他の UI 要素) を単一の項目にバインドする方法や、項目コントロールを項目のコレクションにバインドする方法を説明します。 また、項目のレンダリングを制御する方法、選択内容に基づいて詳細ビューを実装する方法、表示するデータを変換する方法も紹介します。 |
| [UWP 用 Entity Framework 7](https://msdn.microsoft.com/library/windows/apps/mt592863) | 大きなデータ セットに対する複雑なクエリの実行は、UWP をサポートする Entity Framework 7 を使用することで大幅に簡素化されます。 このチュートリアルでは、Entity Framework を使用してローカル SQLite データベースへの基本的なデータ アクセスを実行する UWP アプリを構築します。 |
| [SQLite ローカル データベース](https://channel9.msdn.com/Series/A-Developers-Guide-to-Windows-10/10) | このビデオは、アプリのローカル データベースのソリューションとして推奨される SQLite を使用するための開発者向けの包括的なガイドです。 [SQLite](https://www.sqlite.org/download.html) にアクセスして UWP 用の最新バージョンをダウンロードするか、Windows 10 SDK で既に提供されているバージョンを使用してください。 |

 

## <a name="networking-and-data-serialization"></a>ネットワークとデータのシリアル化


基幹業務アプリでは、他のさまざまなシステムのデータと通信したり、こうしたシステムにデータを保存したりすることが必要になる場合があります。 通常、これはネットワーク サービスに接続し (REST や SOAP などのプロトコルを使用)、データを一般的な形式にシリアル化または逆シリアル化することによって実現されます。 UWP アプリでのネットワークとデータのシリアル化の操作は、WPF、WinForms、ASP.NET の各アプリケーションと類似しています。 詳しくは、以下の記事をご覧ください。

| トピック | 説明 |
|-------|-------------|
| [ネットワークの基本](https://msdn.microsoft.com/library/windows/apps/mt280233) | このチュートリアルでは、使用する通信プロトコルに関係なく、すべての UWP アプリに関連する基本的なネットワークの概念について説明します。  |
| [アプリに適したネットワーク テクノロジ](https://msdn.microsoft.com/library/windows/apps/mt280235) | UWP アプリで利用できるネットワーク テクノロジの概要と、アプリに適したテクノロジの選び方に関する推奨事項について説明します。 |
| [XML シリアル化および SOAP シリアル化](https://msdn.microsoft.com/library/90c86ass.aspx) | XML シリアル化では、オブジェクトが、特定の XML スキーマ定義言語 (XSD) に準拠する XML ストリームに変換されます。 XML と厳密に型指定されたクラス間の変換を行うには、ネイティブの [XDocument](https://msdn.microsoft.com/library/system.xml.linq.xdocument.aspx) クラスまたは外部ライブラリを使用します。 |
| [JSON シリアル化](https://msdn.microsoft.com/library/windows/apps/br240639) | JSON (JavaScript Object Notation) シリアル化は、REST API と通信するための一般的な形式です。 [Newtonsoft Json.NET](http://www.newtonsoft.com/json) は、UWP アプリで完全にサポートされています。 |

 

## <a name="devices"></a>デバイス


基幹業務ツール (プリンター、バー コード スキャナー、スマート カード リーダーなど) と統合するには、外部のデバイスやセンサーをアプリに統合することが必要になる場合があります。 ここでは、このセクションで説明するテクノロジを使って、アプリに追加できる機能例をいくつか紹介します。

| トピック  | 説明 |
|--------|-------------|
| [デバイスの列挙](https://msdn.microsoft.com/library/windows/apps/mt187355) | この記事では、[Windows.Devices.Enumeration](https://msdn.microsoft.com/library/windows/apps/br225459) 名前空間を使って、システムに内部接続されているデバイス、外部接続されているデバイス、ワイヤレス プロトコルまたはネットワーク プロトコル経由で検出できるデバイスを検索する方法について説明します。 デバイスと連携して動作するアプリを構築する場合は、ここから始めてください。 |
| [印刷とスキャン](https://msdn.microsoft.com/library/windows/apps/mt204544) | アプリから印刷およびスキャンする方法について説明します。販売時点管理 (POS) システム、レシート プリンター、大容量フィーダー スキャナーなどの業務用デバイスに接続する方法やこれらのデバイスを操作する方法についても説明します。 |
| [Bluetooth](https://msdn.microsoft.com/library/windows/apps/mt270288) | 従来の Bluetooth 接続を使用したデータの送受信やデバイスの制御に加えて、Windows 10 では、Bluetooth 低エネルギー (BTLE) を使用してバックグラウンドでビーコンを送受信できるようになりました。 この BTLE を利用して、通知を表示します。また、ユーザーが特定の場所に近づいた場合や特定の場所から離れた場合の機能を有効にします。 |
| [エンタープライズ共有記憶域](enterprise-shared-storage.md) | デバイスのロックダウン シナリオにおける、同じアプリ内でのデータの共有、また 1 つのアプリの複数のインスタンス間でのデータの共有、さらに複数のアプリ間でのデータの共有について、その方法を説明します。 |

 

## <a name="device-targeting"></a>対象となるデバイス


今日、多くのユーザーは自分の電話やタブレットを持ち歩いて作業を行っています。また、それらの電話やタブレットのフォーム ファクターと画面サイズにはさまざまなものがあります。 ユニバーサル Windows プラットフォーム (UWP) では、すべての種類のデバイス (デスクトップ PC や PPI ディスプレイなど) でシームレスに動作する 1 つの基幹業務アプリを作成して、アプリの範囲やコードの効率を最大限に高めることができます。

| トピック | 説明 |
|-------|-------------|
| [UWP アプリ ガイド](https://msdn.microsoft.com/library/windows/apps/dn894631) | この入門用ガイドでは、Windows 10 UWP プラットフォームについて説明します。ここでは、デバイス ファミリの説明、対象となるデバイス ファミリを決定する方法、さまざまなデバイスのフォーム ファクターに合わせて UI を対応させることができる新しい UI コントロールとパネル、およびアプリで利用できる API サーフェスを理解し制御する方法を取り上げます。 |
| [アダプティブ XAML UI コードのサンプル](http://go.microsoft.com/fwlink/p/?LinkId=619992) | このコード サンプルでは、デバイスの種類に関係なく、アプリで利用できるすべてのレイアウト オプションとコントロールが示されています。また、このコード サンプルを使うと、パネルを操作して、目的のレイアウトを実現する方法を確認できます。 さまざまなフォーム ファクターに対する各コントロールの応答方法に加えて、アプリ自体の応答性、およびアダプティブ UI を実現するためのさまざまな方法も示されています。 |

 

## <a name="deployment"></a>展開


組織のユーザーにアプリを配布するための方法がいくつかあります。 ビジネス向け Windows ストアや既存のモバイル デバイス管理ツールを使用したり、アプリをデバイスにサイドロードしたりすることができます。 Windows ストアに公開すると、一般ユーザーにもアプリを利用可能にすることができます。

| トピック | 説明 |
|-------|-------------|
| [LOB アプリの企業への配布](https://msdn.microsoft.com/library/windows/apps/mt608995) | 基幹業務アプリを、ボリューム購入できるように、ビジネス向け Windows ストアで企業に直接公開できます。一般ユーザーが利用できるようにアプリを公開する必要はありません。 |
| [アプリのサイドローディング](https://technet.microsoft.com/library/mt269549) | アプリをサイドローディングすると、署名されたアプリ パッケージをデバイスに展開します。 これらのアプリの署名、ホスティング、展開は維持されます。 アプリのサイドローディングのプロセスは、Windows 10 向けに簡素化されています。             |
| [Windows ストアへのアプリの公開](https://dev.windows.com/publish) | 統合された Windows ストアでは、すべての Windows デバイス向けのすべてのアプリを公開し管理することができます。 市場ごとの価格、配布と表示のコントロール、その他のオプションを使って、アプリの使用可能状況をカスタマイズできます。 |

 

## <a name="patterns-and-practices"></a>パターンとプラクティス


大規模なエンタープライズ レベルのアプリ向けのコード ベースは、扱うのが難しくなる場合があります。 Prism は、保守やテストが可能である疎結合な XAML アプリケーションを WPF、Windows 10 UWP、Xamarin の各フォームで構築するためのフレームワークです。 Prism には、適切に構造化され、保守が可能な XAML アプリケーションの作成に役立つ設計パターンのコレクションの実装が用意されています (MVVM、依存関係挿入、コマンド、EventAggregator など)。

Prism について詳しくは、[GitHub リポジトリ](https://github.com/PrismLibrary/Prism)をご覧ください。

 

 