#bitset
```cpp
namespace std {
  template <size_t N>
  class bitset;
}
```

##概要

`<bitset>`ヘッダでは、ビットの固定サイズ配列を計算するための`std::bitset`クラスを定義する。

###メンバ関数

| | |
|----------------------------|------------------------------------------------------------------------------------------|
| `(constructor)` | コンストラクタ |
| `(destructor)` | デストラクタ |
| `operator=` | 代入演算子 |
| `operator&=` | ANDの複合演算 |
| <code>operator&#x7C;=</code> | ORの複合演算 |
| `operator^=` | XORの複合演算 |
| `operator<<=` | 左シフトの複合演算 |
| `operator>>=` | 右シフトの複合演算 |
| `set` | 任意の位置のビットをONにする |
| `reset` | 任意の位置のビットをOFFにする |
| `operator~` | NOTをとる |
| `flip` | ビット反転 |
| `operator[]` | 任意の位置のビットにアクセスする |
| `to_ulong` | unsigned long型に変換する |
| `to_ullong` | unsigned long long型に変換する |
| `to_string` | 文字列に変換する |
| `count` | ONになっているビットの数を取得する |
| `size` | ビット数を取得する |
| `operator==` | 等値比較 |
| `operator!=` | 非等値比較 |
| `test` | 任意の位置のビットがONになっているかを判定する |
| `all` | 全てのビットがONになっているかを判定する(C++11) |
| `any` | いずれかのビットがONになっているかを判定する |
| `none` | 全てのビットがOFFになっているかを判定する |
| `operator<<` | 左シフト |
| `operator>>` | 右シフト |

###メンバ型

| | |
|------------------------|--------------------------------------------------------------------|
| `reference` | 任意の位置のビットを参照するためのプロキシ型 |

###非メンバ関数

| | |
|-------------------------|-----------------------------|
| `operator&` | AND演算 |
| <code>operator&#x7C;</code> | OR演算 |
| `operator^` | XOR演算 |
| `operator>>` | ストリームから入力 |
| `operator<<` | ストリームに出力 |


##例
```cpp
```

###出力
```cpp
###参照
```