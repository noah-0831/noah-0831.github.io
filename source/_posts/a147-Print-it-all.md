---
title: a147. Print it all
date: 2024-04-07 11:46:43
categories: 程式教學
tags: C語言
---
## 題目連結
https://zerojudge.tw/ShowProblem?problemid=a147

## 解題思路
利用for迴圈檢查1到n-1的所有整數是否可被7整除，若該數除以7之後的餘數不為0，代表該數不能被7整除，就將其輸出。

## 注意事項
根據題意，測資檔會包含多組測資，直到n等於0代表輸入結束。可能有人會想用while(scanf("%d", &n) != 0)這樣的寫法判斷程式結束執行的條件，但須注意scanf()函式沒有[回傳值](https://noah-0831.github.io/a002-%E7%B0%A1%E6%98%93%E5%8A%A0%E6%B3%95/)，也就是說他僅會將讀取到的數值存入變數中，而不會回傳，因此這項判斷條件永遠不會成立。如果要使用scanf()函式讀取到的輸入作為判斷條件，必須要先將輸入用指定的變數存起來，再使用該變數的值。

<!-- more -->

## 程式碼：C語言
```C==
#include <stdio.h>
int main() {
    //宣告變數n，代表判斷範圍的上限
    int n;
    //用while迴圈重複讀取變數n
    while(scanf("%d", &n)) {
        //若n為0，代表輸入結束，直接跳出迴圈
        if(n == 0)
            break;
        //檢查1到n-1之間的整數是否可被7整除
        for(int num = 1 ; num < n ; num++)
            //若該數除以7之後的餘數不為，代表該數不能被7整除，需輸出
            if(num%7 != 0)
               printf("%d ", num);
        printf("\n");
    }
    return 0;
}
```

