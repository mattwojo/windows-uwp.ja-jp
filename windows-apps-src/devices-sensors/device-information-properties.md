---
author: muhsinking
ms.assetid: 4A4C2802-E674-4C04-8A6D-D7C1BBF1BD20
title: デバイス情報プロパティ
description: デバイスにはそれぞれ DeviceInformation プロパティが関連付けられており、特定の情報が必要な場合やデバイス セレクターを作成する場合に使うことができます。
ms.author: mukin
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c8fe51fd98f70e6f920a7421a9932e69bba11377
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "959248"
---
# <a name="device-information-properties"></a>デバイス情報プロパティ



**重要な API**

- [**Windows.Devices.Enumeration**](https://docs.microsoft.com/en-us/uwp/api/Windows.Devices.Enumeration)

デバイスにはそれぞれ [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) プロパティが関連付けられており、特定の情報が必要な場合やデバイス セレクターを作成する場合に使うことができます。 これらのプロパティを AQS フィルターとして指定して、列挙するデバイスを絞り込むことにより、指定した特徴を持つデバイスを見つけることができます。 また、各デバイスについて返される情報を指定するために使うこともできます。 これにより、アプリケーションに返されるデバイス情報を指定できます。

デバイス セレクターでの [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) プロパティの使い方について詳しくは、「[デバイス セレクターのビルド](build-a-device-selector.md)」をご覧ください。 このトピックでは、情報プロパティを要求する方法や、一般的なプロパティとその目的を確認できます。

[**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) オブジェクトは、ID ([**DeviceInformation.Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id))、種類 ([**DeviceInformation.Kind**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.kind.aspx))、プロパティ バック ([**DeviceInformation.Properties**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.properties.aspx)) で構成されています。 **DeviceInformation** オブジェクトのその他のプロパティはすべて **Properties** プロパティ バッグから派生します。 たとえば、[**Name**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.name) は **System.ItemNameDisplay** から派生します。 つまり、このプロパティ バッグには、その他のプロパティを決定するために必要な情報が常に含まれています。

## <a name="requesting-properties"></a>プロパティの要求

[**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) オブジェクトには、[**Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id) や [**Kind**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.kind.aspx) などの基本的なプロパティがいくつか用意されていますが、ほとんどのプロパティは、[**Properties**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.properties.aspx) の下にあるプロパティ バッグに格納されています。 このため、プロパティ バッグには、プロパティ バッグからプロパティを提供するのに使われるプロパティが含まれています。 たとえば、[System.ItemNameDisplay](https://msdn.microsoft.com/library/windows/desktop/Bb760770) を使うと、[**Name**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.name) プロパティを提供できます。 これは、わかりやすい名前を持つ一般的な既知のプロパティの一例です。 このように、Windows はわかりやすい名前を付け、プロパティの照会を簡単にしています。

要求できるプロパティは、わかりやすい名前を持つ一般的なプロパティだけではありません。 基になる GUID とプロパティ ID (PID) を指定することで、個別のデバイスまたはドライバーによって提供されたカスタム プロパティも含め、利用可能なすべてのプロパティを要求できます。 カスタム プロパティの指定形式は「`{GUID} PID`」です。 例:"`{744e3bed-3684-4e16-9f8a-07953a8bf2ab} 7`"します。 

> [!Note]
> デバイス ドライバーのデバイス プロパティ キー ヘッダー ファイルのプロパティの Guid の一覧が表示されます。

一部のプロパティは、[**DeviceInformationKind**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformationkind) のすべてのオブジェクトで共通していますが、ほとんどのプロパティは特定の種類に固有です。 以下のセクションでは、**DeviceInformationKind** ごとに並べ替えた共通プロパティの一部を紹介しています。 さまざまな種類の関係性について詳しくは、「**DeviceInformationKind**」をご覧ください。

## <a name="deviceinterface-properties"></a>DeviceInterface プロパティ

**DeviceInterface** は既定で最も一般的な [**DeviceInformationKind**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformationkind) オブジェクトで、アプリのシナリオに使われます。 これは、デバイス API が別の特定の **DeviceInformationKind** を示さない限り使用すべきオブジェクトの種類です。

| 名前                                  | 種類    | 説明                                                                                                                                                                                                                                                                                                                                                                                               |
|---------------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **System.Devices.ContainerId**        | GUID    | この **DeviceInterface** を含む **Device** が含まれている **DeviceInformationKind.DeviceContainer** の ID。 この値を **DeviceInformationKind.DeviceContainer** と共に [**CreateFromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.createfromidasync) に渡すと、適切なコンテナーを見つけることができます。                                                                                    |
| **System.Devices.InterfaceClassGuid** | GUID    | このインターフェイスが表すインターフェイス クラス GUID。                                                                                                                                                                                                                                                                                                                                                       |
| **System.Devices.DeviceInstanceId**   | String  | 親 **DeviceInformationKind.Device** の ID。 この値を **DeviceInformationKind.Device** と共に [**CreateFromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.createfromidasync) に渡すと、適切なデバイスを見つけることができます。                                                                                                                                                                   |
| **System.Devices.InterfaceEnabled**   | Boolean | インターフェイスが有効かどうかを示します。 [**DeviceInformation.IsEnabled**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.isenabled) はこのプロパティから派生します。                                                                                                                                                                                                                                                           |
| **System.Devices.GlyphIcon**          | String  | グリフのアイコン パス。                                                                                                                                                                                                                                                                                                                                                                                  |
| **System.Devices.IsDefault**          | Boolean | これが **System.Devices.InterfaceClassGuid** の既定のデバイスかどうかを示します。 これは主にプリンターに使われます。 オーディオの既定値が複数存在するため、これはオーディオでは機能しません。 オーディオの既定値を取得するには、[**GetDefaultAudioRenderId**](https://msdn.microsoft.com/library/windows/apps/BR226819) または [**GetDefaultAudioCaptureId**](https://msdn.microsoft.com/library/windows/apps/BR226818) を使います。 |
| **System.Devices.Icon**               | String  | アイコンのパス。                                                                                                                                                                                                                                                                                                                                                                                                |
| **System.ItemNameDisplay**            | String  | デバイス オブジェクトに最適な表示名。                                                                                                                                                                                                                                                                                                                                                              |

 

## <a name="device-properties"></a>デバイスのプロパティ

| 名前                                  | 種類       | 説明                                                                                                                                                                                                                                                                              |
|---------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **System.Devices.ClassGuid**          | GUID       | デバイスのインストール時に使われるデバイス クラス。 詳しくは、「[デバイス セットアップ クラス](https://msdn.microsoft.com/library/windows/hardware/Ff541509)」をご覧ください。                                                                                                                                                            |
| **System.Devices.CompatibleIds**      | String\[\] | デバイスの互換性 ID。 Windows がデバイスにインストールする最適なドライバーを決める場合に、これらが使われます。 詳しくは、「[互換性 ID](https://msdn.microsoft.com/library/windows/hardware/Ff539950)」をご覧ください。                                                                                                |
| **System.Devices.ContainerId**        | GUID       | このデバイスを含む **DeviceInformationKind.DeviceContainer** の ID。 この値を **DeviceInformationKind.DeviceContainer** と共に [**CreateFromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.createfromidasync) に渡すと、適切なコンテナーを見つけることができます。          |
| **System.Devices.DeviceCapabilities** | UInt32     | **CfgMgr32.h** で定義された CM\_DEVCAP\_X 機能フラグのビット単位の OR。 詳しくは、「[**DEVPKEY\_Device\_Capabilities**](https://msdn.microsoft.com/library/windows/hardware/Ff542373)」をご覧ください。                                                                                             |
| **System.Devices.DeviceHasProblem**   | Boolean    | デバイスには現在問題があり、正しく機能していないと考えられます。 ドライバーが古いか、見つからないか、無効である可能性があります。                                                                                                                                                |
| **System.Devices.DeviceInstanceId**   | String     | デバイスの ID。 これは [**DeviceInformation.Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id) の値でもあります。                                                                                                                                                                       |
| **System.Devices.DeviceManufacturer** | String     | デバイスの製造元。                                                                                                                                                                                                                                                          |
| **System.Devices.HardwareIds**        | String\[\] | デバイスのハードウェア ID。 インストールに最適なドライバーを決める場合に、Windows がこれらの ID を使います。 デバイスのベンダーは、このプロパティを使ってアプリからデバイスを識別します。 詳しくは、「[ハードウェア ID](https://msdn.microsoft.com/library/windows/hardware/Ff546152)」をご覧ください。                                         |
| **System.Devices.Parent**             | String     | 親デバイスの [**DeviceInformation.Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id)。 これは接続親であり、**DeviceContainer** 親ではありません。                                                                                                                                 |
| **System.Devices.Present**            | Boolean    | デバイスが現在存在し、利用できるかどうかを示します。                                                                                                                                                                                                                         |
| **System.ItemNameDisplay**            | String     | このデバイス オブジェクトに最適な表示名。 この場合は、これがユーザーにとって最適な名前であるとは限りません。 関連付けられている **DeviceContainer** または **DeviceInterface** の **System.ItemNameDisplay** を参照すると、もっとわかりやすい名前が見つかる可能性があります。 |

 

## <a name="devicecontainer-properties"></a>DeviceContainer プロパティ

| 名前                              | 種類       | 説明                                                                                                                                                        |
|-----------------------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **System.Devices.Category**       | String\[\] | デバイスが属しているカテゴリの説明の一覧。 この一覧で提供されるカテゴリは単数形です。 たとえば、「Display」、「Phone」、または「Audio device」です。  |
| **System.Devices.CategoryIds**    | String\[\] | このデバイスが属しているカテゴリの一覧が含まれています。 たとえば、**Audio.Headphone**、**Display.Monitor**、または **Input.Gaming** です。                                  |
| **System.Devices.CategoryPlural** | String\[\] | デバイスが属しているカテゴリの説明の一覧。 この一覧で提供されるカテゴリは複数形です。 たとえば、「Displays」、「Phones」、または「Audio devices」です。 |
| **System.Devices.CompatibleIds**  | String\[\] | すべての **DeviceInformationKind.Device** 子オブジェクトの互換性 ID のコレクション。                                                                       |
| **System.Devices.Connected**      | Boolean    | デバイスが現在システムに接続されているかどうかを示します。                                                                                          |
| **System.Devices.GlyphIcon**      | String     | グリフのアイコン パス。                                                                                                                                           |
| **System.Devices.HardwareIds**    | String\[\] | すべての **DeviceInformationKind.Device** 子オブジェクトのハードウェア ID のコレクション。                                                                         |
| **System.Devices.Icon**           | String     | アイコンのパス。                                                                                                                                                         |
| **System.Devices.LocalMachine**   | Boolean    | この **DeviceContainer** がシステム自体を示す場合は **true**、デバイスがシステム外部にある場合は **false**。                                              |
| **System.Devices.Manufacturer**   | String     | デバイスの製造元。                                                                                                                                    |
| **System.Devices.ModelName**      | String     | デバイス コンテナーのモデル名。                                                                                                                                |
| **System.Devices.Paired**         | Boolean    | **DeviceInformationKind.Device** 子オブジェクトのどれかが、現在システムとペアリングされたワイヤレス デバイスまたはネットワーク デバイスであるかどうかを示します。             |
| **System.ItemNameDisplay**        | String     | このデバイスに最適な表示名。                                                                                                                             |

 

## <a name="deviceinterfaceclass-properties"></a>DeviceInterfaceClass プロパティ

| 名前                       | 種類   | 説明                            |
|----------------------------|--------|----------------------------------------|
| **System.ItemNameDisplay** | String | このデバイスに最適な表示名。 |

 

## <a name="associationendpoint-properties"></a>AssociationEndpoint プロパティ

| 名前                                  | 種類       | 説明                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|---------------------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **System.Devices.Aep.AepId**          | String     | このデバイスの ID。 これは [**DeviceInformation.Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id) の値でもあります。                                                                                                                                                                                                                                                                                                                                                                        |
| **System.Devices.Aep.CanPair**        | Boolean    | デバイスがシステムとペアリングされているかどうかを示します。 [**DeviceInformationPairing.CanPair**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformationpairing.canpair.aspx) はこのプロパティから派生します。                                                                                                                                                                                                                                                                                                       |
| **System.Devices.Aep.Category**       | String\[\] | デバイスが含まれるカテゴリ。 たとえば、プリンターやカメラです。                                                                                                                                                                                                                                                                                                                                                                                                             |
| **System.Devices.Aep.ContainerId**    | GUID       | **AssociationEndpointContainer** 親オブジェクトの ID。                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **System.Devices.Aep.DeviceAddress**  | String     | デバイスのアドレス。 デバイスがネットワーク デバイスの場合、これは IP アドレスです。                                                                                                                                                                                                                                                                                                                                                                                                  |
| **System.Devices.Aep.IsConnected**    | Boolean    | デバイスが現在システムに接続されているかどうかを示します。                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **System.Devices.Aep.IsPaired**       | Boolean    | デバイスが現在ペアリングされているかどうかを示します。 [**DeviceInformationPairing.IsPaired**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformationpairing.ispaired.aspx) はこのプロパティから派生します。                                                                                                                                                                                                                                                                                                                      |
| **System.Devices.Aep.IsPresent**      | Boolean    | デバイスが現在存在するかどうか、つまり、デバイスが使用されていて、ネットワーク プロトコルまたはワイヤレス プロトコル経由で検出されているかどうかを示します。 デバイスとシステムをペアリングすると、デバイスはキャッシュされます。 この後、**AssociationEndpoint** オブジェクトを照会すると、デバイスは自動的に検出されます。 そのため、デバイスがクエリで検出されても、現在使用可能かどうかはわかりません。 したがって、このプロパティが重要になります。 |
| **System.Devices.Aep.Manufacturer**   | String     | デバイスの製造元。                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **System.Devices.Aep.ModelId**        | GUID       | デバイスのモデル ID。                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **System.Devices.Aep.ModelName**      | String     | デバイスのモデル名。                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **System.Devices.Aep.ProtocolId**     | GUID       | この **AssocationEndpoint** デバイスの検出に使われたプロトコルを示します。                                                                                                                                                                                                                                                                                                                                                                                                            |
| **System.Devices.Aep.SignalStrength** | Int32      | デバイスのシグナルの強さ。 このプロパティは、一部のプロトコルにのみ適用されます。                                                                                                                                                                                                                                                                                                                                                                                                |
| **System.ItemNameDisplay**            | String     | デバイスに最適な表示名。                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

 

## <a name="associationendpointcontainer-properties"></a>AssociationEndpointContainer プロパティ

| 名前                                                | 種類       | 説明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-----------------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **System.Devices.AepContainer.Categories**          | String\[\] | デバイスが含まれるカテゴリ。 たとえば、プリンターやカメラです。                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **System.Devices.AepContainer.Children**            | String\[\] | このコンテナーに格納される **AssocationEndpoint** オブジェクトの ID のコレクション。                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **System.Devices.AepContainer.CanPair**             | Boolean    | 子 **AssociationEndpoint** デバイスのいずれかをシステムとペアリングできるかどうかを示します。 [**DeviceInformationPairing.CanPair**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformationpairing.canpair.aspx) はこのプロパティから派生します。                                                                                                                                                                                                                                                                                                       |
| **System.Devices.AepContainer.ContainerId**         | GUID       | このデバイスの ID。 これは [**DeviceInformation.Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id) の値ですが、GUID 形式の値でもあります。                                                                                                                                                                                                                                                                                                                                                                                            |
| **System.Devices.AepContainer.IsPaired**            | Boolean    | 子 **AssociationEndpoint** デバイスのいずれかが現在ペアリングされているかどうかを示します。 [**DeviceInformationPairing.IsPaired**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformationpairing.ispaired.aspx) はこのプロパティから派生します。                                                                                                                                                                                                                                                                                                                      |
| **System.Devices.AepContainer.IsPresent**           | Boolean    | 子 **AssociationEndpoint** デバイスのいずれかが現在存在するかどうか、つまり、デバイスが使用されていて、ネットワーク プロトコルまたはワイヤレス プロトコル経由で検出されているかどうかを示します。 デバイスとシステムをペアリングすると、デバイスはキャッシュされます。 この後、**AssociationEndpoint** オブジェクトを照会すると、デバイスは自動的に検出されます。 そのため、デバイスがクエリで検出されても、現在使用可能かどうかはわかりません。 したがって、このプロパティが重要になります。 |
| **System.Devices.AepContainer.Manufacturer**        | String     | デバイスの製造元。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **System.Devices.AepContainer.ModelIds**            | String\[\] | デバイスのモデル ID の一覧。 各モデルは、string 形式の GUID です。                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **System.Devices.AepContainer.ModelName**           | String     | デバイスのモデル名。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **System.Devices.AepContainer.ProtocolIds**         | GUID\[\]   | この **AssociationEndpointContainer** オブジェクトの構築に関係するプロトコル ID の一覧。 **AssociationEndpointContainer** デバイスは、同じ物理デバイスについてさまざまなプロトコルで検出された **AssociationEndpoint** デバイスをすべて集めて作成されることに注意してください。                                                                                                                                                                                                                           |
| **System.Devices.AepContainer.SupportedUriSchemes** | String\[\] | このデバイスでサポートされているキャスト URI スキームの一覧。                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **System.Devices.AepContainer.SupportsAudio**       | Boolean    | このデバイスがオーディオのキャストをサポートしているかどうかを示します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **System.Devices.AepContainer.SupportsImages**      | Boolean    | このデバイスがイメージのキャストをサポートしているかどうかを示します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **System.Devices.AepContainer.SupportsVideo**       | Boolean    | このデバイスがビデオのキャストをサポートしているかどうかを示します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **System.ItemNameDisplay**                          | String     | デバイスに最適な表示名。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

 

## <a name="associationendpointservice-properties"></a>AssociationEndpointService プロパティ

| 名前                                            | 種類    | 説明                                                                                                      |
|-------------------------------------------------|---------|------------------------------------------------------------------------------------------------------------------|
| **System.Devices.AepService.AepId**             | String  | **AssociationEndpoint** 親オブジェクトの ID。                                                     |
| **System.Devices.AepService.ContainerId**       | GUID    | **AssociationEndpointContainer** 親オブジェクトの ID。                                            |
| **System.Devices.AepService.ParentAepIsPaired** | Boolean | **AssociationEndpoint** 親オブジェクトがシステムとペアリングしているかどうかを示します。                           |
| **System.Devices.AepService.ProtocolId**        | GUID    | このデバイスの検出に使われるプロトコルの ID。                                                           |
| **System.Devices.AepService.ServiceClassId**    | GUID    | このデバイスで表されるサービスの ID。                                                             |
| **System.Devices.AeoService.ServiceId**         | String  | このサービスの ID。 これは [**DeviceInformation.Id**](https://msdn.microsoft.com/library/windows/apps/windows.devices.enumeration.deviceinformation.id) の値でもあります。 |
| **System.ItemNameDisplay**                      | String  | このサービスに最適な表示名。                                                                           |

 

 

 