#get_allocator(C++11)
```cpp
allocator_type get_allocator() const noexcept;
```

##概要
`vector`が内包しているアロケータを取得する。


##戻り値
`vector`が内包しているアロケータ


##例外
投げない


##例
```cpp
#include <cassert>
#include <vector>

int main()
{
  std::allocator<int> alloc;
  std::vector<int> v(alloc);

  std::allocator<int> result = v.get_allocator();

  assert(result == alloc);
}
```
* get_allocator[color ff0000]

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


