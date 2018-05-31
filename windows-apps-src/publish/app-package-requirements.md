---
author: jnHs
Description: Follow these guidelines to prepare your app's packages for submission to the Microsoft Store.
title: アプリ パッケージの要件
ms.assetid: 651B82BA-9D0C-45AC-8997-88CD93DC903C
ms.author: wdg-dev-content
ms.date: 04/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, パッケージ要件, パッケージ, パッケージ形式, サポートされているバージョン, 提出
ms.localizationpriority: high
ms.openlocfilehash: 76dd0a5f9ebcb1e92ac7874b535d286cb051df22
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832316"
---
# <a name="app-package-requirements"></a>アプリ パッケージの要件

Microsoft Store に申請するために、次のガイドラインに従ってアプリのパッケージを準備してください。

## <a name="before-you-build-your-apps-package-for-the-microsoft-store"></a>Microsoft Store に向けてアプリのパッケージを構築する前に

[Windows アプリ認定キットでアプリをテスト](../debug-test-perf/windows-app-certification-kit.md)したことを確認してください。 また、さまざまな種類のハードウェアでアプリをテストすることをお勧めします。 アプリが認定され、Microsoft Store から入手できるようになるまでの間、アプリをインストールして実行できるのは、開発者用ライセンスを持つコンピューター上のみになります。

## <a name="building-the-app-package-using-microsoft-visual-studio"></a>Microsoft Visual Studio を使ったアプリ パッケージのビルド

開発環境として Microsoft Visual Studio を使っている場合は、アプリ パッケージを迅速かつ簡単に作成するための組み込みツールが既に用意されています。 詳しくは、「[アプリのパッケージ化](../packaging/index.md)」をご覧ください。

> [!NOTE]
> すべてのファイル名に ANSI を使っていることを確認してください。 

Visual Studio でパッケージを作るときは、必ず、開発者アカウントに関連付けられている同じアカウントでサインインしてください。 パッケージ マニフェストの一部には、お使いのアカウントに関連する固有の詳細情報が含まれています。 この情報は自動的に検出されて追加されます。 マニフェストにこの追加情報が追加されていない場合、パッケージのアップロードでエラーが発生する可能性があります。 

アプリのパッケージをビルドする場合、Visual Studio では .appx ファイルまたは .appxupload ファイル (または、Windows Phone 8.1 以前の場合は .xap ファイル) を作成することができます。 Windows 10 を対象とするアプリの場合は、常に .appxupload ファイルを [パッケージ](upload-app-packages.md) ページにアップロードします。 Microsoft Store 用の UWP アプリのパッケージ化について詳しくは、「[Visual Studio での UWP アプリのパッケージ化](../packaging/packaging-uwp-apps.md)」をご覧ください。

アプリのパッケージに、信頼された証明機関が発行する証明書で署名する必要はありません。


### <a name="app-bundles"></a>アプリ バンドル

アプリの対象が Windows 8.1、Windows Phone 8.1、およびそれ以降である場合は、Visual Studio でアプリ バンドル (.appxbundle) を生成することによって、ユーザーがダウンロードするアプリのサイズを小さくすることができます。 その利便性が発揮されるのは、言語固有のアセットや多様な画像倍率のアセット、特定バージョンの Microsoft DirectX に適用されるリソースを定義した場合などです。

> [!NOTE]
> 1 つのアプリ バンドルには、すべてのアーキテクチャ用のパッケージを含めることができます。 対象 OS ごとにバンドルを 1 つだけ申請する必要があります。

アプリ バンドルが使われている場合、ユーザーは、自分に関係したファイルだけをダウンロードすればよく、すべてのリソースをダウンロードする必要はありません。 アプリ バンドルについて詳しくは、「[アプリのパッケージ化](../packaging/index.md)」と「[Visual Studio で UWP アプリをパッケージ化する](../packaging/packaging-uwp-apps.md)」をご覧ください。


## <a name="building-the-app-package-manually"></a>手動によるアプリ パッケージのビルド

