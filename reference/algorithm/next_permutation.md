#next_permutation
```cpp
namespace std {
  template<class BidirectionalIterator>
  bool next_permutation(BidirectionalIterator first,
                        BidirectionalIterator last);

  template<class BidirectionalIterator, class Compare>
  bool next_permutation(BidirectionalIterator first,
                        BidirectionalIterator last,
                        Compare comp);
}
```

##概要

<b>次の順列を生成する。</b>


##要件

BidriectionalIteratorがValueSwappableの要件を満たしていること。


##効果

[first, last)の範囲を次の順列に変換する。

operator<またはcompによって辞書順に並んでいる全ての順列の集合があると仮定すると、次の順列が発見される。


##戻り値

次の順列が存在する場合はtrueを返し、そうでなければfalseを返す。


##計算量

高々`(last - first)/2`回の要素の交換


##例

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void print(const std::vector<int>& v)
{
  std::for_each(v.begin(), v.end(), [](int x) {
    std::cout << x << " ";
  });
  std::cout << std::endl;
}

int main ()
{
  std::vector<int> v = {1, 2, 3};

  do {
    print(v);
  } while (std::next_permutation(v.begin(), v.end()));
}
```
* next_permutation(v.begin(), v.end()));[color ff0000]

###出力

```cpp
1 2 3 
1 3 2 
2 1 3 
2 3 1 
3 1 2 
3 2 1 
```

##実装例

```cpp
template <class BidirectionalIterator, class Compare>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last, Compare comp)
{
  if (first == last)
    return false;

  BidirectionalIterator i = first;
  ++i;

  if (i == last)
    return false;

  i = last;
  --i;

  for(;;) {
    BidirectionalIterator ii = i;
    --i;
    if (comp(*i, *ii)) {
      BidirectionalIterator j = last;
      while (!comp(*i, *--j)) {}

      std::swap(*i, *j);
      std::reverse(ii, last);
      return true;
    }
    if (i == first) {
      std::reverse(first, last);
      return false;
    }
  }
}

template <class BidirectionalIterator>
bool next_permutation(BidirectionalIterator first, BidirectionalIterator last)
{
  typedef
    typename std::iterator_traits<BidirectionalIterator>::value_type
  value_type;

  return next_permutation(first, last, std::less<value_type>());
}
```

##参照

