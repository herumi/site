#cend(C++11)
```cpp
const_iterator cend() const noexcept;
```

##概要
最終の要素の次を指す読み取り専用イテレータを取得する。

`unordered_map` は非順序連想コンテナであるため「最終」に特に意味はないが、[`cbegin`](./cbegin.md)`()` で得られたイテレータを `cend()` まで `operator++()` でイテレートすることで当該コンテナの要素を漏れなくダブりなく走査することができる。


##戻り値
最終の要素の次を指すイテレータ


##例外
投げない。


##計算量
定数


##例
```cpp
#include <iostream>
#include <string>
#include <algorithm>
#include <utility>
#include <unordered_map>

int main()
{
  typedef std::unordered_map<std::string, int> mymap;

  mymap um{ { "1st", 1 }, { "2nd", 2 }, { "3rd", 3 }, };

  std::for_each(um.cbegin(), um.cend(), [](mymap::value_type p) { std::cout << '{' << p.first << ',' << p.second << "}, "; });
  std::cout << std::endl;
}
```
* iostream[link /reference/iostream]
* string[link /reference/string.md]
* algorithm[link /reference/algorithm.md]
* utility[link /reference/utility.md]
* unordered_map[link /reference/unordered_map.md]
* for_each[link /reference/algorithm/for_each.md]
* cbegin[link /reference/unordered_map/unordered_map/cbegin.md]

###出力
```
{3rd,3}, {2nd,2}, {1st,1},
```

注：[`unordered_map`](/reference/unordered_map/unordered_map.md) は非順序連想コンテナであるため、出力順序は無意味であることに注意


##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): -
- [Clang, C++0x mode](/implementation#clang.md): 3.0, 3.1
- [GCC](/implementation#gcc.md): -
- [GCC, C++0x mode](/implementation#gcc.md): 4.4.7, 4.5.3, 4.6.3, 4.7.0
- [ICC](/implementation#icc.md): ?
- [Visual C++](/implementation#visual_cpp.md): ?

##参照

| | |
|----------------------------------------------|--------------------------------------------|
| [`begin`](./begin.md)                        | 先頭要素を指すイテレータの取得             |
| [`end`](./end.md)                            | 最終要素の次を指すイテレータの取得         |
| [`cbegin`](./cbegin.md)                      | 先頭要素を指す読み取り専用イテレータの取得 |
| [`begin(size_type)`](./begin-size_type.md)   | インデックス（添え字）で指定したバケット内の先頭要素を指すイテレータを取得 |
| [`end(size_type)`](./end-size_type.md)       | インデックス（添え字）で指定したバケット内の最終要素の次を指すイテレータを取得 |
| [`cbegin(size_type)`](./cbegin-size_type.md) | インデックス（添え字）で指定したバケット内の先頭要素を指す読み取り専用イテレータを取得 |
| [`cend(size_type)`](./cend-size_type.md)     | インデックス（添え字）で指定したバケット内の最終要素の次を指す読み取り専用イテレータを取得 |


