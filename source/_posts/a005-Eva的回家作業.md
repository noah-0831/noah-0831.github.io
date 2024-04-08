---
title: a005. Eva的回家作業
date: 2024-02-23 17:02:29
categories: 程式教學
tags: C語言
---
## 題目連結
https://zerojudge.tw/ShowProblem?problemid=a005

## 解題思路
由題意可知輸入的數列只有等差數列或等比數列兩種可能。先用if_else條件句判斷輸入數列為等差數列還是等比數列，再依據等差數列兩相鄰項差相同、等比數列兩相鄰項比相同的性質推知第五項。

<!-- more -->

## 注意事項
根據題意，測資檔會包含多組測資，因此可使用[for迴圈](https://openhome.cc/Gossip/CGossip/forStatement.html)判斷程式執行的條件。

## 程式碼：C語言
```C==
#include <stdio.h>
int main() {
    // 宣告並讀取變數t，代表數列的數目
    int t;
    scanf("%d", &t);
    // 使用for迴圈分別討論每一個數列的情況
    for(int i = 0 ; i < t ; i++) {
        // 宣告並讀取陣列a[4]，代表輸入數列的前四項
        int a[4];
        scanf("%d %d %d %d", &a[0], &a[1], &a[2], &a[3]);
        // 若數列任兩項間的差相同，即為等差數列
        if(a[1]-a[0] == a[2]-a[1])
            printf("%d %d %d %d %d\n", a[0], a[1], a[2], a[3], a[3]+(a[1]-a[0]));
        // 若否，即為等比數列
        else
            printf("%d %d %d %d %d\n", a[0], a[1], a[2], a[3], a[3]*(a[1]/a[0]));
    }
    return 0;
}
```