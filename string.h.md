1.size_t strlen(const char *str)  //用來計算字串str的長度，但不包括終止空字符
```
#include <stdio.h>
#include <string.h>

int main ()
{
   char str[50];
   int len;

   strcpy(str, "This is gitbook.net");

   len = strlen(str);
   printf("Length of |%s| is |%d|", str, len);
   
   return(0);
}
```
(出自c語言網)



2.int strncmp(const char *str1, const char *str2, size_t n)  // 用來比較前n個字節str1和str2 ，n為最大字符數進行比較
```
#include <stdio.h>
#include <string.h>

int main ()
{
   char str1[15];
   char str2[15];
   int ret;

   strcpy(str1, "abcdef");
   strcpy(str2, "ABCDEF");

   ret = strncmp(str1, str2, 4);

   if(ret > 0)  //代表str2<str1
   {
      printf("str1 is less than str2");
   }
   else if(ret < 0)  //代表str2>str1
   {
      printf("str2 is less than str1");
   }
   else  //ret==0，代表str1=str2
   {
      printf("str1 is equal to str2");
   }
   
   return(0);
}
```
(出自c語言網)



3.void *memcpy(void *str1, const void *str2, size_t n)  //用來拷貝n個字符從存儲區str2中內存區域到str1。str1是指針數組，目的是將被複製到目標；str2 是只要複製的數據源的指針；str2 -- 這是要複製的數據源的指針
```
#include <stdio.h>
#include <string.h>

int main ()
{
   const char src[50] = "http://www.gitbook.net/html";
   char dest[50];

   printf("Before memcpy dest = %s
", dest);
   memcpy(dest, src, strlen(src)+1);
   printf("After memcpy dest = %s
", dest);
   
   return(0);
}
```
(出自c語言網)



4.void *memmove(void *str1, const void *str2, size_t n) 。用來從某一記憶體區段拷貝 n 個字元相接到另一記憶體區段的後端。str1是指針數組，目的為將被複製到目標，類型強制轉換為void*類型的指針。str2為要複製的數據源的。針。n是指要被複製的字節數。
```
#include <stdio.h>
#include <string.h>

int main(void)
{
    char s[20] = "out of work";
    char t[20] = "future";
    
    memmove(s, t, 6);
    
    printf("%s\n", s);
    
    return 0;    
}
```
(出自c速查手冊)



5.void *memset(void *str, int c, size_t n)  //用來將某一記憶體區段的前 n 個字元全部設定為某一字元。str代表是來填充的內存塊的指針。c用來要設置的值。作為一個int值傳遞，但使用這個值的無符號字符型轉換函數填充的內存塊。n是指要設置的值的字節數。

以下的程式是將string全部設成'n'
```
#include <stdio.h>
#include <string.h>

int main(void)
{
    char s[] = "congratulation";
    
    printf("%s\n", memset(s, 'n', 13));
    
    return 0;    
}
```
(出自c速查手冊)



6.strcpy（）    //拷貝一個字串到另一個字串陣列中(注意:必須保證 destin 足夠大，能夠容納下 source，否則會導致溢出錯誤。)
```
#include <string.h>
 
#include <stdio.h>
 
int main(void) {
 
   char string[10];
 
   char *str1 = "www.dotcpp.com";
 
   strcpy(string, str1);
 
   printf("%s\n", string);
 
   return 0;
 
}
```
(出自c速查手冊)



7.strcat（）    //將一個字串拼接在目標字串的後面
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char destination[25]={"I love"};
 
   char *blank = " ", *c = "www.dotcpp.com";
 
   strcat(destination, blank);
 
   strcat(destination, c);
 
   printf("%s\n", destination);
 
   return 0;
 
}
```
(出自c速查手冊)



8.int strcmp（const char *str1，const char *str2）;    // 比較兩個字串的大小，區分大小寫(str1 < str2傳回 -1，str1 == str2傳回 0)
```
#include <string.h>
 
#include <stdio.h>
 
int main(void) {
 
   char *buf1 = "aaa", *buf2 = "bbb", *buf3 = "ccc";
 
   int ptr = strcmp(buf2, buf1);
 
   if (ptr > 0) {
 
      printf("buffer 2 is greater than buffer 1\n");
 
   }else if(ptr < 0){
 
      printf("buffer 2 is less than buffer 1\n");
 
   }else{
 
      printf("buffer 2 is equals buffer 1\n");
 
   }
 
   ptr = strcmp(buf2, buf3);
 
   if (ptr > 0) {
 
      printf("buffer 2 is greater than buffer 3\n");
 
   }else if(ptr < 0){
 
      printf("buffer 2 is less than buffer 3\n");
 
   }else{
 
      printf("buffer 2 is equals buffer 3\n");
 
   }
 
   return 0;
 
}
```
(出自c速查手冊)



9.char *strchr（const char *str， char c）;    //尋找字串中第一個出現的指定字元的位置
```
#include <string.h>
 
