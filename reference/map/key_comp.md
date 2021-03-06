#key_comp
```cpp
key_compare key_comp() const;
```

##概要
コンテナに関連づけられた比較オブジェクトを返す。このオブジェクトはコンテナ内の二つの要素のキー値を比較するために利用できる。 
この比較オブジェクトはオブジェクトの構築時に与えられ、関数へのポインタでも関数オブジェクトでも良い。いずれの場合でも、これは同じ型の 2 つの引数をとり、狭義の弱順序に従って一つ目の引数が二つ目の引数より前のときに `true` を返し、そうでないときに `false` を返す。 


##戻り値
比較オブジェクト。`key_compare` はメンバ型であり、テンプレートパラメータ `Compare` の別名として定義される。


##計算量
定数時間


##例
```cpp
#include <iostream>
#include <map>
using namespace std;

int main()
{
  map<int,char> c;
  map<int,char>::key_compare comp = c.key_comp();

  cout << comp(1, 2) << endl;
  cout << comp(3, 2) << endl;

  return 0;
}
```

###出力
```
1
0
```

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): ??
- [GCC, C++11 mode](/implementation#gcc.md): ??
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md): ??, 11.0

##参照

| 名前 | 説明|
|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [`value_comp`](./value_comp.md) | 値を比較した結果を返す |
| [`find`](./find.md) | 指定したキーで要素を探す |
| [`count`](./count.md) | 指定したキーにマッチする要素の数を返す |
| [`lower_bound`](./lower_bound.md) | 与えられた値より小さく無い最初の要素へのイテレータを返す |
| [`upper_bound`](./upper_bound.md) | 特定の値よりも大きい最初の要素へのイテレータを返す |


