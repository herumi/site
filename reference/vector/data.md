#data
```cpp
T* data() noexcept;
const T* data() const noexcept;
```

##効果
配列の先頭へのポインタを返す。


##戻り値
`[data(), data() + size())` が適正な範囲になるようなポインタ。

空ではない`vector`に対しては`data() == &front()`となる。


##計算量
定数時間


##例
```cpp
#include <iostream>
#include <vector>

int main()
{
  std::vector<int> v = {3, 1, 4};

  int* p = v.data();

  std::cout << *p << std::endl;

  ++p;
  std::cout << *p << std::endl;
}
```
* data[color ff0000]

###出力
```
3
1
```

##言語
- C++11

