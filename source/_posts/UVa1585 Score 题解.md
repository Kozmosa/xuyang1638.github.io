---
title: UVa1585 Score 题解
author: xuyang1638
date: 2020-03-31
---
[UVa1585 题目原地址](https://onlinejudge.org/external/15/1585.pdf)

本体思路重点在于分数的统计及重置。
由题面可得输入的是一个小于80个字符的字符串，故使用一个字符数组存储。

更新 2020/3/1 11:52
傻了，uva评测太慢代码挂上就先去摸鱼，结果一看wa了。看了下代码，只写了主功能函数。给定的输入有多个kase...
代码更新如下（ifdef内的是调试代码，可去掉）：
```cpp
#include <stdio.h>
#include <cstdlib>

int getScore() {
 int quantity = 0;
 int score = 0;
 char inputs[80] = {};

 scanf("%s", inputs);
 #ifdef DEBUG
 printf("Current string: %s\n", inputs);
 #endif

 for(int i = 0; i <= 80; i++){
  if(inputs[i] == 'O') {
   quantity++;
   score += quantity;
   #ifdef DEBUG
   printf("Current quantity of O: %d\n", quantity);
   printf("Score: %d\n\n", score);
   #endif
  }
  if(inputs[i] == 'X') {
   quantity = 0;
   #ifdef DEBUG
   printf("Current character is X.\n");
   printf("Score: %d\n\n", score);
   #endif
  }
 }
 
 return score;
}

int main(void){

 #ifdef DEBUG
 freopen("data.in", "r", stdin);
 #endif

 int *scores;
 
 int kase_quantity = 0;
 scanf("%d", &kase_quantity);
 // create a array to save scores of each kase
 scores = (int*)calloc(kase_quantity, sizeof(int));

 for(int i = 0; i <= kase_quantity; i++) {
  int score = getScore();
  scores[i] = score;
 }
 for(int i = 0; i < kase_quantity; i++) {
  printf("%d\n", scores[i]);
 }

 // free memory used by scores array
 free(scores);

 return 0;
}
```

废话不多说，代码如下：
```cpp
#include <stdio.h>

int main(void){
 char inputs[80];
 int quantity = 1;
 int score;
 
 scanf("%s", inputs);
 for(int i = 0; i <= 80; i++){
  if(inputs[i] == 'O') {
   score += quantity;
   quantity++;
  }
  if(inputs[i] == 'X') {
   quantity = 1;
  }
 }

 printf("%d\n", score);
 
 return 0;
}
```