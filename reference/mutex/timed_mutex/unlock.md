#unlock
```cpp
void unlock();
```

##概要

<b>ロックを手放す</b>



##要件

この関数を実行するスレッドがミューテックスの所有権を持っていること



##効果

この関数を呼び出したスレッドが持つミューテックスの所有権を手放す



##戻り値

なし



##例外

投げない



##備考



##例

```cpp
#include <iostream>
#include <thread>
#include <mutex>
#include <vector>

class X {
  std::timed_mutex mtx_;
  int value_ = 0;
public:
  // メンバ変数value_への書き込みを排他的にする
  void add_value(int value)
  {
    mtx_.lock(); // ロックを取得する
    value_ = value;
    mtx_.unlock(); // ロックを手放す
  }
};

int main()
{
  X x;

  std::thread t1([&x]{ x.add_value(1); });
  std::thread t2([&x]{ x.add_value(2); });

  t1.join();
  t2.join();
}
```
* unlock[color ff0000]

###出力

```cpp
```

##バージョン
```
###言語


- C++11



###処理系

- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??



##参照

