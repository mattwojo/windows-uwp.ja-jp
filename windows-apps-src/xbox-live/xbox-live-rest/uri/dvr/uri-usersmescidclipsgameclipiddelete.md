---
title: DELETE (/users/me/scids/{scid}/clips/{gameClipId})
assetID: 486fac60-6884-2e3f-9ef8-8de5da0ad8af
permalink: en-us/docs/xboxlive/rest/uri-usersmescidclipsgameclipiddelete.html
author: KevinAsgari
description: " DELETE (/users/me/scids/{scid}/clips/{gameClipId})"
ms.author: kevinasg
ms.date: 20-12-2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Xbox Live, Xbox, ゲーム, UWP, Windows 10, Xbox One
ms.localizationpriority: medium
ms.openlocfilehash: a68d765cfdec81da064b0522ea2ff9a4be12bafb
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "4155042"
---
# <a name="delete-usersmescidsscidclipsgameclipid"></a>DELETE (/users/me/scids/{scid}/clips/{gameClipId})
これらの Uri のドメインは、ゲーム クリップを削除`gameclipsmetadata.xboxlive.com`と`gameclipstransfer.xboxlive.com`問題の URI の機能に応じて、します。
 
  * [注釈](#ID4EX)
  * [URI パラメーター](#ID4ECB)
  * [Authorization](#ID4ENB)
  * [必要な要求ヘッダー](#ID4EYB)
  * [省略可能な要求ヘッダー](#ID4EEE)
  * [要求本文](#ID4ENF)
  * [HTTP ステータス コード](#ID4EYF)
  * [必要な応答ヘッダー](#ID4EIAAC)
  * [省略可能な応答ヘッダー](#ID4E2CAC)
  * [応答本文](#ID4E2DAC)
 
<a id="ID4EX"></a>

 
## <a name="remarks"></a>注釈
 
GameClips サービスからユーザーのビデオを削除するためのメカニズムを提供します。 削除、時にすべてのメタデータと実際のビデオ アセット (生成されると元) は、システムから削除されます。 これは、永続的な操作です。 

> [!NOTE] 
> 指定された所有者 ID は、正常に削除要求の承認トークンで呼び出し元と一致する必要があります。 


  
<a id="ID4ECB"></a>

 
## <a name="uri-parameters"></a>URI パラメーター
 
| パラメーター| 型| 説明| 
| --- | --- | --- | --- | 
| scid| string| アクセスされているリソースのサービス構成 ID。 認証されたユーザーの SCID に一致する必要があります。| 
| gameClipId| string| ゲーム クリップだったにアクセスしているリソースの ID です。| 
  
<a id="ID4ENB"></a>

 
## <a name="authorization"></a>Authorization
 
Xuid クレームだけでは、このメソッドに必要です。
  
<a id="ID4EYB"></a>

 
## <a name="required-request-headers"></a>必要な要求ヘッダー
 
| ヘッダー| 型| 説明| 
| --- | --- | --- | --- | --- | --- | --- | 
| Authorization| string| HTTP 認証の資格情報を認証します。 値の例: <b>Xauth =&lt;authtoken ></b>| 
| X RequestedServiceVersion| string| この要求を送信する必要があります、Xbox LIVE サービスの名前/数をビルドします。 要求は、ヘッダー、要求に認証トークンなどの有効性を確認した後、そのサービスにのみルーティングされます。例: 1、vnext します。| 
| Content-Type| string| 応答本文の MIME タイプ。 例:<b>アプリケーション/json</b>します。| 
| Accept| string| コンテンツの種類の許容値です。 例:<b>アプリケーション/json</b>します。| 
| キャッシュ コントロール| string| キャッシュ動作を指定するていねい要求します。| 
  
<a id="ID4EEE"></a>

 
## <a name="optional-request-headers"></a>省略可能な要求ヘッダー
 
| ヘッダー| 型| 説明| 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| Accept-Encoding| string| 受け入れ可能な圧縮エンコードします。 値の例: gzip、圧縮を識別します。| 
| ETag| string| キャッシュの最適化のために使用します。 値の例:"686897696a7c876b7e"です。| 
  
<a id="ID4ENF"></a>

 
## <a name="request-body"></a>要求本文
 
この要求の本文には、オブジェクトは送信されません。
  
<a id="ID4EYF"></a>

 
## <a name="http-status-codes"></a>HTTP ステータス コード
 
サービスでは、このリソースには、この方法で行った要求に対する応答としてでは、このセクションで、状態コードのいずれかを返します。 Xbox Live サービスで使用される標準の HTTP ステータス コードの一覧は、[標準の HTTP ステータス コード](../../additional/httpstatuscodes.md)を参照してください。
 
| コード| 理由フレーズ| 説明| 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| 204| OK| クリップが正常に削除します。| 
| 401| 権限がありません| 要求の認証トークンの形式で問題があります。| 
| 403| Forbidden| 一部の必須の要求は含まれていません。| 
| 404| Not Found します。| URL に指定されているクリップが存在しませんでした (または 2 つ目の時間を削除されました)。| 
| 503| 許容できません。| サービスまたはダウン ストリームの依存関係はいくつかダウンしています。 標準のバックオフ動作を指定して再試行します。| 
  
<a id="ID4EIAAC"></a>

 
## <a name="required-response-headers"></a>必要な応答ヘッダー
 
| ヘッダー| 型| 説明| 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| X RequestedServiceVersion| string| この要求を送信する必要があります、Xbox LIVE サービスの名前/数をビルドします。 要求は、ヘッダー、要求に認証トークンなどの有効性を確認した後、そのサービスにのみルーティングされます。例: 1、vnext します。| 
| Content-Type| string| 応答本文の MIME タイプ。 例:<b>アプリケーション/json</b>します。| 
| キャッシュ コントロール| string| キャッシュ動作を指定するていねい要求します。| 
| Accept| string| コンテンツの種類の許容値です。 例:<b>アプリケーション/json</b>します。| 
| Retry-after| string| クライアントが利用できないサーバーの場合、後で再試行するように指示します。| 
| 異なる| string| 下位のプロキシ応答をキャッシュする方法を指示します。| 
  
<a id="ID4E2CAC"></a>

 
## <a name="optional-response-headers"></a>省略可能な応答ヘッダー
 
| ヘッダー| 型| 説明| 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| Etag| string| キャッシュの最適化のために使用します。 例:"686897696a7c876b7e"です。| 
  
<a id="ID4E2DAC"></a>

 
## <a name="response-body"></a>応答本文
 
サービスが成功すると、204 (No content) の HTTP ステータス コードで応答します。 しようとして、同じオブジェクトを削除するか、存在しないオブジェクトに 404 が返されます。
 
エラー発生時**ServiceErrorResponse**オブジェクトが返されます。
  
<a id="ID4EJEAC"></a>

 
## <a name="see-also"></a>関連項目
 
<a id="ID4ELEAC"></a>

 
##### <a name="parent"></a>Parent 

[/users/me/scids/{scid}/clips/{gameClipId}](uri-usersmescidclipsgameclipid.md)

   