#geometric_distribution(C++11)
```cpp
namespace std {
  template <class IntType = int>
  class geometric_distribution;
}
```

##概要
`geometric_distribution`は、離散確率分布の一種である幾何分布を表すクラスである。  
このクラスは、ベルヌーイ分布([`bernoulli_distribution`](./bernoulli_distribution.md))を施行し、初めて成功するまでに何回失敗したかを取得する。これは、[`negative_binomial_distribution`](./negative_binomial_distribution.md)`<IntType>(1, p)`と同じである。


テンプレートパラメータは、以下を意味する：

- `IntType` : 成功回を表す整数型。


##メンバ関数
###構築・リセット

| 名前 | 説明 | 対応バージョン |
|-----------------------------------------------------------------------|--------------------|-------|
| [`(constructor)`](./geometric_distribution/geometric_distribution.md) | コンストラクタ     | C++11 |
| `~geometric_distribution() = default;`                                | デストラクタ       | C++11 |
| [`reset`](./geometric_distribution/reset.md)                          | 状態をリセットする | C++11 |


###生成

| 名前 | 説明 | 対応バージョン |
|-----------------------------------------------------|----------------|-------|
| [`operator()`](./geometric_distribution/op_call.md) | 乱数を生成する | C++11 |


###プロパティ

| 名前 | 説明 | 対応バージョン |
|----------------------------------------------|----------------------------------|-------|
| [`p`](./geometric_distribution/p.md)         | 確率を取得する                   | C++11 |
| [`param`](./geometric_distribution/param.md) | 分布のパラメータを取得／設定する | C++11 |
| [`min`](./geometric_distribution/min.md)     | 生成する範囲の最小値を取得する   | C++11 |
| [`max`](./geometric_distribution/max.md)     | 生成する範囲の最大値を取得する   | C++11 |


##メンバ型

| 型 | 説明 | 対応バージョン |
|---------------|---------------------------------|-------|
| `result_type` | 乱数生成結果の整数型。`IntType` | C++11 |
| `param_type`  | 分布パラメータの型。未規定。    | C++11 |


##非メンバ関数

| 名前 | 説明 | 対応バージョン |
|----------------------------------------------------------|----------------------|-------|
| [`operator==`](./geometric_distribution/op_equal.md)     | 等値比較             | C++11 |
| [`operator!=`](./geometric_distribution/op_not_equal.md) | 非等値比較           | C++11 |
| [`operator<<`](./geometric_distribution/op_ostream.md)   | ストリームへの出力   | C++11 |
| [`operator>>`](./geometric_distribution/op_istream.md)   | ストリームからの入力 | C++11 |


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::random_device seed_gen;
  std::default_random_engine engine(seed_gen());

  // 成功確率0.5の事象を、成功するまで施行する
  std::geometric_distribution<> dist(0.5);

  // 成功するまでに、何回失敗したかを取得
  int result = dist(engine);
  std::cout << result << std::endl;
}
```

###出力例
```
0
```


##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.2
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md): ??


##参照
- [幾何分布 - Wikipedia](http://ja.wikipedia.org/wiki/幾何分布)

