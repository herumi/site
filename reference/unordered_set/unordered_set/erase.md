#erase
```cpp
iterator erase(const_iterator position);                   // (1)
size_type erase(const key_type& k);                        // (2)
iterator erase(const_iterator first, const_iterator last); // (3)
```

##概要

指定された要素を削除する


##要件


- <code style='color:black'>position</code> は、有効で、かつ、間接参照可能な（dereferenceable、つまり <code style='color:black'>[cend](/reference/unordered_set/unordered_set/cend.md)()</code> ではない）当該コンテナを指す読み取り専用イテレータでなければならない。

- <code style='color:black'>k</code> は <code style='color:black'>key_type</code> 型の値でなければならない。
<li><code style='color:black'>first</code> と <code style='color:black'>last</code> は <code style='color:black'>[first, last)</code> が当該コンテナの有効な範囲である読み取り専用イテレータでなければならない。
なお、標準では <code style='color:black'>first</code> は間接参照可能である必要があることになっているが、他の種類のコンテナの要件と照らし合わせると、間接参照可能である必要はない（つまり、<code style='color:black'>first</code> と <code style='color:black'>last</code> が共に <code style='color:black'>[cend](/reference/unordered_set/unordered_set/cend.md)()</code> でも良い）ものと思われる。</li>


##効果

- (1)	`position` で指定された要素を削除する。
- (2)	`k` と等価なキーの要素を削除する。
- (3)	`[first, last)` の範囲にある要素を全て削除する。


##戻り値

- (1)	「削除前に、削除された要素の次だった位置」を指すイテレータ。`erase()` を呼び出しても削除された要素以外を指す全てのイテレータは無効にならないため、`std::[next](/reference/iterator/next.md)(position)` と同じ位置を指す `iterator` である。なお、`position` は `const_iterator` なのに対して、戻り値は `iterator` であるため注意が必要だが、非順序連想コンテナの場合いずれにせよどちらも読み取り専用イテレータである。
- (2)	削除した要素数。つまり、`k` と等価なキーの要素があれば 1、無ければ 0。
- (3)	 「削除前に、削除された要素の範囲の次だった位置」を指すイテレータ。`erase()` を呼び出しても削除された要素以外を指す全てのイテレータは無効にならないため、`last` と同じ位置を指す `iterator` である。なお、<code style='font-size:10pt'>first</code> 及び <code style='font-size:10pt'>last</code> は <code style='font-size:10pt'>const_iterator</code> なのに対して、戻り値は `iterator` であるため注意が必要だが、非順序連想コンテナの場合いずれにせよどちらも読み取り専用イテレータである。また、要件に示したように `first` が間接参照可能である必要がなかった場合にも、他の種類のコンテナの戻り値と照らし合わせると、`last` と同じ位置を指す `iterator` を返すのが適切であるものと思われる。


##例外

- (1)	投げない。
- (2)	コンテナの `key_equal` と `hasher` のオブジェクト（それぞれ `key_eq()` と `hash_function()` が返すオブジェクト）が例外を投げなければ、例外を投げない。
- (3)	投げない。


##計算量

- (1)	平均的なケースでは定数（O(1)）だが、最悪のケースではコンテナの要素数に比例（O(N)）
- (2)	平均的なケースでは削除された要素数に比例（O(`count(k)`)）だが、最悪のケースではコンテナの要素数に比例（O(`size()`)）
- (3)	平均的なケースでは指定された範囲の要素数に比例（O(`std::distance(first, last)`)）だが、最悪のケースではコンテナの要素数に比例（O(`size()`)）


##備考

削除された要素を指すイテレータ、および、参照のみ無効になる。なお、標準に明確な記載は無いが、削除された要素を指すポインタも無効になる。


##例

