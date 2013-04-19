#is_object
```cpp
namespace std {  template <class T>  struct is_object;}
```

##概要

<b>型Tがオブジェクト型か調べる。オブジェクト型は、スカラ型、配列型、共用型、クラス型、およびそれらのcv修飾を含む。</b>


##効果

`is_object`は、型`T`がオブジェクト型であるならば[`true_type`](/reference/type_traits/integral_constant-true_type-false_type.md)から派生し、そうでなければ[`false_type`](/reference/type_traits/integral_constant-true_type-false_type.md)から派生する。


##例

```cpp
#include <type_traits>static_assert(std::is_object<int>::value == true, "value == true, int is object");static_assert(std::is_same<std::is_object<int>::value_type, bool>::value, "value_type == bool");static_assert(std::is_same<std::is_object<int>::type, std::true_type>::value, "type == true_type");static_assert(std::is_object<int>() == true, "is_object<int>() == true");static_assert(std::is_object<void>::value == false, "value == false, void is not object");static_assert(std::is_same<std::is_object<void>::value_type, bool>::value, "value_type == bool");static_assert(std::is_same<std::is_object<void>::type, std::false_type>::value, "type == false_type");static_assert(std::is_object<void>() == false, "is_object<void>() == false");enum e{};class c{};union u{};static_assert(std::is_object<e>::value == true, "enum is object");static_assert(std::is_object<c>::value == true, "class is object");static_assert(std::is_object<u>::value == true, "union is object");static_assert(std::is_object<const volatile int>::value == true, "const volatile int is object");static_assert(std::is_object<int*>::value == true, "int* is object");static_assert(std::is_object<int[1]>::value == true, "int[1] is object");static_assert(std::is_object<int&>::value == false, "int& is not object");static_assert(std::is_object<int ()>::value == false, "int () is not object");static_assert(std::is_object<std::nullptr_t>::value == true, "std::nullptr_t is object");int main(){}
```

###出力

```cpp
```

##バージョン
```
###言語


- C++11



###処理系

- [GCC, C++0x mode](/implementation#gcc.md): 4.3.4, 4.5.3, 4.6.2, 4.7.0
- [Visual C++](/implementation#visual_cpp.md) 10.0<h4>備考</h4>
上の例でコンパイラによってはエラーになる。GCC 4.3.4, 4.5.3, Visual C++ 10.0 は integral_constant が operator bool を持っていないためエラーになる。

