#make_ready_at_thread_exit
```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

##概要

<b>タスクを実行し、スレッド終了時に準備完了状態にする。</b>
<b>この関数は、タスクの実行と準備完了状態にするタイミングをずらし、準備完了にするのをスレッド終了時まで遅延させたい場合に使用する。</b>


##効果

メンバ変数として保持している関数オブジェクト`f`に対して[`INVOKE`](/reference/functional/invoke.md)(f, args..., R)によって関数呼び出しを`行い、その戻り値を`[future](/reference/future/future.md)との共有状態に格納する。関数`f`の内部で例外が送出された場合は、共有状態に送出された例外が格納される。
現在のスレッドが終了し、スレッドローカル記憶域を持つ全てのオブジェクトを破棄したあと、準備完了状態([`future_status::ready`](/reference/future/future_status.md))にする。



##戻り値

なし


##例外

この関数は、以下のerror conditionを持つ[future_error](/reference/future/future_error.md)例外オブジェクトを送出する可能性がある：

- [`promise_already_satisfied`](/reference/future/future_errc.md) ： 格納されたタスクがすでに実行された
- `[no_state](/reference/future/future_errc.md) `： `*this`が共有状態を持っていない(`packaged_task`オブジェクトがムーブされると起こりうる)



##備考



##例

```cpp
#include <iostream>
#include <future>
#include <thread>
#include <functional>

int plus_task(int a, int b)
{
  return a + b;
}

// packaged_taskを左辺値参照にしているのはVisual C++ 2012のバグのため
// http://connect.microsoft.com/VisualStudio/feedback/details/737812
void calc(std::packaged_task<int(int, int)>& task)
{
  // 現在のスレッド終了時に準備完了状態にする
  task.make_ready_at_thread_exit(2, 3);
}

int main()
{
  std::packaged_task<int(int, int)> task(plus_task);
  std::future<int> f = task.get_future();

  std::thread t(calc, std::ref(task));
  t.detach();

  // タスクの結果を取得
  int result = f.get();
  std::cout << result << std::endl;
}
```
* http://connect.microsoft.com/VisualStudio/feedback/details/737812[link http://connect.microsoft.com/VisualStudio/feedback/details/737812]

###出力

```cpp
5
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) 11.0<h4>備考</h4>
(処理系やライブラリのバグや不完全な実装などをここに書く。なければ備考欄を削除)



##参照

[_at_thread_exit系の関数が存在している理由](/article/at_thread_exit.md)
