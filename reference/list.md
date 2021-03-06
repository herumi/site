#list
```cpp
namespace std {
  template <class T, class Allocator = allocator<T> >
  class list;
}
```

##概要
`<list>`ヘッダでは、双方向リンクリストの実装である `list` コンテナを提供する。  
任意の位置への挿入や削除を定数時間で行う事が出来るが、高速なランダムアクセスは出来ず、常にシーケンシャルアクセスを行う必要がある。


##メンバ関数
###構築／コピー／破棄

| 名前 | 説明 | 対応バージョン |
|-----------------------------------|----------------|-------|
| [`(constructor)`](./list/list.md) | コンストラクタ | |
| [`(destructor)`](./list/-list.md) | デストラクタ | |
| [`operator=`](./list/op_assign.md) | 代入演算子 | |
| [`assign`](./list/assign.md) | コンテナの再代入 | |


###イテレータ

| 名前 | 説明 | 対応バージョン |
|--------------------------------|----------------|-------|
| [`begin`](./list/begin.md)     | 先頭要素を指すイテレータを取得する               | |
| [`end`](./list/end.md)         | 末尾の次を指すイテレータを取得する               | |
| [`cbegin`](./list/cbegin.md)   | 先頭要素を指す読み取り専用イテレータを取得する   | C++11 |
| [`cend`](./list/cend.md)       | 末尾の次を指す読み取り専用イテレータを取得する   | C++11 |
| [`rbegin`](./list/rbegin.md)   | 末尾を指す逆イテレータを取得する                 | |
| [`rend`](./list/rend.md)       | 先頭の前を指す逆イテレータを取得する             | |
| [`crbegin`](./list/crbegin.md) | 末尾を指す読み取り専用逆イテレータを取得する     | C++11 |
| [`crend`](./list/crend.md)     | 先頭の前を指す読み取り専用逆イテレータを取得する | C++11 |


###領域

| 名前 | 説明 | 対応バージョン |
|------------|----------------|-------|
| `empty`    | コンテナが空かどうかを判定する | |
| `size`     | 要素数を取得する | |
| `max_size` | 格納可能な最大の要素数を取得する | |
| `resize`   | 要素数を変更する | |


###要素アクセス

| 名前 | 説明 | 対応バージョン |
|---------|----------------|-------|
| `front` | 先頭要素への参照を取得する | |
| `back` | 末尾要素への参照を取得する | |


###コンテナの変更

| 名前 | 説明 | 対応バージョン |
|-----------------|--------------------------------|-------|
| `emplace_front` | 先頭への直接構築による要素追加 | C++11 |
| `pop_front`     | 先頭から要素を削除 | |
| `emplace_back`  | 末尾への直接構築による要素追加 | C++11 |
| `push_front`    | 先頭に要素を追加する | |
| `push_back`     | 末尾に要素を追加する | |
| `pop_back`      | 末尾から要素を削除 | |
| `emplace`       | 要素の直接構築 | C++11 |
| `insert`        | 要素の挿入 | |
| `erase`         | 要素の削除 | |
| `swap`          | コンテナの交換 | |
| `clear`         | 全要素削除 | |


###リスト操作

| 名前 | 説明 | 対応バージョン |
|-----------------|--------------------------------|-------|
| `splice` | 2つのコンテナを併合する | |
| `remove` | コンテナから指定された値の要素を削除する | |
| `remove_if` | コンテナの条件に合った要素を削除する | |
| `unique` | 重複した要素をコンテナから削除する | |
| `merge` | 2つのコンテナを併合する | |
| `sort` | コンテナを並べ替える | |
| `reverse` | コンテナを反転する | |


###アロケータ

| 名前 | 説明 | 対応バージョン |
|-----------------|------------------------------|-------|
| `get_allocator` | アロケータオブジェクトの取得 | |


##メンバ型

| 名前 | 説明 | 対応バージョン |
|-----------------|------------------------------|-------|
| `reference` | `value_type&` | |
| `const_reference` | `const value_type&` | |
| `iterator` | 双方向イテレータ | |
| `const_iterator` | 読み取り専用双方向イテレータ | |
| `size_type` | 符号なし整数型(通常は`size_t`) | |
| `difference_type` | 符号あり整数型(通常は`ptrdiff_t`) | |
| `value_type` | `T` | |
| `allocator_type` | `Allocator` | |
| `pointer` | `allocator_traits<Allocator>::pointer` | |
| `const_pointer` | `allocator_traits<Allocator>::const_pointer` | |
| `reverse_iterator` | `std::reverse_iterator<iterator>` | |
| `const_reverse_iterator` | `std::reverse_iterator<const_iterator>` | |


##非メンバ関数

| 名前 | 説明 | 対応バージョン |
|--------------|------------------------------|-------|
| `operator==` | 等値比較 | |
| `operator!=` | 非等値比較 | |
| `operator<`  | 左辺が右辺より小さいかの判定を行う | |
| `operator<=` | 左辺が右辺以下かの判定を行う | |
| `operator>`  | 左辺が右辺より大きいかの判定を行う | |
| `operator>=` | 左辺が右辺以上かの判定を行う | |
| `swap`       | 2つの `list` オブジェクトを入れ替える | |


##例
```cpp
#include <iostream>
#include <list>
#include <algorithm>  // for_each

int main ()
{
  std::list<int>  ls;

  // 先頭から要素を追加
  ls.push_front(1);
  ls.push_front(2);

  // 末尾から要素を追加
  ls.push_back(3);
  ls.push_back(4);

  // 要素を先頭から順番に表示
  std::for_each(ls.cbegin(), ls.cend(), [](int x){
    std::cout << x << " ";
  });
}
```

###出力
```
2 1 3 4 
```

###参照


