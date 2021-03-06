#cbegin(C++11)
```cpp
const_iterator cbegin() const noexcept;
```

##概要
先頭の要素を指す読み取り専用イテレータを取得する。


##戻り値
先頭要素を指す読み取り専用イテレータ


##例外
投げない


##例
```cpp
#include <iostream>
#include <list>
#include <algorithm>

int main()
{
  std::list<int>  ls  =  { 1, 2, 3 };

  // このアルゴリズム内ではlsの書き換えを決して行わない
  std::for_each(ls.cbegin(), ls.cend(), [](const int& x) {
    std::cout << x << std::endl;
  });
}
```
* cbegin[color ff0000]

###出力
```
1
2
3
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) 10.0


##参照