```cpp
<pre style='margin:0'><code style='color:black'>#include <iostream>
#include <unordered_set>
#include <iterator>
#include <algorithm>
#include <string>

template <class C>
void print(const std::string& label, const C& c, std::ostream& os = std::cout)
{
  os << label << " : ";
  std::copy(c.begin(), c.end(), std::ostream_iterator<typename C::value_type>(os, " "));
  os << std::endl;
}

int main()
{
  // 指定した位置にある要素を削除（(1)の形式）
  {
    std::unordered_set<int> us{ 1, 3, 5, 7, 9, };
    print("(1) erase(const_iterator) before", us);

    auto it1 = std::next(us.cbegin(), 3);
    std::cout << "argument: " << *it1 << std::endl;
    auto it2 = us.erase(it1);
    std::cout << "return value: " << *it2 << std::endl;
    print("after", us);
  }

  // 指定したキーと等価な要素を削除（(2)の形式）
  {
    std::unordered_set<int> us{ 1, 3, 5, 7, 9, };
    print("(2) erase(const value_type&) before", us);

    auto count1 = us.erase(5);
    auto count2 = us.erase(8);
    std::cout << "argument: 5, 8" << std::endl;
    std::cout << "return value: " << count1 << ", " << count2 << std::endl;
    print("after", us);
  }

  // 指定した位置にある要素を削除（(3)の形式）
  {
    std::unordered_set<int> us{ 1, 3, 5, 7, 9, };
    print("(3) erase(const_iterator, const_iterator) before", us);

    auto it1 = std::next(us.cbegin());
    auto it2 = std::next(it1, 2);
    std::cout << "arguments: " << *it1 << ", " << *it2 << std::endl;
    auto it3 = us.erase(it1, it2);
    std::cout << "return value: " << *it3 << std::endl;
    print("after", us);
  }
}</pre>
```
* iostream[link /site/cpprefjp/reference/iostream]
* unordered_set[link /reference/unordered_set.md]
* iterator[link /reference/iterator.md]
* algorithm[link /reference/algorithm.md]
* string[link /reference/string.md]
* ostream[link /site/cpprefjp/reference/iostream/ostream]
* copy[link /reference/algorithm/copy.md]
* begin[link /reference/unordered_set/unordered_set/begin.md]
* end[link /reference/unordered_set/unordered_set/end.md]
* ostream_iterator[link /reference/iterator/ostream_iterator.md]
* next[link /reference/iterator/next.md]
* cbegin[link /reference/unordered_set/unordered_set/cbegin.md]

###出力

```cpp
<pre style='margin:0'><code style='color:black'>(1) erase(const_iterator) before : 9 7 5 3 1
argument: 3
return value: 1
after : 9 7 5 1
(2) erase(const value_type&) before : 9 7 5 3 1
argument: 5, 8
return value: 1, 0
after : 9 7 3 1
(3) erase(const_iterator, const_iterator) before : 9 7 5 3 1
arguments: 7, 3
return value: 3
after : 9 3 1</pre>
```

注：<code style='color:black'>[unordered_set](/reference/unordered_set/unordered_set.md)</code> は非順序連想コンテナであるため、出力順序は無意味であることに注意


##バージョン


###言語

- C++11

###処理系

- [Clang](/implementation#clang.md): -

- [Clang, C++0x mode](/implementation#clang.md): 3.1

- [GCC](/implementation#gcc.md): -

- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0

- [ICC](/implementation#icc.md): ?

- [Visual C++](/implementation#visual_cpp.md): ?

##参照


| | |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
|<code style='color:black'>[emplace](/reference/unordered_set/unordered_set/emplace.md)</code> |コンテナ内への要素の直接構築 |
|<code style='color:black'>[emplace_hint](/reference/unordered_set/unordered_set/emplace_hint.md)</code> |挿入位置のヒントを使用したコンテナ内への要素の直接構築 |
|<code style='color:black'>[insert](/reference/unordered_set/unordered_set/insert.md)</code> |要素の追加 |
|<code style='color:black'>[clear](/reference/unordered_set/unordered_set/clear.md)</code> |全要素の削除 |
|<code style='color:black'>[swap](/reference/unordered_set/unordered_set/swap.md)</code> |内容の交換 |