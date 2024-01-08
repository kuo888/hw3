目的為檢查一個條件是否為真

1.void assert(int expression);  //判斷一個表達式是否正確
```
#include<assert.h>
#include<stdio.h>
int main(void){ 
   int a=50;
   assert(a<80);   //判斷a<80,如果為0输出錯誤信息终止程序，否則繼續執行 
   printf("Assert a is true\n"); 
   return(0); 
}
```
(出自C語言網)



2.
