---
author: mcleanbyron
ms.assetid: 37F2C162-4910-4336-BEED-8536C88DCA65
description: Windows デベロッパー センター アカウントに登録されているアプリのパッケージ フライトを管理するには、Microsoft Store 申請 API の以下のメソッドを使います。
title: パッケージ フライトの管理
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Microsoft Store 申請 API, フライト
ms.localizationpriority: medium
ms.openlocfilehash: 7b5e3c100ece6ec79abad0efbf4797b0102959cb
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2018
ms.locfileid: "1661872"
---
# <a name="manage-package-flights"></a>パッケージ フライトの管理

アプリのパッケージ フライトを管理するには、Microsoft Store 申請 API の以下のメソッドを使います。 Microsoft Store 申請 API の概要については、「[Microsoft Store サービスを使用した申請の作成と管理](create-and-manage-submissions-using-windows-store-services.md)」をご覧ください。この API を使用するための前提条件などの情報があります。

以下のメソッドは、パッケージ フライトの取得、作成、または削除にしか使用できません。 パッケージ フライトの申請を作成するには、「[パッケージ フライトの申請の管理](manage-flight-submissions.md)」のメソッドをご覧ください。

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">メソッド</th>
<th align="left">URI</th>
<th align="left">説明</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">GET</td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}</td>
<td align="left"><a href="get-a-flight.md">パッケージ フライトの取得</a></td>
</tr>
<tr>
<td align="left">POST</td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights</td>
<td align="left"><a href="create-a-flight.md">パッケージ フライトの作成</a></td>
</tr>
<tr>
<td align="left">DELETE</td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}</td>
<td align="left"><a href="delete-a-flight.md">パッケージ フライトの削除</a></td>
</tr>
</tbody>
</table>

## <a name="prerequisites"></a>前提条件

Microsoft Store 申請 API に関するすべての[前提条件](create-and-manage-submissions-using-windows-store-services.md#prerequisites)がまだ満たされていない場合は、ここに記載されているメソッドを使用する前に前提条件を整えてください。

## <a name="related-topics"></a>関連トピック

* [Microsoft Store サービスを使用した申請の作成と管理](create-and-manage-submissions-using-windows-store-services.md)
* [パッケージ フライトの申請の管理](manage-flight-submissions.md)