パッケージの作成に Visual Studio を使わない場合は、[パッケージ マニフェストを手動で作成](https://docs.microsoft.com/uwp/schemas/appxpackage/how-to-create-a-package-manifest-manually) する必要があります。

マニフェストの詳細や要件については、[アプリ パッケージ マニフェスト](https://docs.microsoft.com/uwp/schemas/appxpackage/appx-package-manifest) に関するドキュメントをご覧ください。 認定に合格するには、マニフェストがパッケージ マニフェスト スキーマに従っている必要があります。

マニフェストには、アカウントとアプリに関するいくらかの具体的な情報を含める必要があります。 この情報は、ダッシュボードにあるアプリの概要ページの [**アプリの管理**] セクションで[アプリの ID の詳細情報を表示する](view-app-identity-details.md)ことで確認できます。

> [!NOTE]
> マニフェスト内の値は、大文字と小文字が区別されます。 スペースや句読点なども一致する必要があります。 注意して入力し、間違いがないか確認してください。


アプリ バンドルには、特別なマニフェストが使われます。 アプリ バンドル マニフェストの詳細や要件については、[バンドル マニフェスト](https://docs.microsoft.com/uwp/schemas/bundlemanifestschema/bundle-manifest)に関するドキュメントをご覧ください。

> [!TIP]
> 必ず、[Windows アプリ認定キット](../debug-test-perf/windows-app-certification-kit.md)を実行してから、パッケージを提出してください。 これによって、認定や提出の失敗の原因となる可能性がある問題がマニフェストに含まれているかどうかを判断できます。

アプリに複数のパッケージがある場合、以下のアプリ マニフェストの要素は各パッケージで (ターゲット OS ごとに) 同じである必要があります。

-   [**Package/Capabilities**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-capabilities)
-   [**Package/Dependencies**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-dependencies)
-   [**Package/Resources**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-resources)


## <a name="package-format-requirements"></a>パッケージの形式の要件

アプリのパッケージは、次の要件に準拠している必要があります。

| アプリ パッケージの性質 | 要件                                                          |
|----------------------|----------------------------------------------------------------------|
| パッケージのサイズ         | .appxbundle: バンドルあたり最大 25 GB <br>Windows 10 を対象とする .appx パッケージ: パッケージあたり最大 25 GB<br>Windows 8.1 を対象とする .appx パッケージ: パッケージあたり最大 8 GB <br> Windows 8 を対象とする .appx パッケージ: パッケージあたり最大 2 GB <br> Windows Phone 8.1 を対象とする .appx パッケージ: パッケージあたり最大 4 GB <br> .xap パッケージ: パッケージあたり最大 1 GB                                                                           |
| ブロック マップ ハッシュ     | SHA2-256 アルゴリズム                                                   |


## <a name="supported-versions"></a>サポートされているバージョン

UWP アプリの場合、すべてのパッケージは Microsoft Store によりサポートされている Windows 10 のバージョンをターゲットとする必要があります。 パッケージがサポートするバージョンは、アプリ マニフェストの [TargetDeviceFamily](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) 要素の **MinVersion** 属性と **MaxVersionTested** 属性で指定されています。

現時点でサポートされているバージョンの範囲は以下のとおりです。 
- 最小: 10.0.10240.0
- 最大: 10.0.17134.0


## <a name="storemanifest-xml-file"></a>StoreManifest XML ファイル

StoreManifest.xml は、必要に応じてアプリ パッケージに含めることのできる構成ファイルです。 その目的は、Microsoft Store デバイス アプリとしてアプリを宣言する機能や、パッケージ マニフェストの対象外となるデバイスに適用される要件を宣言する機能などを有効にすることです。 StoreManifest.xml はアプリ パッケージと共に提出し、アプリのメイン プロジェクトのルート フォルダーにあることが必要です。 詳しくは、「[StoreManifest スキーマ](https://docs.microsoft.com/uwp/schemas/storemanifest/store-manifest-schema-portal)」をご覧ください。

 

 



