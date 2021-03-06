#bucket(C++11)
```cpp
size_type bucket(const key_type& k) const;
```

##概要
指定したキーと等価な要素が格納されている場合、そのバケットのインデックス（添え字）を返す。


##要件
当該コンテナは [`bucket_count`](./bucket_count.md)`() > 0` であること


##戻り値
パラメータ `k` と等価なキーの要素が格納されているバケットのインデックス（添え字）

戻り値は `[0, `[`bucket_count`](./bucket_count.md)`())` の範囲である。


##計算量
定数。


##備考
指定したキーと等価な要素が格納されていない場合、そのキーを挿入した際に [`rehash`](./rehash.md) が発生しなければ格納されるバケットのインデックス（添え字）が返る。


##例
```cpp
#include <iostream>
#include <string>
#include <unordered_set>

int main()
{
  std::unordered_set<std::string> us{ "A", "B", "C", "D", "E", };

  decltype(us)::size_type c = us.bucket_count();
  std::cout << "bucket_count() = " << c << std::endl;

  // 全てのキーに対するバケットのインデックスとそのバケットの要素数を取得
  for (decltype(us)::key_type k : us) {
    decltype(us)::size_type b = us.bucket(k);
    decltype(us)::size_type s = us.bucket_size(b);
    std::cout << "key = " << k << ", bucket = " << b << ", bucket_size = " << s << std::endl;
  }

  // 存在しないキーに対するバケットのインデックスとそのバケットの要素数を取得
  decltype(us)::key_type k = "H";
  decltype(us)::size_type b = us.bucket(k);
  decltype(us)::size_type s = us.bucket_size(b);
  std::cout << "key = " << k << ", bucket = " << b << ", bucket_size = " << s << std::endl;
}
```
* iostream[link /reference/iostream.md]
* string[link /reference/string.md]
* unordered_set[link /reference/unordered_set.md]
* bucket_count[link ./bucket_count.md]
* bucket_size[link ./bucket_size.md]

###出力
```
bucket_count() = 5
key = E, bucket = 0, bucket_size = 1
key = D, bucket = 1, bucket_size = 1
key = C, bucket = 4, bucket_size = 2
key = B, bucket = 4, bucket_size = 2
key = A, bucket = 3, bucket_size = 1
key = H, bucket = 2, bucket_size = 0
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): -
- [Clang, C++0x mode](/implementation#clang.md): 3.1
- [GCC](/implementation#gcc.md): -
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.2
- [ICC](/implementation#icc.md): ?
- [Visual C++:](/implementation#visual_cpp.md) ?

##参照


| | |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------|
| [`max_bucket_count`](./max_bucket_count.md) | 最大バケット数の取得 |

