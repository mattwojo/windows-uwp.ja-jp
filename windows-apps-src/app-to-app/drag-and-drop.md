---
description: この記事では、ユニバーサル Windows プラットフォーム (UWP) アプリにドラッグ アンド ドロップを追加する方法について説明します。
title: ドラッグ アンド ドロップ
ms.assetid: A15ED2F5-1649-4601-A761-0F6C707A8B7E
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7854c0bb541c04ec3cc109ad32ce30ba1c8bd52e
ms.sourcegitcommit: 9f059b37e45099b4314c96a0b604449e966d3c3c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
ms.locfileid: "1704653"
---
# <a name="drag-and-drop"></a>ドラッグ アンド ドロップ



この記事では、ユニバーサル Windows プラットフォーム (UWP) アプリにドラッグ アンド ドロップを追加する方法について説明します。 ドラッグ アンド ドロップは、画像やファイルなどのコンテンツを操作するための従来からある自然な方法です。 ドラッグ アンド ドロップを実装すると、アプリからアプリ、アプリからデスクトップ、デスクトップからアプリなど、あらゆる方向でシームレスに機能します。

## <a name="set-valid-areas"></a>有効な領域を設定する

[**AllowDrop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.AllowDrop) プロパティと [**CanDrag**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.CanDrag) プロパティを使うと、ドラッグ アンド ドロップの操作に有効なアプリ内の領域を指定できます。

次のマークアップは、XAML で [**AllowDrop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.AllowDrop) を使って、アプリの特定の領域をドロップ操作に有効な領域として設定する方法を示しています。 ユーザーが他の場所へのドロップを試みても、ドロップすることはできません。 アプリ内のすべての領域でユーザーが項目をドロップできるようにする場合は、背景全体をドロップ ターゲットとして設定します。

[!code-xml[Main](./code/drag_drop/cs/MainPage.xaml#SnippetDropArea)]

ドラッグ操作では通常、どの項目がドラッグ可能であるか指定しておく必要があります。 ユーザーがドラッグしようとするのは、アプリ内のすべてではなく、画像などの特定の項目です。 XAML を使って [**CanDrag**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.CanDrag) を設定する方法を次に示します。

[!code-xml[Main](./code/drag_drop/cs/MainPage.xaml#SnippetDragArea)]

UI をカスタマイズする場合 (この記事の後半で説明します) を除き、他には何もしなくてもドラッグ操作を有効にできます。 ドロップ操作には、あといくつかの手順が必要です。

## <a name="handle-the-dragover-event"></a>DragOver イベントを処理する

[**DragOver**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.DragOver) イベントは、ユーザーがアプリに項目をドラッグし、まだドロップしていないときに発生します。 このハンドラーでは、[**AcceptedOperation**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.DragEventArgs.AcceptedOperation) プロパティを使って、アプリがサポートしている操作の種類を指定する必要があります。 最も一般的な操作はコピーです。

[!code-cs[Main](./code/drag_drop/cs/MainPage.xaml.cs#SnippetGrid_DragOver)]

## <a name="process-the-drop-event"></a>Drop イベントを処理する

[**Drop**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.Drop) イベントは、有効なドロップ領域内でユーザーが項目を放したときに発生します。 放した項目を処理するには [**DataView**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.DragEventArgs.DataView) プロパティを使います。

次の例では、わかりやすくするために、ユーザーが単一の写真をドロップして直接それにアクセスしたとします。 実際には、ユーザーがさまざまな形式の複数の項目を同時にドロップすることもあります。 アプリで、ドロップされたファイルの種類とファイル数を確認することでこの状況を処理し、状況に応じてそれぞれを処理する必要があります。 また、ユーザーがアプリでサポートされていない処理を実行しようとしたときに、ユーザーに通知することを検討する必要があります。

[!code-cs[Main](./code/drag_drop/cs/MainPage.xaml.cs#SnippetGrid_Drop)]

## <a name="customize-the-ui"></a>UI をカスタマイズする

システムでは、ドラッグ アンド ドロップ用に既定の UI が提供されています。 ただし、カスタムのキャプションやグリフを設定して UI のさまざまな部分をカスタマイズすることも、UI をまったく表示しないこともできます。 UI をカスタマイズするには、[**DragEventArgs.DragUIOverride**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.DragEventArgs.DragUIOverride) プロパティを使います。

[!code-cs[Main](./code/drag_drop/cs/MainPage.xaml.cs#SnippetGrid_DragOverCustom)]

## <a name="open-a-context-menu-on-an-item-you-can-drag-with-touch"></a>タッチによるドラッグが可能な項目のコンテキスト メニューを開く

タッチを使い、[**UIElement**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement) をドラッグして、コンテキスト メニューを開くには、類似したタッチ ジェスチャを使用します。それぞれ長押しから始まります。 アプリの要素が 2 つのアクションをサポートしている場合に、システムがそれを区別する方法を次に示します。 

* ユーザーがある項目を長押しし、500 ミリ秒以内にドラッグを開始した場合、項目はドラッグされ、コンテキスト メニューは表示されません。 
* ユーザーが長押ししてから 500 ミリ秒以内にドラッグしなかった場合には、コンテキスト メニューが開きます。 
* コンテキスト メニューが開いた後に、ユーザーが指を離すことなく、項目をドラッグしようとすると、コンテキスト メニューは閉じられ、ドラッグが開始されます。

## <a name="designate-an-item-in-a-listview-or-gridview-as-a-folder"></a>ListView または GridView の項目をフォルダーとして指定する

[ **ListViewItem** ](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.ListViewItem) または [ **GridViewItem** ](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.GridViewItem) をフォルダーとして指定できます。 これは、ツリー ビューとエクスプローラーのシナリオで特に便利です。 これを行うには、その項目で [ **AllowDrop** ](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.AllowDrop) プロパティを明示的に **True** に設定します。 

(非フォルダー項目にではなく) フォルダーにドロップするための、適切なアニメーションが自動的に表示されます。 アプリのコードは、フォルダー項目の[**ドロップ**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.UIElement.Drop) イベントの処理 (および非フォルダー項目の処理) を継続し、データ ソースを更新して、ドロップ先のフォルダーにドロップされた項目を追加する必要があります。

## <a name="see-also"></a>関連項目

* [アプリ間通信](index.md)
* [AllowDrop](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.allowdrop.aspx)
* [CanDrag](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.candrag.aspx)
* [DragOver](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.dragover.aspx)
* [AcceptedOperation](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.drageventargs.acceptedoperation.aspx)
* [DataView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.drageventargs.dataview.aspx)
* [DragUIOverride](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.drageventargs.draguioverride.aspx)
* [Drop](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.uielement.drop.aspx)
* [IsDragSource](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.isdragsource.aspx)