#include <stdio.h>
 
int main(void) {
 
   char string[15]; //定义字符数组
 
   char *ptr, c = 'c'; 
 
   strcpy(string, "www.dotcpp.com"); //复制字符串
 
   ptr = strchr(string, c); //查找字符出现的第一个位置
 
   if (ptr) {
 
      printf("The character %c is at position: %d\n", c, ptr-string);
 
   }else{
 
      printf("The character was not found\n");
 
   }
 
   return 0;
 
}
```
(出自c速查手冊)



10.int strcmpi（char *str1， char *str2）;    //比較兩個字元串的大小(str1>str2 返回1;str1==str2 返回0;str1<str2 返回-1;)
```
#include <string.h>
 
#include <stdio.h>
 
  
 
int main(void){
 
   char *buf1 = "www.dotcpp.com", *buf2 = "WWW.DOTCPP.COM";
 
   int ptr = strcmpi(buf2, buf1);
 
   if(ptr > 0){
 
      printf("buffer 2 is greater than buffer 1\n");
 
   }
 
   if(ptr < 0){
 
      printf("buffer 2 is less than buffer 1\n");
 
   }
 
   if(ptr == 0){
 
      printf("buffer 2 equals buffer 1\n");
 
   }
 
   return 0;
 
}
```
(出自c速查手冊)



11.strcspn（）    //查找連續有幾個字元都不屬於字串str2內的字元
```
#include <string.h>
 
#include <stdio.h>
 
int main(void){
 
   char *string1 = "1234567890";
 
   char *string2 = "747DC8";
 
   int length = strcspn(string1,string2);
 
   printf("Character where strings intersect is at position %d\n", length);
 
   return 0;
 
}
 
```
(出自c速查手冊)



12.int strspn（char *str1， char *str2）;     //計算字串str1中連續有幾個字元都屬於字串str2
```
#include <string.h>
 
#include <stdio.h>
 
int main(void){
 
   char *string1 = "1234567890";
 
   char *string2 = "123DC8";
 
   int length = strspn(string1, string2);
 
   printf("Character where strings differ is at position %d\n", length);
 
   return 0;
 
}
```
(出自c速查手冊)



13.int stricmp（const char *str1， const char *str2）;     //比較兩個字元串大小
```
#include <string.h>
 
#include <stdio.h>
 
int main(void) {
 
   char *buf1 = "WWW.DOTCPP.COM", *buf2 = "www.dotcpp.com";
 
   int ptr = stricmp(buf2, buf1);
 
   if (ptr > 0) {
 
      printf("buffer 2 is greater than buffer 1\n");
 
   }
 
   if (ptr < 0){
 
      printf("buffer 2 is less than buffer 1\n");
 
   }
 
   if (ptr == 0) {
 
      printf("buffer 2 equals buffer 1\n");
 
   }
 
   return 0;
 
}
```
(出自c速查手冊)



14.char *strlwr（char *str）;    // 將字串中的大寫字母全部轉換成小寫形式
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
    char str[20]="WWw.DoTCPP.COM";
 
     char *str2=strlwr(str);
 
    printf("%s\n",str);
 
   return 0;  
 
}
```
(出自c速查手冊)



15.char *strncat(char *destin,char *str,int n);    //在字符串尾部追加
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char destin[30]="I like ";
 
   char *str="www.dotcpp.com very much"; 
 
   int n=14;
 
   char *newStr=strncat(destin,str,n);
 
   printf("%s\n",newStr);
 
   return 0;
 
}
```
(出自c速查手冊)



16.int strncmp（const char *str1，const char *str2，int n）;     //對指定字串數量的兩個字串進行比較 (str1 > str2 返回大於0的值;str1==str2 返回等於0的值;str1 < str2 返回小於0的值;)
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char *s1="www.dotcpp",*s2="dotcpp.com",*s3="dotcpp";
 
   int p=strncmp(s2,s1,3);
 
   if(p>0){
 
      printf("s2 is greater than s1\n");
 
   }else if(p<0){
 
      printf("s2 is less than s1\n");
 
   }else{
 
      printf("s2 is equals s1\n");
 
   }
 
   p=strncmp(s2,s3,3);
 
   if(p>0){
 
      printf("s2 is greater than s3\n");
 
   }else if(p<0){
 
      printf("s2 is less than s3\n");
 
   }else{
 
      printf("s2 is equals s3\n");
 
   }
 
   return 0;  
 
}
```
(出自c速查手冊)



