---
title: Windows 10 用の Powertoy キーボードマネージャーユーティリティ
description: ユーザーがキーボードのキーを再定義できるようにするユーティリティ
ms.date: 12/02/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a8ffd782a1b23d1e439be0462300ebdf20593913
ms.sourcegitcommit: 375cf20e0583335805ec246d65819dc1674a2e32
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98241002"
---
# <a name="keyboard-manager-utility"></a>キーボードマネージャーユーティリティ

Powertoy キーボードマネージャーを使用すると、キーボードのキーを再定義できます。

たとえば、キーボードの文字<kbd>D</kbd>の文字<kbd>A</kbd>を交換できます。 <kbd>A</kbd>キーを選択すると、 <kbd>D</kbd>が表示されます。

![Powertoy キーボードマネージャーリマップキースクリーンショット](../images/powertoys-keyboard-remap.png)

また、ショートカットキーの組み合わせを交換することもできます。 たとえば、ショートカットキー <kbd>Ctrl</kbd> + <kbd>C</kbd>は、Microsoft Word でテキストをコピーします。 Powertoy のキーボードマネージャーユーティリティを使用すると、 <kbd>⊞ Win</kbd>C のショートカットを交換でき + <kbd></kbd>ます。 ここで、 <kbd>⊞ Win</kbd> + <kbd>C</kbd>) によってテキストがコピーされます。 Powertoy キーボードマネージャーで対象のアプリケーションを指定しない場合、ショートカットエクスチェンジは Windows 全体でグローバルに適用されます。

再マップされたキーとショートカットを適用するには、(Powertoy がバックグラウンドで実行されている powertoy で) Powertoy キーボードマネージャーが有効になっている必要があります。 Powertoy が実行されていない場合、キーの再マップは適用されなくなります。

![Powertoy キーボードマネージャー再マップのショートカットスクリーンショット](../images/powertoys-keyboard-shortcuts.png)

> [!NOTE]
> オペレーティングシステム用に予約されているショートカットキーがいくつかあり、置き換えることはできません。 再マップできないキーには次のものがあります。
> - `⊞ Win`+`L`およびは、 `Ctrl`  +  `Alt`  +  `Del` Windows OS によって予約されているため、再マップすることはできません。
> - `Fn`(関数) キーを再マップすることはできません (ほとんどの場合)。 `F1` - `F12` (および `F13` - `F24` ) キーをマップできます。
> - `Pause` は sngle keydown イベントのみを送信します。 たとえば、backspace キーに対してこれをマップし、押しながら保持すると、1つの文字だけが削除されます。

## <a name="settings"></a>設定

キーボードマネージャーを使用してマッピングを作成するには、Powertoy の設定を開く必要があります (Windows の [スタート] メニューで [Powertoy] アプリを検索し、これを選択すると [Powertoy の設定] ウィンドウが開きます)。 Powertoy の設定の [キーボードマネージャー] タブには、次のオプションが表示されます。

- <kbd>キーの再マップ</kbd>を選択して [キーボード設定の再マップ] ウィンドウを起動する
- <kbd>ショートカット</kbd>の再マップを選択して、[ショートカットの設定の再マップ] ウィンドウを起動します。

## <a name="remap-keys"></a>キーの再マップ

キーを再マップし、新しい値に変更するには、[ <kbd>キー</kbd> の再マップ] ボタンを使用して [キーボード設定の再マップ] ウィンドウを起動します。 最初に起動したときに、定義済みのマッピングは表示されません。 新しいリマップを追加するには、このボタンを選択する必要があり <kbd>+</kbd> ます。

新しいリマップ行が表示されたら、[キー] 列で ***変更** する出力のキーを選択します。 [マップ先] 列に割り当てられる新しいキー値を選択します。

たとえば <kbd>、を押して</kbd> <kbd>B</kbd>  を表示する場合は、次のようになります。

- キー: "A"
- マップ先: "B"

"A" キーと "B" キーの間でキー位置を交換するには、別の再マップを追加します。

- キー: "B"
- マップ先: "A"

![キーボードマップキーのスクリーンショット](../images/powertoys-keyboard-remap-a-b.png)

## <a name="key-to-shortcut"></a>ショートカットキー

キーをショートカット (キーの組み合わせ) に再マップするには、[マップ先] 列にショートカットキーの組み合わせを入力します。

たとえば、"C" キーを選択し、結果を "Ctrl + V" にする場合は、次のようになります。

- キー: "C"
- マップ先: "Ctrl + V"

> [!NOTE]
> 再マップされたキーが別のショートカットで使用されている場合でも、キーの再マップが維持されます。 たとえば、"Alt + C" というショートカットキーを入力すると、"Alt + Ctrl + V" という結果になります。これは、C キーが "Ctrl + V" に再マップされているためです。

