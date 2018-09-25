---
title: /users/{ownerId}/people/mute
assetID: efb929d8-79a7-83f0-c348-c92ced42bc05
permalink: en-us/docs/xboxlive/rest/uri-privacyusersowneridpeoplemute.html
author: KevinAsgari
description: " /users/{ownerId}/people/mute"
ms.author: kevinasg
ms.date: 20-12-2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Xbox Live, Xbox, ゲーム, UWP, Windows 10, Xbox One
ms.localizationpriority: medium
ms.openlocfilehash: a5de74be5e82fde007d6680eaf4c9e5a543afc64
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "4156122"
---
# <a name="usersowneridpeoplemute"></a>/users/{ownerId}/people/mute
ユーザーのミュート リストにアクセスします。

  * [URI パラメーター](#ID4EQ)

<a id="ID4EQ"></a>


## <a name="uri-parameters"></a>URI パラメーター

| パラメーター| 型| 説明|
| --- | --- | --- |
| ownerId| string| 必須。 そのリソースにアクセスしているユーザーの識別子です。 設定可能な値は"me" <code>xuid({xuid})</code>、または gt({gamertag}) します。 認証されたユーザーである必要があります。 値の例: <code>xuid(2603643534573581)</code>、<code>gt(SomeGamertag)</code>します。 最大サイズ: なし。 |

<a id="ID4ETB"></a>


## <a name="valid-methods"></a>有効なメソッド

[GET (/users/{ownerId}/people/mute)](uri-privacyusersowneridpeoplemuteget.md)

&nbsp;&nbsp;ユーザーのミュートの一覧を取得します。

<a id="ID4E4B"></a>


## <a name="see-also"></a>関連項目

<a id="ID4E6B"></a>


##### <a name="parent"></a>Parent

[プライバシー URI](atoc-reference-privacyv2.md)