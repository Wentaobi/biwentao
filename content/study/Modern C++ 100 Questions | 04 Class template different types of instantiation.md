---
title: "Modern C++ 100 Questions | 04 Class template different types of instantiation"
date: "2014-02-19"
description: "Implement pipe operator"
tags:
  - static
  - lambda function
  - template
---

This article offers a sample of basic Markdown syntax that can be used in Hugo content files, also it shows whether basic HTML elements are decorated with CSS in a Hugo theme.

<!--more-->

## `04` Class template different types of instantiation

**Requirements**：

1. Please don't change `main` function.
2. Please implement your function/code to get **Expected results**.

```cpp {linenos=true}
#include<iostream>
class ComponentBase{
protected:
    static inline std::size_t component_type_count = 0;
};
template<typename T>
class Component : public ComponentBase{
public:
    // todo...
    // Change the current template class in any way so that for any type X, if it inherits from Component

    // Then X::component type id() will get a unique id of type size t (different values should be returned for different X types)值应不同）
    // Requirements: std::type info cannot be used (the typeid keyword is disabled), and all ids are consecutive starting from 0
};
class A : public Component<A>
{};
class B : public Component<B>
{};
class C : public Component<C>
{};
int main()
{
    std::cout << A::component_type_id() << std::endl;
    std::cout << B::component_type_id() << std::endl;
    std::cout << B::component_type_id() << std::endl;
    std::cout << A::component_type_id() << std::endl;
    std::cout << A::component_type_id() << std::endl;
    std::cout << C::component_type_id() << std::endl;
}
```

### Expected results

```text
0
1
1
0
0
2
```

### Suggested environments

[Compiler explorer](https://godbolt.org/), please add **--std=c++20** to the compilation options.

### My implementation

[Reference code][def], please use browser to translate page from Chinese to English if necessary.

[def]: https://zhuanlan.zhihu.com/p/681510902