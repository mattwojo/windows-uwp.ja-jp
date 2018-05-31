---
author: Mtoepke
title: Xbox One 開発者モードの非アクティブ化
description: 開発者モードを非アクティブ化する方法を説明します。
ms.author: scotmi
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, UWP
ms.assetid: 244124dd-d80a-4a72-91db-1c9c2fbc7c3c
ms.localizationpriority: medium
ms.openlocfilehash: 90d1c5a8c5fc65cf591211d6f26cfce099597aad
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
ms.locfileid: "1689088"
---
# <a name="xbox-one-developer-mode-deactivation"></a>Xbox One 開発者モードの非アクティブ化

本体を開発用に使うことをやめる場合は、以下の手順を使って開発者モードを非アクティブ化します。

## <a name="switch-to-retail-mode"></a>リテール モードに切り替える

まず、Xbox One 本体をリテール モードに戻します。

1. **Dev Home** を開きます。

2. **[開発者モードの終了]** を選びます。  本体がリテール モードで再起動します。  

   ![開発者モードの終了](images/devkit-deactivation-1.png)

次のいずれかの方法を使って本体を非アクティブ化します。

## <a name="deactivate-your-console-using-the-dev-mode-activation-app"></a>開発者モードのアクティブ化用アプリを使って本体を非アクティブ化する

本体の開発者モードを非アクティブ化するための推奨される方法は、**開発者モードのアクティブ化**用アプリを使うことです。 

1. **[ゲームとアプリ]** > **[アプリ]** に移動します。
  
   ![アクティブ化手順 3](images/devkit-deactivation-5.png)    
   
2.  開発者モードのアクティブ化用アプリを開きます。

3.  **[非アクティブ化]** を選びます。
  
    ![本体の非アクティブ化](images/deactivation-app.png)

**開発者モードのアクティブ化**用アプリについて詳しくは、「[Xbox One 開発者モードのアクティブ化](devkit-activation.md)」をご覧ください。 

## <a name="reset-your-console"></a>本体をリセットする

開発者モードを非アクティブ化するには、本体をリセットする方法を使うこともできます。  

> [!NOTE]
> 本体をリセットすると、ローカルに保存されているゲーム データはすべて失われます。

本体をリセットするには、次の手順を実行します。

1.  **[マイ コレクション]** に移動します。

2.  **[アプリ]** を選択し、**[設定]** を選択します。

3.  左ペインの **[システム]** に移動し、右ペインの **[本体の情報]** を選択します。   
   
    ![本体の情報と更新](images/devkit-deactivation-2.png)  
    
4.  **[本体のリセット]** を選択します。
    
    ![本体のリセット](images/devkit-deactivation-3.png)
    
5.  次に、**[Reset and remove everything]** (すべてを削除してリセット) を選びます。 このオプションは、本体をリセットして元の製品版の状態にします。  アプリ、ゲーム、ローカルに保存されたデータはすべて削除されます。 もう 1 つのオプションである **[Reset and keep my games & apps]** (ゲームとアプリを保持してリセット) を選んだ場合、本体は開発者プログラムから削除されません。  
   
    ![すべてを削除してリセット](images/devkit-deactivation-4.png)

## <a name="deactivate-your-console-using-windows-dev-center"></a>Windows デベロッパー センターを使って本体を非アクティブ化する

何らかの理由で本体にアクセスできない場合は、Windows デベロッパー センターを使って本体の開発者モードを非アクティブ化できます。

1. デベロッパー センターにある [Xbox One 本体の管理](https://developer.microsoft.com/xboxdevices)についてのページに移動します。 デベロッパー センター アカウントへのサインインを求められることがあります。

2. 本体の一覧で、シリアル番号、本体の ID、またはデバイス ID を照らし合わせて、非アクティブ化する本体を見つけます。  

3. **[Deactivate]** (非アクティブ化) をクリックします。  
  
![DevCenter を使った非アクティブ化](images/devkit-deactivation-6.png)

事前に Xbox One 本体をリテール モードに戻していない場合は、「[リテール モードに切り替える](#switch-to-retail-mode)」の説明に従ってここで戻してください。

## <a name="see-also"></a>関連項目
- [Xbox One 開発者モードのアクティブ化](devkit-activation.md)
- [Xbox One の UWP](index.md)