---
author: TylerMSFT
title: ユニバーサル Windows プラットフォームを使用してコンソール アプリを作成する
description: このトピックでは、コンソールウィンドウで実行される UWP アプリを記述する方法について説明します。
keywords: console uwp
ms.author: twhitney
ms.date: 03/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 413f4db427557460c267370f477e16d84c8af29c
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
ms.locfileid: "1815537"
---
# <a name="create-a-universal-windows-platform-console-app"></a>ユニバーサル Windows プラットフォームを使用してコンソール アプリを作成する

このトピックでは、C++ /WinRT または /CX ユニバーサル Windows プラットフォーム (UWP) コンソール アプリを作成する方法について説明します。

Windows 10 バージョン 1803 以降では、C++ /WinRT または /CX の UWP コンソール アプリを作成して、DOS や PowerShell などのコンソール ウィンドウで実行できるようになりました。 コンソール アプリはコンソール ウィンドウを使用して入力と出力を行い、**printf** や **getchar** などの UWP アプリで使用可能な Win32 API を使用できます。 Microsoft Store には、UWP コンソール アプリを公開することができます。 それらのアプリは、アプリのリストにエントリがあり、スタート メニューに固定することができるプライマリ タイルがあります。 UWP コンソール アプリは、スタート メニューから起動することができますが、通常はコマンドラインから起動します。

実際の動作を確認するには、UWP コンソール アプリの作成に関するこのビデオをご覧ください。
> [!VIDEO https://www.youtube.com/embed/bwvfrguY20s]

## <a name="use-a-uwp-console-app-template"></a>UWP コンソール アプリ テンプレートを使用する 

UWP コンソール アプリを作成するには、まず [Visual Studio Marketplace](https://aka.ms/E2nzbv) から入手できる**コンソール アプリ (ユニバーサル) プロジェクト テンプレート**をインストールします。 インストールされているテンプレートは、**[新しいプロジェクト]** > **[インストール]** > **[他の言語]** > **[Visual C++]** > **[Windows ユニバーサル]** で、**コンソール アプリ C++/CX (ユニバーサル Windows)** および **コンソール アプリ C++/WinRT (ユニバーサル Windows)** として使用できます。

## <a name="add-your-code-to-main"></a>Main() にコードを追加します。

テンプレートは **Program.cpp** を追加します。これには `main()` 関数が含まれています。 これは、UWP コンソール アプリで実行が開始される場所です。 `__argc` および `__argv` パラメーターでコマンドライン引数にアクセスします。 制御が `main()` から返ってくると、UWP コンソール アプリは終了します。

**Program.cpp** の次の例は、**Console App C++ /WinRT** テンプレートによって追加されています。

```cpp
#include "pch.h"

using namespace winrt;

// This example code shows how you could implement the required main function
// for a Console UWP Application. You can replace all the code inside main
// with your own custom code.

int __cdecl main()
{
    // You can get parsed command-line arguments from the CRT globals.
    wprintf(L"Parsed command-line arguments:\n");
    for (int i = 0; i < __argc; i++)
    {
        wprintf(L"__argv[%d] = %S\n", i, __argv[i]);
    }

    // Keep the console window alive in case you want to see console output when running from within Visual Studio
      wprintf(L"Press 'Enter' to continue: ");
    getchar();
}
```

## <a name="uwp-console-app-behavior"></a>UWP コンソール アプリの動作

UWP コンソール アプリは、実行されているディレクトリ、およびその下のファイル システムにアクセスできます。 テンプレートは [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias) 拡張機能をアプリの Package.appxmanifest ファイルに追加するため、これが可能になります。 この拡張機能を使用すると、コンソール ウィンドウからエイリアスを入力してアプリを起動することもできます。 アプリを起動するためにシステムパスに入る必要はありません。

さらに、[ファイル アクセス許可](https://docs.microsoft.com/windows/uwp/files/file-access-permissions) で説明されているように、制限された機能 `broadFileSystemAccess` を追加することで、ファイルシステムへの広範なアクセスを UWP コンソール アプリに付与することができます。 この機能は、[**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346) 名前空間の API で動作します。

テンプレートによって [SupportsMultipleInstances](multi-instance-uwp.md) 機能がアプリの Package.appxmanifest ファイルに追加されるため、複数の UWP コンソール アプリのインスタンスを同時に実行できます。

テンプレートは Package.appxmanifest ファイルに `Subsystem="console"` の機能も追加します。これは、この UWP アプリがコンソール アプリであることを示しています。 `desktop4` と iot2 `namespace` プレフィックスに注意してください。 UWP コンソール アプリは、デスクトップやモノのインターネット (IoT) プロジェクトでのみサポートされています。

```xml
<Package
  ...
  xmlns:desktop4="http://schemas.microsoft.com/appx/manifest/desktop/windows10/4" 
  xmlns:iot2="http://schemas.microsoft.com/appx/manifest/iot/windows10/2" 
  IgnorableNamespaces="uap mp uap5 desktop4 iot2">
  ...
  <Applications>
    <Application Id="App"
      ...
      desktop4:Subsystem="console" 
      desktop4:SupportsMultipleInstances="true" 
      iot2:Subsystem="console" 
      iot2:SupportsMultipleInstances="true"  >
      ...
      <Extensions>
          <uap5:Extension 
            Category="windows.appExecutionAlias" 
            Executable="YourApp.exe" 
            EntryPoint="YourApp.App">
            <uap5:AppExecutionAlias desktop4:Subsystem="console">
              <uap5:ExecutionAlias Alias="YourApp.exe" />
            </uap5:AppExecutionAlias>
          </uap5:Extension>
      </Extensions>
    </Application>
  </Applications>
    ...
</Package>
```

## <a name="additional-considerations-for-uwp-console-apps"></a>UWP コンソール アプリに関するその他の考慮事項

- C++ /WinRT および C++ /CX UWP アプリのみがコンソール アプリです。
- UWP コンソール アプリはデスクトップまたは IoT プロジェクト タイプをターゲットにする必要があります。
- UWP コンソール アプリンはウィンドウを作成しない場合があります。 たとえば、ウィンドウを作成するため、MessageBox() は使用できません。
- UWP コンソール アプリは、バックグラウンド タスクを消費したり、バックグラウンド タスクとして機能したりしない場合があります。
- [コマンド ラインのアクティブ化](https://blogs.windows.com/buildingapps/2017/07/05/command-line-activation-universal-windows-apps/#5YJUzjBoXCL4MhAe.97) を除き、UWP コンソール アプリは、ファイルの関連付け、プロトコルの関連付けなどのアクティブ化をサポートしていません。
- UWP コンソール アプリは複数インスタンスをサポートしていますが、[複数インスタンスのリダイレクト](multi-instance-uwp.md) はサポートしていません
- UWP アプリで使用できる Win32 API の一覧については、「[UWP アプリ用の Win32 API と COM API](https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps)」をご覧ください。