## <a name="remap-shortcuts"></a>ショートカットの再マップ

ショートカットキーの組み合わせ ("Ctrl + v" など) を再マップするには、[ <kbd>ショートカットを</kbd> 再マップする] を選択して [ショートカットの設定] ウィンドウを起動します。

最初に起動したときに、定義済みのマッピングは表示されません。 新しいリマップを追加するには、このボタンを選択する必要があり <kbd>+</kbd> ます。

新しい再マップ行が表示されたら、[ショートカット] 列で出力を _*_変更_*_ するキーを選択します。 [マップ先] 列に割り当てられる新しいショートカット値を選択します。

たとえば、ショートカット<kbd>Ctrl</kbd> + <kbd>C</kbd>は選択したテキストをコピーします。 <kbd>Ctrl</kbd>キーではなく<kbd>Alt</kbd>キーを使用するようにそのショートカットを再マップするには、次のようにします。

- ショートカット: "Ctrl" + "C"
- マップ先: "Alt" + "C"

![キーボード再マップのショートカットスクリーンショット](../images/powertoys-keyboard-remap-shortcut.png)

ショートカットを再マップするときに従う必要があるルールがいくつかあります (これらのルールは、"ショートカット" 列にのみ適用されます)。

- ショートカットは、修飾子キー ( <kbd>Ctrl</kbd>、 <kbd>Shift</kbd>、 <kbd>Alt</kbd>、または<kbd>⊞ Win</kbd> ) で始める必要があります。
- ショートカットは、アクションキー (すべての非修飾キー) で終了する必要があります (A、B、C、1、2、3など)。
- ショートカットを3キーより長くすることはできません  

## <a name="remap-a-shortcut-to-a-single-key"></a>ショートカットを1つのキーに再マップする

ショートカット (キーの組み合わせ) を1回のキー押下に再マップすることができます。

たとえば、ショートカットキー <kbd>⊞ Win</kbd>  +  <kbd>D</kbd> (Windows デスクトップアプリの表示/非表示) を単一のキー押下に置き換えるには、 <kbd>Alt</kbd>キーを押します。

- ショートカット: "⊞ Win" (Windows キー) + "D"
- マップ先: "Alt"

> [!NOTE]
> 再マップされたキーが別のショートカットで使用されている場合でも、ショートカットの再マップが維持されます。 たとえば、ショートカット "Alt" + "Tab" を入力すると、上記の "Alt" キーを再度マップした後、"⊞ Win" + "D" + "Tab" が返されます。

## <a name="app-specific-shortcuts"></a>アプリ固有のショートカット

キーボードマネージャーでは、(Windows 全体ではなく) 特定のアプリのショートカットを再マップすることができます。

たとえば、Outlook 電子メールアプリでは、電子メールを検索するために、ショートカット "Ctrl + E" が既定で設定されています。 代わりに "Ctrl + F" を設定して電子メールを検索する場合は (既定で設定された電子メールを転送するのではなく)、"Outlook" を "ターゲットアプリケーション" として設定して、ショートカットを再マップすることができます。

キーボードマネージャーは、アプリケーション名ではなく、プロセス名を使用してアプリを対象とします。 たとえば、Microsoft Edge は、"Microsoft Edge" (アプリケーション名) ではなく "msedge" (プロセス名) として設定されます。 アプリケーションのプロセス名を検索するには、PowerShell を開き、コマンドを入力するか、コマンドプロンプトを開いてコマンドを `get-process` 入力し `tasklist` ます。 これにより、現在開いているすべてのアプリケーションのプロセス名の一覧が表示されます。 いくつかの一般的なアプリケーションプロセス名の一覧を次に示します。

  | _ *アプリケーション**   | **プロセス名**|
  | ------------------| --------------|
  | Microsoft Edge    |  msedge.exe   |
  | OneNote           |  onenote.exe  |
  | Outlook           |  outlook.exe  |
  | Teams             |  Teams.exe    |
  | Adobe Photoshop   |  Photoshop.exe|
  | エクスプローラー     |  explorer.exe |
  | Spotify 音楽     |  spotify.exe  |
  | Google Chrome     |  chrome.exe   |
  | Excel             |  excel.exe    |
  | Word              |  winword.exe  |
  | PowerPoint        |  powerpnt.exe |

### <a name="keys-that-cannot-be-remapped"></a>再マップできないキー

再マップに許可されていないショートカットキーがいくつかあります。 次に例を示します。

- <kbd>Ctrl</kbd> +<kbd>Alt</kbd> + <kbd>Del</kbd> (interupt コマンド)
- <kbd>⊞ Win</kbd> +<kbd>L</kbd> (コンピューターをロックする)
- 関数キー <kbd>Fn</kbd>を再マップすることはできません (ほとんどの場合)。ただし、 <kbd>F1</kbd> - <kbd>F12</kbd>はマップできます。

