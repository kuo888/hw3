1.time()   //用來回傳日曆的時間，也就是自 1970 年 1 月 1 日後經過的總秒數
```
#include <stdio.h>
#include <time.h>

int main(void)
{
    time_t t1 = time(NULL);
    
    printf("自 1970 年 1 月 1 日後經過了 %d 秒....\n", t1);
    
    return 0;
}
```
(出自c語言網)



2.clock()  //用來回傳程式執行後佔用的 CPU 時間，單位為tick 
```
#include <stdio.h>
#include <time.h>

int main(void)
{
    long fiveseconds = CLOCKS_PER_SEC * 5;
    
    printf("程式開始執行，準備暫停五秒...\n");
    while (clock() < fiveseconds) {
    }
    
    printf("五秒過後，程式執行結束...\n");
    
    return 0;
}
```
(出自c語言網)



3.difftime() //用來計算兩個 time_t 型態參數的時間差
```
#include <stdio.h>
#include <time.h>

int main(void)
{
    char c;
    time_t t1, t2;
    
    t1 = time(NULL);
    
    printf("請輸入小寫字母 q 結束迴圈\n");
    while ((c = getchar()) != 'q') {  //getchar()為讀取字元
        if (c == '\n') {
            continue;
        }
    }
    
    t2 = time(NULL);
    printf("此程式共執行 %d 秒...\n", (int) difftime(t2, t1));
    
    return 0;
}
```
(出自c語言網)



4.mktime() //用來指向結構 (structure) tm 的指標當作參數，回傳此 tm 所表示的日曆時間
```
#include <stdio.h>
#include <time.h>

int main(void)
{
    time_t n;
    struct tm t1;
    t1.tm_sec = 8;
    t1.tm_min = 12;
    t1.tm_hour = 3;
    t1.tm_mday = 22;
    t1.tm_mon = 3;
    t1.tm_year = 1999-1900;
    t1.tm_wday = 1;
    t1.tm_yday = 81;
    t1.tm_isdst = -1;
    
    n = mktime(&t1);
    printf("西元 1999 年 3 月 22 日 3 點 12 分 8 秒共累計了 %u 秒....\n", n);
    
    return 0;
}
```
(出自c語言網)



5.localtime()  //用來指向日曆時間的指標當作參數，將此日曆時間轉換成結構 (structure) tm 的表示方法，並回傳表示此結構 tm
```
#include <stdio.h>
#include <time.h>

int main(void)
{
    time_t t1 = time(NULL);
    struct tm *nPtr = localtime(&t1);
    int year = nPtr->tm_year + 1900;
    int month = nPtr->tm_mon + 1;
    int mday = nPtr->tm_mday;
    int wday = nPtr->tm_wday;
    
    printf("今天是 %u 年 %u 月 %u 號星期 %u\n", year, month, mday, wday);
    
    return 0;
}

```
(出自c語言網)



6.char *asctime（const struct tm *t）;   //將給定的日期和時間轉換成ASCII碼
```
#include<time.h>
 
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   struct tm t;
 
   char str[80];
 
   t.tm_sec = 1;
 
   t.tm_min = 30;
 
   t.tm_hour = 9;
 
   t.tm_mday = 22;
 
   t.tm_mon = 11; 
 
   t.tm_year = 56;
 
   t.tm_wday = 4;
 
   t.tm_yday = 0;     //不显示
 
   t.tm_isdst = 0;    //不实行夏令时
 
   strcpy(str, asctime(&t));
 
   printf("%s\n", str);
 
   return 0;
 
}

```
(出自c語言網)



7.char *ctime（const time_t *time）;    //把日期和時間轉換為字串
```
#include<stdio.h>
 
#include<time.h>
 
int main(void){
 
   time_t t;    //typedef long time_t;
 
   time(&t);    //获取系统时间
 
   char *str=ctime(&t);  //将时间t转换为字符串
 
   printf("Today's date and time: %s\n",str); 
 
   return 0;
 
}
```
(出自c語言網)



8.struct tm *gmtime（long *clock）;   //把clock中的時間轉換為格林尼治標準時間
```
#include<stdio.h>
 
#include<time.h>
 
int main(void){
 
   time_t t;
 
   struct tm *gmt, *area;
 
   t = time(NULL);
 
   area = localtime(&t);
 
   printf("Local time is: %s", asctime(area));
 
   gmt = gmtime(&t);
 
   printf("GMT is: %s", asctime(gmt));
 
   return 0;
 
}
```
(出自c語言網)



9.void tzset（void）;  // 對UNIX作業系統的時間相容性
```
#include<stdio.h>
 
#include<time.h>
 
int main(void){
 
   time_t td;
 
   if(putenv("TZ=PST8PDT")==-1){  // 设置环境变量，并判断是否成功
 
      printf("Unable to set tz\n");
 
      return 0;
 
   }
 
   tzset();  //设置UNIX时间兼容
 
   time(&td);
 
   printf("Current time = %s\n", asctime(localtime(&td)));
 
   return 0;
 
}
```
(出自c語言網)
