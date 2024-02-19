---
title: "Modern C++ 100 Questions | 05 Implement scope_guard"
date: "2014-02-19"
description: "Implement scope_guard"
tags:
  - scope_guard
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
#include <cstdio>
#include <cassert>

#include <stdexcept>
#include <iostream>
#include <functional>

struct X {
    X() { puts("X()"); }
    X(const X&) { puts("X(const X&)"); }
    X(X&&) noexcept { puts("X(X&&)"); }
    ~X() { puts("~X()"); }
};

int main() {
    {
        // scope_guard的作用之一，是让各种C风格指针接口作为局部变量时也能得到RAII支持
        // 这也是本题的基础要求
        FILE * fp = nullptr;
        try{
            fp = fopen("test.txt","a");
            auto guard = scope_guard([&] {
                fclose(fp);
                fp = nullptr;
            });

            throw std::runtime_error{"Test"};
        } catch(std::exception & e){
            puts(e.what());
        }
        assert(fp == nullptr);
    }
    puts("----------");
    {
        // 附加要求1，支持函数对象调用
        struct Test {
            void operator()(X* x) {
                delete x;
            }
        } t;
        auto x = new X{};
        auto guard = scope_guard(t, x);
    }
    puts("----------");
    {
        // 附加要求2，支持成员函数和std::ref
        auto x = new X{};
        {
            struct Test {
                void f(X*& px) {
                    delete px;
                    px = nullptr;
                }
            } t;
            auto guard = scope_guard{&Test::f, &t, std::ref(x)};
        }
        assert(x == nullptr);
    }
}
```

### Expected results

```text
Test
----------
X()
~X()
----------
X()
~X()
```

### Suggested environments

[Compiler explorer](https://godbolt.org/), please add **--std=c++20** to the compilation options.

### My implementation

[Reference code][def], please use browser to translate page from Chinese to English if necessary.

[def]: https://zhuanlan.zhihu.com/p/681521425