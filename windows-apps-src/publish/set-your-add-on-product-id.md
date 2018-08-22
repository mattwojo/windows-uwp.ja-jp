---
author: jnHs
Description: When you create a new add-on in the Windows Dev Center dashboard, you need to specify a product type and assign it a product ID.
title: アドオンの製品の種類と製品 ID を設定する
ms.assetid: 59497B0F-82F0-4CEE-B628-040EF9ED8D3D
ms.author: wdg-dev-content
ms.date: 01/12/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, アドオン, iap, 永続的, コンシューマブル, サブスクリプション, 製品の種類, 製品 id, アプリ内購入, アプリ内製品
ms.localizationpriority: medium
ms.openlocfilehash: 0673048fc9a1ed8fb7c439607ebc4197039699e9
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "2800499"
---
# <a name="set-your-add-on-product-type-and-product-id"></a>アドオンの製品の種類と製品 ID を設定する

アドオンは、ダッシュボードで作成済みのアプリと関連付けている必要があります (アプリが未申請であっても同様)。 アプリの **[概要]** ページまたは **[アドオン]** ページに **[新しいアドオンを作成する]** ボタンがあります。

**[新しいアドオンを作成する]** を選ぶと、製品の種類を指定し、アドオンに製品 ID を割り当てるように求められます。

## <a name="product-type"></a>製品の種類

まず、提供するアドオンの種類を指定する必要があります。 この選択内容は、ユーザーがアドオンをどのように使うことができるかを示しています。

> [!NOTE]
> このページを保存してアドオンを作成した後は、製品の種類を変更することはできません。 間違った製品の種類を選択した場合は、いつでも進行中のアドオンの申請を削除して、新しいアドオンを作成し直すことができます。

<span id="durable" />

### <a name="durable"></a>永続的

通常 1 回しか購入しないタイプのアドオンの場合は、製品の種類に **[永続的]** を選びます。 このタイプのアドオンは多くの場合、アプリの追加機能のロックを解除するために使います。

永続的なアドオンの **[製品の有効期限]** の既定値は、**[無期限]** です。つまり、アドオンの期限は切れません。 **[製品の有効期限]** は、アドオンの申請プロセスの[プロパティ](enter-add-on-properties.md)の手順で、別の期限に変更できます。 変更すると、アドオンは指定した期限 (1 ～ 365 日) を過ぎると使用できなくなります。その場合は、アドオンの期限切れ後に再びアドオンを購入可能にすることもできます。

<span id="consumable" />

### <a name="consumable"></a>コンシューマブル

購入して使用 (消費) した後に、再び購入できるアドオンの場合は、**コンシューマブル**な製品の種類のいずれかを選びます。 コンシューマブル アドオンは多くの場合、一定金額を購入してユーザーが使い切ることができるゲーム内通貨 (ゴールド、コインなど) などに使います。 詳しくは、「[コンシューマブルなアドオン購入の有効化](../monetize/enable-consumable-add-on-purchases.md)」をご覧ください。

コンシューマブルなアドオンには、次の 2 種類があります。
- **開発者により管理されるコンシューマブル**: 残高とフルフィルメントは、アプリ内で管理する必要があります。 すべての OS バージョンでサポートされます。
- **ストアで管理されるコンシューマブル:** 残高は、Windows 10 バージョン 1607 以降を実行している顧客の全デバイスを対象に、Microsoft によって追跡されます。これ以前の OS バージョンではサポートされません。 このオプションを使うには、Windows 10 SDK バージョン 14393 以降を使用して親製品をコンパイルする必要があります。 また、親製品が公開されるまで、ストアで管理されるコンシューマブル アドオンをストアに申請することはできません (ただし、ダッシュ ボードで申請を作成して作業を開始することは可能です)。 申請の**プロパティ**のステップで、ストアで管理されるコンシューマブル アドオンの数量を入力する必要があります。

<span id="subscription" />

### <a name="subscription"></a>サブスクリプション

アドオンの顧客に繰り返し課金する場合は、**[サブスクリプション]** を選びます。

サブスクリプション アドオンは一度購入すると、その後アドオンを使い続けるための料金が定期的にユーザーに課金されます。 ユーザーはいつでもサブスクリプションをキャンセルして、それ以降の課金を取り消すことができます。 サブスクリプション期間と、無料試用版を提供するかどうかを申請の**プロパティ**のステップで指定する必要があります。

サブスクリプション アドオンは、Windows 10 バージョン 1607 以降を実行しているユーザーのみが対象です。 親アプリは Windows 10 SDK バージョン 14393 以降を使ってコンパイルし、**Windows.ApplicationModel.Store** 名前空間ではなく、**Windows.Services.Store** 名前空間のアプリ内購入 API を使う必要があります。 詳しくは、「[アプリのサブスクリプション アドオンの有効化](../monetize/enable-subscription-add-ons-for-your-app.md)」をご覧ください。

親製品を公開しないと、サブスクリプション アドオンを Microsoft Store で公開することはできません (ただし、ダッシュボードで申請を作成して作業を開始することは可能です)。

## <a name="product-id"></a>製品 ID

どの製品の種類を選んでも、アドオンに割り当てる一意の製品 ID を入力する必要があります。 この名前はダッシュボードでアドオンを識別するために使われます。また、この ID は、[コード内でアドオンを参照](../monetize/in-app-purchases-and-trials.md#how-to-use-product-ids-for-add-ons-in-your-code)するためにも使うことができます。

次に示しているのは、製品 ID を選ぶときの留意点です。

-   この製品 ID はお客様には表示されません  (後で、お客様に表示される[タイトルと説明](create-add-on-descriptions.md)を入力できます)。
-   このアドオンの製品 ID はアプリの公開後に変更することも削除することもできません。
-   この製品 ID の長さは 100 文字以内にする必要があります。
-   この製品 ID に **&lt; &gt; \* % & : \\ ? + ,** のいずれの文字も含めることはできません。
-   すべての OS バージョンに対応したアドオンを提供するには、英数字、ピリオド、アンダースコアのみを使う必要があります。 その他の種類の文字を使った場合、Windows Phone 8.1 以前を実行しているお客様はそのアドオンを購入できなくなります。
-   この製品 ID は Microsoft Store では一意である必要はありませんが、開発者アカウントには一意である必要があります。
 