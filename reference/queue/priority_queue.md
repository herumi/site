#priority_queue
```cpp
namespace std {
  template <class T,
            class Container = vector<T>,
            class Compare = less<typename Container::value_type>>
  class priority_queue;
}
```
* vector[link /reference/vector.md]

##概要

priority_queueはコンテナアダプタであり、優先順位付きキューを実現する目的で設計されている。要素をpush()で追加し、取り出す際にtop()を呼び出すことで、Compare述語によって優先順に要素が取り出される。
priority_queue は、所定のメンバ関数を持つコンテナのオブジェクトを内部実装として用いており、標準のコンテナ、もしくは独自に実装したコンテナを指定することができる。
このコンテナに必要な要件は、以下のメンバ関数を持つことである。

- front()
- push_back()
- pop_back()
- emplace_back() (C++11)
この要件を満たすものとしては[vector](/reference/vector.md)と[deque](/reference/deque.md)があり、デフォルトでは[vector](/reference/vector.md)が使用される。

queueは2つのテンプレート引数を持つ。

各テンプレートパラメータの意味は以下の通りである。
<ol>
- T: 要素の型
- Container: 内部実装のコンテナクラス
- Compare: 優先順に並べ替えるための比較用述語型。デフォルトでは降順比較のlessが使用される。</ol>

以下のリファレンス中では、テンプレート引数として同じ名前を用いる。


###メンバ関数

| | |
|--------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
|` `[`(constructor)`](./priority_queue/priority_queue.md) |` コンストラクタ` |
|` ``~priority_queue() = default` |` デストラクタ` |
|` operator=(const priority_queue&) = default`` operator=(priority_queue&&) = default` |` 代入演算子` |
|` [empty](./priority_queue/empty.md)` |` 要素が空かどうかを判定する` |
|` [size](./priority_queue/size.md)` |` 要素数を取得する` |
|` [top](./priority_queue/top.md)` |` 次の要素にアクセスする` |
|` [push](./priority_queue/push.md)` |` 要素を追加する` |
|` [emplace](./priority_queue/emplace.md)` |` 直接構築で要素を追加する(C++11)` |
|` [pop](./priority_queue/pop.md)` |` 次の要素を削除する` |
|` [swap](./priority_queue/swap.md)` |` 他のpriority_queueオブジェクトと値を入れ替え`る(C++11) |

###protectedメンバ変数

| | |
|------------------------|------------------------|
|` 変数名` |` 型` |
|` c` |` Container` |
|` comp` |` Compare` |

###メンバ型

| | |
|------------------------------|------------------------------------------------|
|` value_type` |` Container::value_type` |
|` reference` |` Container::reference(C++11)` |
|` const_reference` |` Container::const_reference(C++11)` |
|` size_type` |` Container::size_type` |
|` container_type` |` Container` |

###非メンバ関数

| | |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|` [swap](./priority_queue/swap_free.md)` |` 2つのpriority_queueオブジェクトを入れ替える(C++11)` |


##例
```cpp
#include <iostream>
#include <queue>

int main()
{
  // intを要素に持つ優先順位付きキュー
  std::priority_queue<int> que;

  // データを追加する
  que.push(3);
  que.push(1);
  que.push(4);

  // 中身の出力
  while (!que.empty()) {
    std::cout << que.top() << std::endl;
    que.pop();
  }
}
```

###出力
```cpp
4
3
1
```

###参照
