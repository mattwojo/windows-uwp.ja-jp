---
author: mcleanbyron
ms.assetid: cb7380d0-bc14-4936-aa1c-206304b3dc70
description: Microsoft Advertising ライブラリの AdControl クラスによって生成されたエラーを処理する方法について説明します。
title: 広告のエラー処理
ms.author: mcleans
ms.date: 08/23/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, 広告, 宣伝, エラー処理, JavaScript, XAML, C#
ms.localizationpriority: medium
ms.openlocfilehash: 5bdbf33cba031bfbeca2216affe7c560b5521b24
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
ms.locfileid: "1654121"
---
# <a name="handle-ad-errors"></a>広告のエラー処理

[AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)、[InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)、[NativeAdsManager](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.nativeadsmanager.aspx) の各クラスには、広告関連のエラーが発生した場合に発生する **ErrorOccurred** イベントがあります。 アプリ コードでこのイベントを処理し、イベント引数オブジェクトの [ErrorCode](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.aderroreventargs.errorcode.aspx) プロパティと [ErrorMessage](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.aderroreventargs.errormessage.aspx) プロパティを調べて、エラーの原因を特定することができます。

<span id="bkmk-dotnet"/>

## <a name="xaml-apps"></a>XAML アプリ

XAML アプリで広告関連のエラーを処理するには:

1. **AdControl**、**InterstitialAd**、**NativeAdsManager** オブジェクトの **ErrorOccurred** イベントを、イベント ハンドラー デリゲートの名前に割り当てます。

2. 送信元の **Object** と [AdErrorEventArgs](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.aderroreventargs.aspx) オブジェクトの、2 つのパラメーターを受け取るようにエラー イベント処理デリゲートのコードを記述します。

**OnAdError** という名前のデリゲートを *myBannerAdControl* という名前の **AdControl** オブジェクトの **ErrorOccurred** イベントに割り当てる例を次に示します。

> [!div class="tabbedCodeSnippets"]
``` csharp
myBannerAdControl.ErrorOccurred = OnAdError;
```

Visual Studio の出力ウィンドウにエラー情報を書き込む **OnAdError** デリゲートの定義例を次に示します。

> [!div class="tabbedCodeSnippets"]
``` csharp
private void OnAdError(object sender, AdErrorEventArgs e)
{
    System.Diagnostics.Debug.WriteLine("AdControl error (" + ((AdControl)sender).Name + "): " + e.Error +
        " ErrorCode: " + e.ErrorCode.ToString());
}
```

XAML および C# での **AdControl** エラー処理について説明するチュートリアルについては、「[XAML/C# チュートリアルでのエラー処理](error-handling-in-xamlc-walkthrough.md)」をご覧ください。

<span id="bkmk-javascript"/>

## <a name="javascripthtml-apps"></a>JavaScript/HTML アプリ

JavaScript アプリで **ErrorOccur** エラーを処理するには:

1.  **onErrorOccurred** イベントをイベント ハンドラーに割り当てます。

2.  イベント ハンドラーのコードを記述します。

**errorLogger** という名前のイベント ハンドラーを **AdControl** オブジェクトの **ErrorOccurred** イベントに割り当てる例を次に示します。

> [!div class="tabbedCodeSnippets"]
``` html
<div id="myAd" style="position: absolute; top: 53px; left: 0px; width: 250px; height: 250px; z-index: 1"
     data-win-control="MicrosoftNSJS.Advertising.AdControl"
     data-win-options="{applicationId: '3f83fe91-d6be-434d-a0ae-7351c5a997f1', adUnitId: 'test', onErrorOccurred: errorLogger}">
</div>
```

エラー処理関数は宣言型で、[markSupportedForProcessing](http://msdn.microsoft.com/library/windows/apps/Hh967819.aspx) 関数内で囲む必要があります。

エラーが発生すると、エラー ハンドラーが JavaScript エラー オブジェクトをキャッチします。 エラー オブジェクトは 2 つの引数をエラー ハンドラーに提供します。 詳しくは、「[非同期 Windows ランタイム メソッドからの特殊なエラー プロパティ](http://msdn.microsoft.com/library/windows/apps/hh994690.aspx)」をご覧ください。

**onErrorOccurred** イベントを処理する **errorLogger** という名前のエラー処理関数の例を示します。

> [!div class="tabbedCodeSnippets"]
``` javascript
WinJS.Utilities.markSupportedForProcessing(
window.errorLogger = function (sender, evt) {
    console.log(new Date()).toLocaleTimeString() + ": " + sender.element.id + " error: " + evt.errorMessage +
    " error code: " + evt.errorCode + \n");
});
```

JavaScript での **AdControl** エラー処理について説明するチュートリアルについては、「[JavaScript チュートリアルでのエラー処理](error-handling-in-javascript-walkthrough.md)」をご覧ください。