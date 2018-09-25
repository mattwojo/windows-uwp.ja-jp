---
title: Achievement (JSON)
assetID: d3b52f66-ddc7-e676-b419-82209caf71d6
permalink: en-us/docs/xboxlive/rest/json-achievementv2.html
author: KevinAsgari
description: " Achievement (JSON)"
ms.author: kevinasg
ms.date: 20-12-2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Xbox Live, Xbox, ゲーム, UWP, Windows 10, Xbox One
ms.localizationpriority: medium
ms.openlocfilehash: e82306119e428dd9279e26d1497d44b371b9587e
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "4149982"
---
# <a name="achievement-json"></a>Achievement (JSON)
実績オブジェクト (バージョン 2)。
<a id="ID4EN"></a>


## <a name="achievement"></a>実績

実績のオブジェクトでは、次の仕様があります。 すべてのメンバーが必要です。

| メンバー| 種類| 説明|
| --- | --- | --- |
| id| string| リソース識別子です。|
| serviceConfigId| string| このリソースの SCID です。 この実績の関連するタイトルを識別します。 |
| name| string| ローカライズされた実績の名前です。|
| titleAssociations| [TitleAssociation](json-titleassociation.md)の配列| TitleAssociation の配列です。|
| progressState| **ProgressState**列挙| 進行状況の状態。 <ul><li>無効 (0): 実績の進行状況が不明な状態です。</li><li>(1) を実現: 実績がロック解除されました。</li><li>inProgress (2): 実績がロックされているが、ユーザーは、ロック解除に向けた進行状況を行ったします。</li><li>未開始 (3): 実績がロックされているし、ユーザーがロック解除に向けた任意の進行状況がまだ行われています。</li></ul> | 
| 進行状況| [進行状況](json-progression.md)| 実績内のユーザーの進行状況です。|
| mediaAssets| [MediaAsset](json-mediaasset.md)の配列| 画像の Id など、実績に関連付けられているメディア アセット。 |
| プラットフォーム| string| プラットフォーム、実績を獲得するとします。|
| isSecret| ブール値| 実績が秘密かどうか。|
| description| string| 実績のロックを解除するときの説明です。|
| lockedDescription| string| 実績がロック解除する前に説明します。|
| productId| string| ProductId 実績でリリースされました。|
| achievementType| **AchievementType**列挙| 実績 (しないと同じ以前の従来の実績の種類) の種類。 <ul><li>無効 (0): 不明なおよびサポートされていない実績型です。</li><li>永続的な (1): 実績を終了日がないと、いつでもロックできます。</li><li>チャレンジ (2): を間になる場合がロックされている特定の時間枠を持つ実績します。</li></ul> |
| participationType| **ParticipationType**列挙| 実績の参加の種類。 有効な値は、個人またはグループはします。|
| 時間| 時間| 時に、実績がロックを解除する時間枠です。 チャレンジのみサポートされます。|
| リワード| [リワード](json-reward.md)の配列| リワードのロックを解除するときの原因のコレクションです。|
| estimatedTime| TimeSpan| 推定時間を獲得実績になります。|
| deeplink| string| タイトルに deeplink します。|
| isRevoked| ブール値| かどうかの実施によって、実績が失効します。|

<a id="ID4EIAAC"></a>


## <a name="sample-json-syntax"></a>JSON 構文の例


```json
{
        "id":"3",
        "serviceConfigId":"b5dd9daf-0000-0000-0000-000000000000",
        "name":"Default NameString for Microsoft Achievements Sample Achievement 3",
        "titleAssociations":
        [{
                "name":"Microsoft Achievements Sample",
                "id":3051199919,
                "version":"abc"
        }],
        "progressState":"Achieved",
        "progression":
        {
          "requirements":
          [{
            "id":"12345678-1234-1234-1234-123456789012",
            "current":null,
            "target":"100"
          }],
          "timeUnlocked":"2013-01-17T03:19:00.3087016Z",
        },
        "mediaAssets":
        [{
                "name":"Icon Name",
                "type":"Icon",
                "url":"http://www.xbox.com"
        }],
        "platform":"D",
        "isSecret":true,
        "description":"Default DescriptionString for Microsoft Achievements Sample Achievement 3",
        "lockedDescription":"Default UnachievedString for Microsoft Achievements Sample Achievement 3",
        "productId":"12345678-1234-1234-1234-123456789012",
        "achievementType":"Challenge",
        "participationType":"Individual",
        "timeWindow":
        {
                "startDate":"2013-02-01T00:00:00Z",
                "endDate":"2100-07-01T00:00:00Z"
        },
        "rewards":
        [{
                "name":null,
                "description":null,
                "value":"10",
                "type":"Gamerscore",
                "valueType":"Int"
        },
        {
                "name":"Default Name for InAppReward for Microsoft Achievements Sample Achievement 3",
                "description":"Default Description for InAppReward for Microsoft Achievements Sample Achievement 3",
                "value":"1",
                "type":"InApp",
                "valueType":"String"
        }],
        "estimatedTime":"06:12:14",
        "deeplink":"aWFtYWRlZXBsaW5r",
        "isRevoked":false
    }

```


<a id="ID4ERAAC"></a>


## <a name="see-also"></a>関連項目

<a id="ID4ETAAC"></a>


##### <a name="parent"></a>Parent

[JavaScript Object Notation (JSON) オブジェクト リファレンス](atoc-xboxlivews-reference-json.md)