## <a name="how-to-select-a-key"></a>キーを選択する方法

再マップするキーまたはショートカットを選択するには、次のようにします。

- [ <kbd>キーの種類</kbd> ] ボタンを使用します。
- ドロップダウンメニューを使用します。

[ <kbd>型キー/ショートカット</kbd> ] ボタンを選択すると、キーボードを使用してキーまたはショートカットを入力できるダイアログが表示されます。 出力に問題がなければ、 <kbd>Enter キー</kbd> を押して続行します。 ダイアログを閉じない場合は、 <kbd>Esc</kbd> ボタンを押したままにします。

ドロップダウンメニューを使用して、キー名を使用して検索できます。追加のドロップダウン値は進行中に表示されます。 ただし、ドロップダウンメニューが開いている間は、型キー機能を使用できません。

## <a name="orphaning-keys"></a>孤立化キー

孤立化は、キーを別のキーにマップし、そのキーにマップされていないことを意味します。

たとえば、キーが-> B から再マップされた場合、キーがキーボードに存在しなくなり、になります。

この問題を解決するには、+ を使用して、の結果にマップされる再マップされた別のキーを作成します。この問題が誤って発生しないように、孤立したキーに対して警告が表示されます。

![Powertoy キーボードマネージャーの孤立したキー](../images/powertoys-keyboard-remap-orphaned.png)

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="i-remapped-the-wrong-keys-how-can-i-stop-it-quickly"></a>間違ったキーを再マップしました。すばやく停止するにはどうすればよいですか。

キーの再マップを機能させるには、Powertoy がバックグラウンドで実行されていて、キーボードマネージャーが有効になっている必要があります。 再マップされたキーを停止するには、Powertoy を閉じるか、または Powertoy の設定でキーボードマネージャーを無効にします。

### <a name="can-i-use-keyboard-manager-at-my-log-in-screen"></a>ログイン画面でキーボードマネージャーを使用できますか。

いいえ。キーボードマネージャーは、Powertoy が実行されていて、[管理者として実行] を含むパスワード画面で動作しない場合にのみ使用できます。

### <a name="do-i-have-to-turn-off-my-computer-for-the-remapping-to-take-effect"></a>再マップが有効になるには、コンピューターの電源をオフにする必要がありますか。

いいえ。再マップは、[ **適用**] を押すとすぐに実行されます。

### <a name="where-are-the-maclinux-profiles"></a>Mac/Linux プロファイルはどこにありますか。

現在、Mac と Linux のプロファイルは含まれていません。

### <a name="will-this-work-on-video-games"></a>これはビデオゲームで動作しますか。

これは、ゲームがキーにアクセスする方法によって異なります。 特定のキーボード Api は、キーボードマネージャーでは動作しません。

### <a name="will-remapping-work-if-i-change-my-input-language"></a>入力言語を変更すると、再マップが機能しますか。

はい、そうです。 ここで <kbd>、を</kbd> 英語 (us) キーボードで <kbd>b</kbd> に再マップした後、言語設定をフランス語に変更すると、フランス語キーボードに「 <kbd>a</kbd> <kbd>」 (英語 (米国</kbd> ) の物理キーボード) を入力すると <kbd>B</kbd>になります。これは、Windows が多言語入力を処理する方法と一致します。

## <a name="troubleshooting"></a>トラブルシューティング

キーまたはショートカットを再マップしようとしたときに問題が発生した場合は、次のいずれかの問題が考えられます。

- **管理者として実行:** 再マップは、そのウィンドウが管理者 (昇格) モードで実行されていて、Powertoy が管理者として実行されていない場合、アプリ/ウィンドウでは機能しません。 管理者として Powertoy を実行してみてください。

- **キーをインターセプトしない:** キーボードマネージャーは、キーを再マップするためにキーボードフックをインターセプトします。 この操作を実行し、キーボードマネージャーに干渉する可能性のあるアプリもあります。 この問題を解決するには、設定にアクセスして、無効にしてから、キーボードマネージャーを再度有効にします。

## <a name="known-issues"></a>既知の問題

- [キャップライトインジケーターが正しく切り替えていません](https://github.com/microsoft/PowerToys/issues/1692)

- [F・ Yzones とショートカットガイドで動作しない再マップ](https://github.com/microsoft/PowerToys/issues/3079)

- [Win、Ctrl、Alt、Shift などのキーを再マッピングするとジェスチャが中断し、特殊なボタンが表示されることがある](https://github.com/microsoft/PowerToys/issues/3703)

[Open keyboard manager の問題](https://github.com/microsoft/PowerToys/issues?q=is%3Aopen+is%3Aissue+label%3A%22Product-Keyboard+Shortcut+Manager%22)の一覧を参照してください。