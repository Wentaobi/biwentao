---
title: "Modern C++ 100 Questions | 03 Template specification with std::formatter"
date: "2014-02-19"
description: "Template specification with std::formatter"
tags:
  - template specification
  - std::formatter
  - template
---

This article offers a sample of basic Markdown syntax that can be used in Hugo content files, also it shows whether basic HTML elements are decorated with CSS in a Hugo theme.

<!--more-->

## `03` Template specification with std::formatter

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

struct Frac {
   int a, b;
};

Frac f{ 1,10 };
print("{}", f);// result: 1/10
```

### Expected results

```text
1/10
```

### Suggested environments

[Compiler explorer](https://godbolt.org/), please add **--std=c++20** to the compilation options.

### My implementation

[Reference code][def], please use browser to translate page from Chinese to English if necessary.

[def]: https://zhuanlan.zhihu.com/p/680736404
