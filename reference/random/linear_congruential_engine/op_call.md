#operator()(C++11)
```cpp
result_type operator()();
```

##概要
乱数生成を行う。


#効果
ランダムな値を生成し、内部状態を進める。


##戻り値
ランダムな値を生成して返す。  
値の範囲は`[`[`min()`](./min.md), [`max()`](.max.md)`]`である。つまり、最小値と最大値両方を含む。


##計算量
償却定数時間


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::minstd_rand engine;

  for (int i = 0; i < 10; ++i) {
    // 乱数生成
    std::uint32_t result = engine();

    std::cout << result << std::endl;
  }
}
```


###出力例
```
48271
182605794
1291394886
1914720637
2078669041
407355683
1105902161
854716505
564586691
1596680831
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.2
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照


