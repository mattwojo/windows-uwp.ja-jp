---
author: TylerMSFT
title: 取り消されたバックグラウンド タスクの処理
description: 取り消し要求を認識し、作業を停止して、固定ストレージを使っているアプリの取り消しを報告するバックグラウンド タスクの作成方法について説明します。
ms.assetid: B7E23072-F7B0-4567-985B-737DD2A8728E
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10、UWP
ms.localizationpriority: medium
ms.openlocfilehash: 767280b3f3a073a55a4f489fd99229e42dd8140f
ms.sourcegitcommit: 54c2cd58fde08af889093a0c85e7297e33e6a0eb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
ms.locfileid: "1664845"
---
# <a name="handle-a-cancelled-background-task"></a>取り消されたバックグラウンド タスクの処理


**重要な API**

-   [**BackgroundTaskCanceledEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224775)
-   [**IBackgroundTaskInstance**](https://msdn.microsoft.com/library/windows/apps/br224797)
-   [**ApplicationData.Current**](https://msdn.microsoft.com/library/windows/apps/br241619)

取り消し要求を認識し、作業を停止して、固定ストレージを使っているアプリに取り消しを報告するバックグラウンド タスクの作成方法について説明します。

このトピックでは、バックグラウンド タスクのエントリ ポイントとして使う Run メソッドも含めて、既にバックグラウンド タスク クラスが作られていることを前提とします。 バックグラウンド タスクの作成方法の概要については、「[アウトプロセス バックグラウンド タスクの作成と登録](create-and-register-a-background-task.md)」または「[インプロセス バックグラウンド タスクの作成と登録](create-and-register-an-inproc-background-task.md)」をご覧ください。 条件とトリガーについて詳しくは、「[バックグラウンド タスクによるアプリのサポート](support-your-app-with-background-tasks.md)」をご覧ください。

このトピックは、インプロセス バックグラウンド タスクにも適用されます。 ただし、**Run()** メソッドを使う代わりに、**OnBackgroundActivated()** に置き換えます。 インプロセス バックグラウンド タスクでは、バックグラウンド タスクがフォアグラウンド アプリと同じプロセスで実行されているため、取り消しを通知するために固定ストレージを使用する必要はありません。アプリの状態を使用して、取り消しを伝えることができます。

## <a name="use-the-oncanceled-method-to-recognize-cancellation-requests"></a>OnCanceled メソッドにより、取り消し要求を認識します。

取り消しイベントを処理するメソッドを作ります。

> **注**  デスクトップ以外のすべてのデバイス ファミリでは、デバイスのメモリが少なくなった場合、バックグラウンド タスクが終了することがあります。 メモリ不足の例外が検出されないか、検出されてもアプリによって処理されない場合、バックグラウンド タスクは、警告や OnCanceled イベントの発生なしに終了します。 こうすることで、フォアグラウンドのアプリのユーザー エクスペリエンスが保証されます。 バックグラウンド タスクは、このシナリオを処理できるように設計する必要があります。

次のように **OnCanceled** という名前のメソッドを作成します。 このメソッドは、バックグラウンド タスクに対して取り消し要求が出されると、Windows ランタイムによって呼び出されるエントリ ポイントです。

> [!div class="tabbedCodeSnippets"]
> ```cs
>    private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
>    {
>        // TODO: Add code to notify the background task that it is cancelled.
>    }
> ```
> ```cpp
>    void ExampleBackgroundTask::OnCanceled(IBackgroundTaskInstance^ taskInstance, BackgroundTaskCancellationReason reason)
>    {
>        // TODO: Add code to notify the background task that it is cancelled.
>    }
> ```

バックグラウンド タスク クラスに **\_CancelRequested** というフラグ変数を追加します。 この変数は、取り消し要求が出されたことを示すために使います。

> [!div class="tabbedCodeSnippets"]
> ```cs
>   volatile bool _CancelRequested = false;
> ```
> ```cpp
>   private:
>     volatile bool CancelRequested;
> ```

手順 1 で作った OnCanceled メソッドで、フラグ変数 **\_CancelRequested** を **true** に設定します。

完全な[バックグラウンド タスクのサンプル]( http://go.microsoft.com/fwlink/p/?linkid=227509)、OnCanceled メソッドでは、**\_CancelRequested** を **true** に設定し、役立つデバッグ出力を書き出します。

> [!div class="tabbedCodeSnippets"]
> ```cs
>     private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
>     {
>         //
>         // Indicate that the background task is canceled.
>         //
>
>         _cancelRequested = true;
>
>         Debug.WriteLine("Background " + sender.Task.Name + " Cancel Requested...");
>     }
> ```
> ```cpp
>     void SampleBackgroundTask::OnCanceled(IBackgroundTaskInstance^ taskInstance, BackgroundTaskCancellationReason reason)
>     {
>         //
>         // Indicate that the background task is canceled.
>         //
>
>         CancelRequested = true;
>     }
> ```

バックグラウンド タスクの Run メソッドでは、処理を開始する前に **OnCanceled** イベント ハンドラー メソッドを登録します。 インプロセス バックグラウンド タスクでは、アプリケーションの初期化の一部としてこの登録を実行できます。 たとえば、次のコード行を使います。

> [!div class="tabbedCodeSnippets"]
> ```cs
>     taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);
> ```
> ```cpp
>     taskInstance->Canceled += ref new BackgroundTaskCanceledEventHandler(this, &SampleBackgroundTask::OnCanceled);
> ```

## <a name="handle-cancellation-by-exiting-your-background-task"></a>バックグラウンド タスクを終了することによって、取り消しを処理します。

バックグラウンド処理を実行しているメソッドは、**\_cancelRequested** が **true** に設定されたタイミングを認識し、処理を停止して終了する必要があります。 インプロセス バックグラウンド タスクの場合、これは **OnBackgroundActivated()** メソッドから戻ることです。 アウトプロセス バックグラウンド タスクの場合、これは **Run()** メソッドから戻ることです。

バックグラウンド タスク クラスの処理中にフラグ変数を確認するようにコードを変更します。 **\_cancelRequested** が true に設定された時点で、処理を中断します。

[バックグラウンド タスクのサンプル](http://go.microsoft.com/fwlink/p/?LinkId=618666)では、バックグラウンド タスクが取り消されたときに、定期タイマーのコールバックを停止するかどうかを確認します。

> [!div class="tabbedCodeSnippets"]
> ```cs
>     if ((_cancelRequested == false) && (_progress < 100))
>     {
>         _progress += 10;
>         _taskInstance.Progress = _progress;
>     }
>     else
>     {
>         _periodicTimer.Cancel();
>
>         // TODO: Record whether the task completed or was cancelled.
>     }
> ```
> ```cpp
>     if ((CancelRequested == false) && (Progress < 100))
>     {
>         Progress += 10;
>         TaskInstance->Progress = Progress;
>     }
>     else
>     {
>         PeriodicTimer->Cancel();
>
>         // TODO: Record whether the task completed or was cancelled.
>     }
> ```

> **注**  上記のコード サンプルでは、[**IBackgroundTaskInstance**](https://msdn.microsoft.com/library/windows/apps/br224797).[**Progress**](https://msdn.microsoft.com/library/windows/apps/br224800) プロパティを使って、バックグラウンド タスクの進行状況を記録します。 進行状況は、[**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782) クラスを使ってアプリに報告されます。

処理が停止したときに、タスクが完了したのか、取り消されたのかを記録するように、Run メソッドを変更します。 この手順は、バックグラウンド タスクが取り消されたときにプロセス間で通信する手段が必要となるため、別のプロセスで実行されるアウトプロセス バック グラウンド タスクに適用されます。 インプロセス バックグラウンド タスクでは、タスクが取り消されたことを示すために、状態をアプリケーションと共有するだけで十分です。

[バックグラウンド タスクのサンプル](http://go.microsoft.com/fwlink/p/?LinkId=618666)では、LocalSettings に状態が記録されます。

> [!div class="tabbedCodeSnippets"]
> ```cs
>     if ((_cancelRequested == false) && (_progress < 100))
>     {
>         _progress += 10;
>         _taskInstance.Progress = _progress;
>     }
>     else
>     {
>         _periodicTimer.Cancel();
>
>         var settings = ApplicationData.Current.LocalSettings;
>         var key = _taskInstance.Task.TaskId.ToString();
>
>         //
>         // Write to LocalSettings to indicate that this background task ran.
>         //
>
>         if (_cancelRequested)
>         {
>             settings.Values[key] = "Canceled";
>         }
>         else
>         {
>             settings.Values[key] = "Completed";
>         }
>         
>         Debug.WriteLine("Background " + _taskInstance.Task.Name + (_cancelRequested ? " Canceled" : " Completed"));
>         
>         //
>         // Indicate that the background task has completed.
>         //
>
>         _deferral.Complete();
>     }
> ```
> ```cpp
>     if ((CancelRequested == false) && (Progress < 100))
>     {
>         Progress += 10;
>         TaskInstance->Progress = Progress;
>     }
>     else
>     {
>         PeriodicTimer->Cancel();
>         
>         //
>         // Write to LocalSettings to indicate that this background task ran.
>         //
>         
>         auto settings = ApplicationData::Current->LocalSettings;
>         auto key = TaskInstance->Task->Name;
>         settings->Values->Insert(key, (Progress < 100) ? "Canceled" : "Completed");
>         
>         //
>         // Indicate that the background task has completed.
>         //
>         
>         Deferral->Complete();
>     }
> ```

## <a name="remarks"></a>注釈

[バックグラウンド タスクのサンプル](http://go.microsoft.com/fwlink/p/?LinkId=618666)をダウンロードして、メソッドのコンテキストに従ってコード例を確認できます。

このサンプル コードでは、説明の便宜上、[バックグラウンド タスクのサンプル](http://go.microsoft.com/fwlink/p/?LinkId=618666)の Run メソッド (およびコールバック タイマー) の一部しか示していません。

## <a name="run-method-example"></a>メソッド例を実行します。

[バックグラウンド タスクのサンプル](http://go.microsoft.com/fwlink/p/?LinkId=618666) のコンテキストがわかるように、以下に完全な Run メソッドとタイマーのコールバック コードを示します。

> [!div class="tabbedCodeSnippets"]
> ```cs
> //
> // The Run method is the entry point of a background task.
> //
> public void Run(IBackgroundTaskInstance taskInstance)
> {
>     Debug.WriteLine("Background " + taskInstance.Task.Name + " Starting...");
>
>     //
>     // Query BackgroundWorkCost
>     // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
>     // of work in the background task and return immediately.
>     //
>     var cost = BackgroundWorkCost.CurrentBackgroundWorkCost;
>     var settings = ApplicationData.Current.LocalSettings;
>     settings.Values["BackgroundWorkCost"] = cost.ToString();
>
>     //
>     // Associate a cancellation handler with the background task.
>     //
>     taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);
>
>     //
>     // Get the deferral object from the task instance, and take a reference to the taskInstance;
>     //
>     _deferral = taskInstance.GetDeferral();
>     _taskInstance = taskInstance;
>
>     _periodicTimer = ThreadPoolTimer.CreatePeriodicTimer(new TimerElapsedHandler(PeriodicTimerCallback), TimeSpan.FromSeconds(1));
> }
>
> //
> // Simulate the background task activity.
> //
> private void PeriodicTimerCallback(ThreadPoolTimer timer)
> {
>     if ((_cancelRequested == false) && (_progress < 100))
>     {
>         _progress += 10;
>         _taskInstance.Progress = _progress;
>     }
>     else
>     {
>         _periodicTimer.Cancel();
>
>         var settings = ApplicationData.Current.LocalSettings;
>         var key = _taskInstance.Task.Name;
>
>         //
>         // Write to LocalSettings to indicate that this background task ran.
>         //
>         settings.Values[key] = (_progress < 100) ? "Canceled with reason: " + _cancelReason.ToString() : "Completed";
>         Debug.WriteLine("Background " + _taskInstance.Task.Name + settings.Values[key]);
>
>         //
>         // Indicate that the background task has completed.
>         //
>         _deferral.Complete();
>     }
> }
> ```
> ```cpp
> void SampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
> {
>     //
>     // Query BackgroundWorkCost
>     // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
>     // of work in the background task and return immediately.
>     //
>     auto cost = BackgroundWorkCost::CurrentBackgroundWorkCost;
>     auto settings = ApplicationData::Current->LocalSettings;
>     settings->Values->Insert("BackgroundWorkCost", cost.ToString());
>
>     //
>     // Associate a cancellation handler with the background task.
>     //
>     taskInstance->Canceled += ref new BackgroundTaskCanceledEventHandler(this, &SampleBackgroundTask::OnCanceled);
>
>     //
>     // Get the deferral object from the task instance, and take a reference to the taskInstance.
>     //
>     TaskDeferral = taskInstance->GetDeferral();
>     TaskInstance = taskInstance;
>
>     auto timerDelegate = [this](ThreadPoolTimer^ timer)
>     {
>         if ((CancelRequested == false) &&
>             (Progress < 100))
>         {
>             Progress += 10;
>             TaskInstance->Progress = Progress;
>         }
>         else
>         {
>             PeriodicTimer->Cancel();
>
>             //
>             // Write to LocalSettings to indicate that this background task ran.
>             //
>             auto settings = ApplicationData::Current->LocalSettings;
>             auto key = TaskInstance->Task->Name;
>             settings->Values->Insert(key, (Progress < 100) ? "Canceled with reason: " + CancelReason.ToString() : "Completed");
>
>             //
>             // Indicate that the background task has completed.
>             //
>             TaskDeferral->Complete();
>         }
>     };
>
>     TimeSpan period;
>     period.Duration = 1000 * 10000; // 1 second
>     PeriodicTimer = ThreadPoolTimer::CreatePeriodicTimer(ref new TimerElapsedHandler(timerDelegate), period);
> }
> ```

## <a name="related-topics"></a>関連トピック

- [インプロセス バックグラウンド タスクの作成と登録](create-and-register-an-inproc-background-task.md)
- [アウトプロセス バックグラウンド タスクの作成と登録](create-and-register-a-background-task.md)
- [アプリケーション マニフェストでのバックグラウンド タスクの宣言](declare-background-tasks-in-the-application-manifest.md)
- [バックグラウンド タスクのガイドライン](guidelines-for-background-tasks.md)
- [バックグラウンド タスクの進捗状況と完了の監視](monitor-background-task-progress-and-completion.md)
- [バックグラウンド タスクの登録](register-a-background-task.md)
- [バックグラウンド タスクによるシステム イベントへの応答](respond-to-system-events-with-background-tasks.md)
- [タイマーでのバックグラウンド タスクの実行](run-a-background-task-on-a-timer-.md)
- [バックグラウンド タスクを実行するための条件の設定](set-conditions-for-running-a-background-task.md)
- [バックグラウンド タスクのライブ タイルの更新](update-a-live-tile-from-a-background-task.md)
- [メンテナンス トリガーの使用](use-a-maintenance-trigger.md)
- [バックグラウンド タスクのデバッグ](debug-a-background-task.md)
- [UWP アプリで一時停止イベント、再開イベント、バックグラウンド イベントをトリガーする方法 (デバッグ時)](http://go.microsoft.com/fwlink/p/?linkid=254345)