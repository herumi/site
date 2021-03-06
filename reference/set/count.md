#count
```cpp
size_type count(const key_type& x) const;
```

##概要
キー `x` を検索し、コンテナ内に見つかった要素の数を返す。`set` コンテナはキーの重複を許さないため、この関数は実際には要素が見つかったときに 1 を、そうでないときに 0 を返す。


##パラメータ
- `x` : 検索する値。`key_type` はメンバ型であり、`set` コンテナの中で `Key` の別名として定義される。ここで `Key` は 1 番目のテンプレートパラメータであり、コンテナに格納される要素の型である。


##戻り値
`x` と同じ値のキーが見つかったなら 1、そうでないなら 0。
メンバ型 `size_type` は符号なし整数型である。


##計算量
[`size()`](./size.md) について対数時間


##例
```cpp
#include <iostream>
#include <set>
using namespace std;

int main()
{
  set<int> c;

  c.insert(10);

  cout << c.count(10) << endl;
  cout << c.count(42) << endl;
  return 0;
}
```

###出力
```
1
0
```

##参照

| | |
|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [`find`](./find.md) | 指定したキーで要素を探す |
| [`size`](./size.md) | 要素数を取得する |
| [`lower_bound`](./lower_bound.md) | 与えられた値より小さくない最初の要素へのイテレータを返す |
| [`upper_bound`](./upper_bound.md) | 特定の値よりも大きい最初の要素へのイテレータを返す |


