---
title: a053. Sagit's 計分程式
date: 2024-03-15 22:51:08
categories: 程式教學
tags: C語言
---
## 題目連結
https://zerojudge.tw/ShowProblem?problemid=a053

## 解題思路
以if_else條件句判斷答對題數的情形，並輸出相對應的輸出。

<!-- more -->

## 注意事項
在C語言裡，一個條件句只能有一個關係運算子，因此平時書寫的寫法10 < N <20，需改寫成10 < N && N < 20。

## 程式碼：C語言
```C==
#include <stdio.h>
int main() {
    //宣告並讀取變數N，代表答對題數
    int N;
    scanf("%d", &N);
    //答對題數在 0~10 者，每題給6分
    if(N <= 10)
        printf("%d", 6*N);
    //題數在 11~20 者，從第11題開始，每題給2分
    else if(10 < N && N <= 20)
        printf("%d", 60+2*(N-10));
    //題數在 21~40 者，從第21題開始，每題給1分
    else if(20 < N && N <= 40)
        printf("%d", 80+1*(N-20));
    //題數在 40 以上者，一律100分
    else
        printf("100");
    return 0;
}
```