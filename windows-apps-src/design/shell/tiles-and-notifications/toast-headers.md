---
description: ヘッダーを使用して、アクションセンターでトースト通知を視覚的にグループ化する方法について説明します。
title: トースト ヘッダー
label: Toast headers
template: detail.hbs
ms.date: 12/07/2017
ms.topic: article
keywords: windows 10, uwp, トースト, ヘッダー, トースト ヘッダー, 通知, トーストのグループ化, アクション センター
ms.localizationpriority: medium
ms.openlocfilehash: 1afc354b15b7c916426ca3c0a7130b777c21e0cf
ms.sourcegitcommit: a3bbd3dd13be5d2f8a2793717adf4276840ee17d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93033075"
---
# <a name="toast-headers"></a>トースト ヘッダー

通知に対してトースト ヘッダーを使用して、アクション センター内の互いに関連する複数の通知を視覚的にグループ化することができます。

> [!IMPORTANT]
> **デスクトップ版の Creators Update と Notifications ライブラリ 1.4.0 が必要** : トースト ヘッダーを表示するには、デスクトップ版ビルド 15063 以上を実行している必要があります。 トーストのコンテンツ内にヘッダーを作成するには、[UWP コミュニティ ツールキットの Notifications NuGet ライブラリ](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)、バージョン 1.4.0 以上を使用する必要があります。 ヘッダーはデスクトップでのみサポートされます。

以下に示すように、このグループの会話は "Camping!!" という 1 つのヘッダーの下にまとめられています。 会話内の個々のメッセージは、同じトースト ヘッダーを共有する別個のトースト通知です。

<img alt="Toasts with header" src="images/toast-headers-action-center.png" width="396"/>

通知は、カテゴリに基づいて視覚的にグループ化することもできます。たとえば、搭乗便のリマインダー、荷物の追跡などのカテゴリーを使用できます。

## <a name="add-a-header-to-a-toast"></a>トーストへのヘッダーの追加

トースト通知にヘッダーを追加する方法は次のとおりです。

> [!NOTE]
> ヘッダーはデスクトップでのみサポートされます。 ヘッダーをサポートしないデバイスでは、ヘッダーが無視されます。

#### <a name="builder-syntax"></a>[ビルダーの構文](#tab/builder-syntax)

```csharp
new ToastContentBuilder()
    .AddHeader("6289", "Camping!!", "action=openConversation&id=6289")
    .AddText("Anyone have a sleeping bag I can borrow?");
```

#### <a name="xml"></a>[XML](#tab/xml)

```xml
<toast>

    <header
        id="6289"
        title="Camping!!"
        arguments="action=openConversation&amp;id=6289"/>

    <visual>
        ...
    </visual>

</toast>
```

---

以上をまとめると次のようになります。

1. **Header** を **ToastContent** に追加します。
2. 必要な **Id** 、 **Title** 、 **Arguments** プロパティを割り当てます。
3. 通知を送信します ([詳細情報](send-local-toast.md))。
4. 別の通知で同じヘッダー ID ( **Id** ) を使用して、それらの通知を同じヘッダーの下にまとめます。 **Id** は複数の通知をグループ化するかどうかの判断に使用される唯一のプロパティであり、これが同じであれば、 **Title** や **Arguments** が異なっていても同じグループに分類されます。 **Title** と **Arguments** は、グループ内の最新の通知のタイトルと引数が使用されます。 その最新の通知が削除された場合、2 番目に新しい通知が繰り上がって最新となり、その通知の **Title** と **Arguments** が使用されます。


## <a name="handle-activation-from-a-header"></a>ヘッダーからのアクティブ化の処理

ヘッダーはクリック可能です。ユーザーはヘッダーをクリックしてアプリから詳細情報を表示できます。

そのため、アプリではトースト自体の起動引数に似た **Arguments** をヘッダーに設定できます。

アクティブ化は、 [通常のトーストのアクティブ化](send-local-toast.md#step-4-handling-activation)と同じ方法で処理されるため、ユーザーがトースト本体やトーストのボタンをクリックした場合と同様、`App.xaml.cs` の **OnActivated** メソッドでこれらの引数を取得できます。

```csharp
protected override void OnActivated(IActivatedEventArgs e)
{
    // Handle toast activation
    if (e is ToastNotificationActivatedEventArgs)
    {
        // Arguments specified from the header
        string arguments = (e as ToastNotificationActivatedEventArgs).Argument;
    }
}
```


## <a name="additional-info"></a>追加情報

ヘッダーは複数の通知を視覚的に分類し、グループ化します。 アプリが保持できる通知の最大数 (20) や、先入れ先出し法による通知の一覧の処理など、その他のしくみはヘッダーを使用しても変わりません。

ヘッダー内で通知が表示される順序は、アプリごとに、そのアプリの最新の通知 (ヘッダーの一部である場合は、ヘッダー グループ全体) が最初に表示されます。

**Id** には、任意の文字列を設定できます。 **ToastHeader** のどのプロパティにも、長さや文字の制限はありません。 唯一の制限は、XML トースト コンテンツ全体の上限が 5 KB ということのみです。

ヘッダーを作成しても、[詳細を表示] ボタンが表示される前に、アクション センター内に表示される通知の数は変わりません (この数は既定で 3 ですが、ユーザーが設定で [システム] を選択して、通知についてアプリごとに構成できます)。

アプリのタイトルをクリックした場合と同様、ヘッダーをクリックしても、このヘッダーに属する通知は消去されません (関連の通知を消去するには、アプリでトースト API を使用する必要があります)。


## <a name="related-topics"></a>関連トピック

- [ローカル トースト通知の送信](send-local-toast.md)
- [トースト コンテンツのドキュメント](adaptive-interactive-toasts.md)
