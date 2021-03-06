#emplace(C++11)
```cpp
template <class... Args>
void emplace(Args&&... args)
```

##概要
要素型`T`のコンストラクタ引数をとり、直接構築でキューに要素を追加する。


##効果
`c.emplace_back(std::`[`forward`](/reference/utility/forward.md)`<Args>(args)...);`


##戻り値
なし


##例
```cpp
#include <iostream>
#include <queue>
#include <string>
#include <utility> // std::pair

int main ()
{
  std::queue<std::pair<int, std::string>> que;

  que.emplace(3, "aaa");
  que.emplace(1, "bbb");
  que.emplace(4, "ccc");

  while (!que.empty()) {
    std::cout << que.front().first << ", " << que.front().second << std::endl;
    que.pop();
  }
}
```
* emplace[color ff0000]

###出力
```
3, aaa
1, bbb
4, ccc
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): ??
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md)


