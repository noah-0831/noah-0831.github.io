---
title: a148. You Cannot Pass?!
date: 2024-04-08 01:33:57
categories: 程式教學
tags: C語言
---
## 題目連結
https://zerojudge.tw/ShowProblem?problemid=a148

## 解題思路
題目有多筆測資，當輸入為n時，代表題目希望我們對接下來輸入的n筆成績取平均，再依照平均是否大於59判斷是否過關。我們可以用for迴圈讀取n筆成績並將他們相加，除以n即可得到平均，再依照取完平均後的結果輸出相對應的輸出。

<!-- more -->

## 注意事項
注意平均可能為小數，如果用整數型態判斷的話可能會出現誤差。舉例來說，假設今天我們計算出來的平均為59.79，顯然是大於59分的，但若是用整數型態儲存只會存到59。因此此題我們需將平均先轉成浮點數再做判斷。

## 程式碼：C語言
```C==
#include <stdio.h>
int main() {
    //宣告變數n，代表成績筆數
    int n;
    //使用EOF寫法判斷程式執行的條件
    while(scanf("%d", &n) != EOF) {
        //宣告變數score，代表輸入的成績
        //宣告變數sum，賦值為0，代表總成績
        int score, sum = 0;
        //用for迴圈讀取n筆成績，並將他們相加得到總成績
        for(int i = 0 ; i < n ; i++) {
            scanf("%d", &score);
            sum += score;
        }
        //若平均大於59.0分，則輸出"no"
        if((float)sum/n > 59.0)
            printf("no\n");
        //若否，則輸出"yes"
        else
            printf("yes\n");
    }
    return 0;
}
```