---
title: "Modern C++ 100 Questions | 01"
date: "2014-01-25"
description: "Implement pipe operator"
tags:
  - pipe operator
  - lambda function
  - template
---

This article offers a sample of basic Markdown syntax that can be used in Hugo content files, also it shows whether basic HTML elements are decorated with CSS in a Hugo theme.

<!--more-->

## `01` Implement pipe operator

**Requirements**：

1. Please don't change `main` function.
2. Please implement your function/code to get **Expected results**.

```cpp {linenos=true}
int main()
{
    std::vector v{1, 2, 3};
    std::function f {[](const int& i) {std::cout << i << ' '; } };
    auto f2 = [](int& i) {i *= i; };
    v | f2 | f;
}
```

### Expected results

```text
1 4 9
```

### Suggested environments

[Compiler explorer](https://godbolt.org/), please add **--std=c++20** to the compilation options.


### My implementation

[Reference code](https://zhuanlan.zhihu.com/p/679162013), please use browser to translate page from Chinese to English if necessary.
