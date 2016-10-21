---
author: mcleanbyron
ms.assetid: AD80F9B3-CED0-40BD-A199-AB81CDAE466C
description: "Windows ストア申請 API のこのメソッドを使用して、Windows デベロッパー センター アカウントに登録されているアプリのパッケージ フライトを削除します。"
title: "Windows ストア申請 API を使用したパッケージ フライトの削除"
translationtype: Human Translation
ms.sourcegitcommit: 5f975d0a99539292e1ce91ca09dbd5fac11c4a49
ms.openlocfilehash: eae25f9a19523b928e30baaf0ffe0eec6e779ed2

---

# Windows ストア申請 API を使用したパッケージ フライトの削除




Windows ストア申請 API のこのメソッドを使用して、Windows デベロッパー センター アカウントに登録されているアプリのパッケージ フライトを削除します。


## 前提条件

このメソッドを使うには、最初に次の作業を行う必要があります。

* Windows ストア申請 API に関するすべての[前提条件](create-and-manage-submissions-using-windows-store-services.md#prerequisites)を満たします (前提条件がまだ満たされていない場合)。
* このメソッドの要求ヘッダーで使う [Azure AD アクセス トークンを取得](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token)します。 アクセス トークンを取得した後、アクセス トークンを使用できるのは、その有効期限が切れるまでの 60 分間です。 トークンの有効期限が切れたら新しいトークンを取得できます。

>**注:**&nbsp;&nbsp;このメソッドは、Windows ストア申請 API を使用するアクセス許可が与えられた Windows デベロッパー センター アカウントにのみ使用できます。 すべてのアカウントでこのアクセス許可が有効になっているとは限りません。

## 要求

このメソッドの構文は次のとおりです。 ヘッダーと要求本文の使用例と説明については、次のセクションをご覧ください。

| メソッド | 要求 URI                                                      |
|--------|------------------------------------------------------------------|
| DELETE    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}``` |

<span/>
 

### 要求ヘッダー

| ヘッダー        | 型   | 説明                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Authorization | string | 必須。 **Bearer** &lt;*token*&gt; という形式の Azure AD アクセス トークン。 |

<span/>

### 要求パラメーター

| 名前        | 型   | 説明                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| applicationId | string | 必須。 削除するパッケージ フライトが含まれるアプリのストア ID。 アプリのストア ID は、デベロッパー センター ダッシュボードで確認できます。  |
| flightId | string | 必須。 削除するパッケージ フライトの ID。 この ID は、[パッケージ フライトの作成](create-a-flight.md)要求と[アプリのパッケージ フライトの取得](get-flights-for-an-app.md)要求の応答データに含まれており、デベロッパー センター ダッシュボードで確認できます。  |

<span/>

### 要求本文

このメソッドでは要求本文を指定しないでください。

<span/>

### 要求の例

次の例は、新しいパッケージ フライトを削除する方法を示しています。

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd HTTP/1.1
Authorization: Bearer <your access token>
```

## 応答

成功した場合、このメソッドは空の応答の本文を返します。

## エラー コード

要求を正常に完了できない場合、次の HTTP エラー コードのいずれかが応答に含まれます。

| エラー コード |  説明                                                                                                                                                                           |
|--------|------------------|
| 400  | 要求パラメーターが有効ではありません。 |
| 404  | 指定されたパッケージ フライトは見つかりませんでした。  |
| 409  | 指定したパッケージ フライトは見つかりましたが、現在の状態で削除できなかったか、[Windows ストア申請 API で現在サポートされていない](create-and-manage-submissions-using-windows-store-services.md#not_supported)デベロッパー センター ダッシュボード機能がアプリで使用されています。 |   

<span/>

## 関連トピック

* [Windows ストア サービスを使用した申請の作成と管理](create-and-manage-submissions-using-windows-store-services.md)
* [パッケージ フライトの作成](create-a-flight.md)
* [パッケージ フライトの取得](get-a-flight.md)



<!--HONumber=Aug16_HO5-->

