#pair
```cpp
namespace std {
  template <class T1, class T2>
  struct pair;
}
```

##概要

`pair`は、2つの異なる型の値を保持する「組」を表現するためのクラスである。また、N個の異なる型の値を保持する「タプル」を表現するためのクラスとして、[`tuple`](/reference/tuple/tuple.md)クラスも提供されている。

###メンバ変数

| | |
|-------------------------|------------------|
| `T1 first;` | 1つめの要素 |
| `T2 second;` | 2つめの要素 |

###メンバ関数

| | |
|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| [`(constructor)`](./pair/pair.md) | コンストラクタ |
| [`operator=`](./pair/op_assign.md) | 代入演算子 |
| [`swap`](./pair/swap.md) | 他の`pair`オブジェクトと値を入れ替える |

###メンバ型

| | |
|--------------------------|-----------------|
| `first_type` | `T1` |
| `second_type` | `T2` |

###非メンバ関数

| | |
|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| [`make_pair`](./pair/make_pair.md) | `pair`を構築するヘルパ関数 |
| [`operator==`](./pair/op_equal.md) | 等値比較を行う |
| [`operator!=`](./pair/op_not_equal.md) | 非等値比較を行う |
| [`operator<`](./pair/op_less.md) | 左辺が右辺よりも小さいか判定を行う |
| [`operator<=`](./pair/op_less_equal.md) | 左辺が右辺以下か判定を行う |
| [`operator>`](./pair/op_greater.md) | 左辺が右辺より大きいか判定を行う |
| [`operator>=`](./pair/op_greater_equal.md) | 左辺が右辺以上か判定を行う |


##例
```cpp
#include <iostream>
#include <utility>
#include <string>

int main()
{
  // pairオブジェクトの構築
  std::pair<int, std::string> p = std::make_pair(1, "hello");

  // 要素の参照
  std::cout << p.first << std::endl;
  std::cout << p.second << std::endl;
}
```

###出力
```cpp
1hello
```

###参照
