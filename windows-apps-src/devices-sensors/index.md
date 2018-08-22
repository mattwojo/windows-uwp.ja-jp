---
author: muhsinking
ms.assetid: 0b891f63-02fa-4c30-b307-9fbcccac5caa
title: デバイス、センサーの使用
description: 優れたユーザー エクスペリエンスを実現するために、外部デバイスまたはセンサーをアプリに統合する必要があります。
ms.author: mukin
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8227de880fd6e467bb015be9affa764d405c4546
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "1018125"
---
# <a name="devices-sensors-and-power"></a>デバイス、センサーの使用


優れたユーザー エクスペリエンスを実現するために、外部デバイスまたはセンサーをアプリに統合する必要があります。 ここでは、このセクションで説明するテクノロジを使って、アプリに追加できる機能例をいくつか紹介します。

-   充実した印刷エクスペリエンスの実現
-   ゲームへのモーション センサーと方位センサーの統合
-   デバイスの直接接続またはネットワーク プロトコルを経由した接続

| トピック | 説明 |
|-------|-------------|
| [デバイス機能を有効にする](enable-device-capabilities.md) | このチュートリアルでは、Microsoft Visual Studio のデバイス機能の宣言方法について説明します。 カメラ、マイク、位置センサー、その他のデバイスをアプリで使うことができるようにします。 | 
| [Windows IoT のユーザー モードのアクセスを有効にします。](enable-usermode-access.md) | このチュートリアルでは、Windows 10 IoT Core で GPIO、I2C、SPI、および UART へのユーザー モード アクセスを有効にする方法について説明します。 |
| [デバイスの列挙](enumerate-devices.md) | 列挙用の名前空間によって、システムに内部接続されているデバイス、外部接続されているデバイス、ワイヤレス プロトコルまたはネットワーク プロトコル経由で検出できるデバイスを検索できます。 |
| [デバイスのペアリング](pair-devices.md) | 一部のデバイスは、使う前にペアリングする必要があります。 [<strong>Windows.Devices.Enumeration</strong>](https://msdn.microsoft.com/library/windows/apps/BR225459) 名前空間では、デバイスをペアリングするための 3 つの異なる方法がサポートされています。 |
| [Point of Service](point-of-service.md) | このセクションでは、バーコード スキャナー、開封済みメッセージ プリンター、引き出しなどのサービス周辺のポイントを操作する方法について説明します。 | 
| [センサー](sensors.md) | センサーは、デバイスとその周囲の実際の世界の関係をアプリに通知します。 つまり、デバイスの方角や向き、動きをアプリに伝えることができます。 |
| [Bluetooth](bluetooth.md) | このセクションでは、RFCOMM、GATT、低エネルギー (LE) アドバタイズを使う方法を含め、ユニバーサル Windows プラットフォーム (UWP) アプリに Bluetooth を統合する方法に関する記事を取り上げています。 | 
| [印刷とスキャン](printing-and-scanning.md) | このセクションでは、ユニバーサル Windows アプリから印刷およびスキャンする方法について説明します。 | 
| [3D 印刷](3d-printing.md) | このセクションでは、ユニバーサル Windows アプリで 3D 印刷機能を使用する方法について説明します。 |
| [NFC スマート カード アプリの作成](host-card-emulation.md) | Windows Phone 8.1 では、SIM ベースのセキュア エレメントを使用する NFC カード エミュレーション アプリがサポートされていましたが、このモデルでは、安全な支払いアプリと移動体通信事業者 (MNO) 様との密接な連携が必要でした。 このことにより、MNO 様と連携していないために、他の事業者様や開発者様によるさまざまな支払いソリューションの可能性が制限されていました。 Windows 10 Mobile では、ホスト カード エミュレーション (HCE) と呼ばれる新しいカード エミュレーション テクノロジが導入されています。 HCE テクノロジを使用すると、アプリが NFC カード リーダーと直接通信することができます。 このトピックでは、Windows 10 Mobile デバイスでのホスト カード エミュレーション (HCE) のしくみと、物理的なカードではなく電話からユーザーがサービスにアクセスできるような HCE アプリを MNO 様と連携せずに開発する方法について説明します。 |
| [バッテリー情報の取得](get-battery-info.md) | [<strong>Windows.Devices.Power</strong>](https://msdn.microsoft.com/library/windows/apps/Dn895017) 名前空間で、API を使って詳細なバッテリー情報を取得する方法について説明します。 |
