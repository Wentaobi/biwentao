---
title: "Modern C++ 100 Questions | 02 User defined literals _f"
date: "2014-02-19"
description: "User defined literals _f"
tags:
  - pipe operator
  - lambda function
---

This article offers a sample of basic Markdown syntax that can be used in Hugo content files, also it shows whether basic HTML elements are decorated with CSS in a Hugo theme.

<!--more-->

## `02` User defined literals _f

**Requirements**：

1. Please don't change `main` function.
2. Please implement your function/code to get **Expected results**.

```cpp {linenos=true}
int main(){
    std::cout << "乐 :{} *\n"_f(5);
    std::cout << "乐 :{0} {0} *\n"_f(5);
    std::cout << "乐 :{:b} *\n"_f(0b01010101);
    std::cout << "{:*<10}"_f("卢瑟");
    std::cout << '\n';
    int n{};
    std::cin >> n;
    std::cout << "π：{:.{}f}\n"_f(std::numbers::pi_v<double>, n);
}
```

### Expected results

```text
乐 :5 *
乐 :5 5 *
乐 :1010101 *
卢瑟******
6
π：3.141593
```

### Suggested environments

[Compiler explorer](https://godbolt.org/), please add **--std=c++20** to the compilation options.

### My implementation

[Reference code](https://zhuanlan.zhihu.com/p/679162013), please use browser to translate page from Chinese to English if necessary.
