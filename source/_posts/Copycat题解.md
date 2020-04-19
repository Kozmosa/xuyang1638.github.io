---
title: LOJ#3 Copycat 题解
author: xuyang1638
date: 2020-04-01
---
代码如下：（提交时请使用C++(NOI)编译）
```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    freopen("copycat.in", "r", stdin);
    freopen("copycat.out", "w", stdout);

    int quantity;
    cin >> quantity;
    string a;
    for (int i = 1; i <= quantity; i++) {
        cin >> a;
        cout << a << endl;
    }

    return 0;
}
```

记录一下我写这道题的过程吧，说来真是话长。
本来这道题是loj的第三题，纯测试文件读写用的。然后我看题的时候，题面有一句“请注意使用文件输入输出，而非标准输入输出。”，导致我一直在使用fin及fout读写，使用的int以及long long在第九个点都爆了内存。调了很久，在本机上样例运行正常，但是上了测试机之后莫名其妙的就wa，一分都没有。
实在懵逼，于是去看了下别人写的题解，入眼就是一个freopen，原本以为控制台流重定向不能用的说...
于是改成这样了，读入的变量要采用string类型，因为第三个子任务的数据量是<=10^1000的，用long long都会爆内存。