17.int strnicmp（const char *str1，const char *str2，unsigned n）;    //對指定長度的兩個字元串進行比較
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char *str1="www.dotcpp.com";
 
   char *str2="WWW.DOTCPP.COM";
 
   int p=strnicmp(str2,str1,3);
 
   if(p>0){
 
      printf("str2 is greater than str1\n");
 
   }else if(p<0){
 
      printf("str2 is less than str1\n");
 
   }else{
 
      printf("str2 is equals str1\n");
 
   }
 
   return 0;  
 
}
```
(出自c速查手冊)



18.char *strncpy（char *destin，const char *source，int n）;     //將指定數量的源字串拼接在目標字串的後面
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char *source="www.dotcpp.com very much!";
 
   char destin[30]={"Good Luck!"};
 
   strncpy(destin,source,14);
 
   printf("%s\n",destin);
 
   return 0;  
 
}
```
(出自c速查手冊)



19.char *strpbrk（const char *str1， const char *str2）;     //比較字串str1和str2中是否有相同的字元，但不包括結束符'\0'
```
#include <string.h>
 
#include <stdio.h>
 
int main(void){
 
   char *str1 = "www.dotcpp.com";
 
   char *str2 = "cde";
 
   char *ptr = strpbrk(str1, str2);
 
   if(ptr){
 
      printf("strpbrk found first character: %c\n", *ptr);
 
   }else{
 
      printf("strpbrk didn't find character in set\n");
 
   }
 
   return 0;
 
}
 
```
(出自c速查手冊)



20.char *strrev（char *str）;    //將字串中的字元全部顛倒順序，重新排序
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char forward[20] = "www.dotcpp.com";
 
   printf("Before strrev(): %s\n", forward);
 
   strrev(forward);
 
   printf("After strrev(): %s\n", forward);
 
   return 0;
 
}
```
(出自c速查手冊)



21.char *strset（char *str， char c）;    //將一個字元串中的所有字元都設為指定字元
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char string[20] = "www.dotcpp.com";
 
   char symbol = 'c';
 
   printf("Before strset(): %s\n", string);
 
   strset(string, symbol);
 
   printf("After  strset(): %s\n", string);
 
   return 0;
 
}
```
(出自c速查手冊)



22.char *strstr（const char *destin， const char *str）;   //在一個字串中查找另一個字串首次出現的位置
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char *str1 = "I like www.dotcpp.com very much!", *str2 = "www.dotcpp.com";
 
char *ptr = strstr(str1, str2);
 
   printf("The substring is: %s\n", ptr);
 
   return 0;
 
}
```
(出自c速查手冊)



23.char *strtok（char *str1， const char *str2）;   //用指定的分隔符分解字元串
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char input[50] = "I like www.dotcpp.com very much";
 
   char *p = strtok(input, " ");
 
   if(p){
 
      printf("%s\n", p);
 
   }
 
   while(p=strtok(NULL, " ")){//使用第一个参数为NULL来提取子串
 
      printf("%s\n", p);
 
   }
 
   return 0;
 
}
```
(出自c速查手冊)



24.strupr（）   //將字串中的小寫字母全部轉換成大寫形式
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char str[20] = "wWw.dotCpp.coM", *ptr;
 
   ptr = strupr(str);
 
   printf("%s\n", ptr);
 
   return 0;
 
}
```
(出自c速查手冊)



25.char *strnset（char *str， char ch， unsigned n）;    //指定字串的前幾個字元都設為指定字元
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char string[50] = "I like www.dotcpp.com";
 
   char letter = '!';
 
   printf("string before strnset: %s\n", string);
 
   strnset(string, letter, 6);
 
   printf("string after  strnset: %s\n", string);
 
   return 0;
 
}
```
(出自c速查手冊)



26.char *strrchr（char *str， char c）;    //查找字串中最後一次出現字元c的位置
```
#include<string.h>
 
#include<stdio.h>
 
int main(void){
 
   char string[15];
 
   char *ptr, c='c';
 
   strcpy(string,"www.dotcpp.com");
 
   ptr = strrchr(string, c);
 
   if(ptr){
 
      printf("The character %c is at position: %d\n", c, ptr-string);
 
   }else{
 
      printf("The character was not found\n");
 
   }
 
   return 0;
 
}
```
(出自c速查手冊)