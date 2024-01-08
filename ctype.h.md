1.isdigit() //用來判斷是否為十進位的數字
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

int total(char *str){
    int sum = 0;
    char *p = str;
    while(*p != '\0'){

        if(isdigit(*p)){      
            sum = sum + atoi(p);   
            while(isdigit(*p)){
                p++;
            }
        }else{
            p++;
        }
    }

    return sum;
}

int main(){
    char a[1000];
    scanf("%[^\n]", a);
    char *str = a;
    int sum = 0;
    sum = total(str);
    printf("%d\n", sum);

    return 0;
}
```
(出自oj week9第四題的題目)



2.int isascii(int ch) //(int ch)為待檢查得字符  //用來判斷字符是否為ASCII碼，即字符ASCII在0-127之間
```
#include<ctype.h>
#include<stdio.h>
int main()
{
   char ch;
   printf("input a character:");
   ch=getchar();
   if(isascii(ch))
   {
      printf("%c is ascii.",ch);
   }
   else
   {
      printf("%c is not ascii.",ch);
   }
   putchar('\n');
   return 0;
}
```
(出自c語言網)



3.int isalnum(int ch)  //用來判斷字符是否為字母或數字   //返回值:ch不是字母或數字，返回0，ch是字母或數字，返回非0
```
#include<ctype.h>
#include<stdio.h>
int main(){
   char ch;
   printf("input a character:");
   scanf("%c",&ch);
   if(isalnum(ch)) //是字母或數字
   {
      printf("%c is alnum.",ch);
   }
   else
   {
      printf("%c is not alnum.",ch);
   } 
   putchar('\n');
   return 0;  
}
```
(出自c語言網)



4.int isalpha(int c); //用來檢查傳遞的字符是不是字母。c為要檢查的字符
```
#include <stdio.h>
#include <ctype.h>

int main()
{
   int var1 = 'd';
   int var2 = '2';
   int var3 = '	';
   int var4 = ' ';
    
   if( isalpha(var1) )
   {
      printf("var1 = |%c| is an alphabet
", var1 );
   }
   else
   {
      printf("var1 = |%c| is not an alphabet
", var1 );
   }
   if( isalpha(var2) )
   {
      printf("var2 = |%c| is an alphabet
", var2 );
   }
   else
   {
      printf("var2 = |%c| is not an alphabet
", var2 );
   }
   if( isalpha(var3) )
   {
      printf("var3 = |%c| is an alphabet
", var3 );
   }
   else
   {
      printf("var3 = |%c| is not an alphabet
", var3 );
   }
   if( isalpha(var4) )
   {
      printf("var4 = |%c| is an alphabet
", var4 );
   }
   else
   {
      printf("var4 = |%c| is not an alphabet
", var4 );
   }
   
   return(0);
}
```
(出自c語言網)



5.int iscntrl(int c) //用來判斷傳遞的字符是不是為控製字符
```
#include <stdio.h>
#include <ctype.h>

int main ()
{
   int i = 0, j = 0;
   char str1[] = "all a about 	 programming";
   char str2[] = "tutorials 
 yiibai";
  
   /* Prints string till control character a */
   while( !iscntrl(str1[i]) ) 
   {
      putchar(str1[i]);
      i++;
   }
  
   /* Prints string till control character 
 */
   while( !iscntrl(str2[j]) ) 
   {
      putchar(str2[j]);
      j++;
   }
   
   return(0);
}
```
(出自c語言網)



6.int isgraph(int c) //用來判斷傳遞的字符是不是為字符的圖形表示，使用的語言環境
```
#include <stdio.h>
#include <ctype.h>

int main()
{
   int var1 = '3';
   int var2 = 'm';
   int var3 = ' ';
    
   if( isgraph(var1) )
   {
       printf("var1 = |%c| can be printed
", var1 );
   }
   else
   {
      printf("var1 = |%c| can't be printed
", var1 );
   }
   if( isgraph(var2) )
   {
       printf("var2 = |%c| can be printed
", var2 );
   }
   else
   {
      printf("var2 = |%c| can't be printed
", var2 );
   }
   if( isgraph(var3) )
   {
       printf("var3 = |%c| can be printed
", var3 );
   }
   else
   {
      printf("var3 = |%c| can't be printed
", var3 );
   }
   
   return(0);
}
```
(出自c語言網)



7.int islower（int ch）;   // 判斷字元是否為小寫英文字母
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   char ch;
 
   printf("input a character:");
 
   scanf("%c",&ch);
 
   if(islower(ch)){
 
      printf("%c is lower alpha.",ch);
 
   }else{
 
      printf("%c is not lower alpha.",ch);
 
   } 
 
   putchar('\n');   
 
   return 0;  
 
}
```
(出自c語言網)



8.int isprint（int ch）;    // 判斷字元是否為可列印字元（含空格）
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   char ch;
 
   printf("input a character:");
 
   scanf("%c",&ch);
 
   if(isprint(ch)){
 
      printf("%c is print character.",ch);
 
   }else{
 
      printf("%c is not print character.",ch);
 
   } 
 
   putchar('\n');   
 
   return 0;  
 
}
```
(出自c語言網)



9.int ispunct（int ch）;    // 判斷字元是否為標點符號
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   char ch;
 
   printf("input a character:");
 
   scanf("%c",&ch);
 
   if(ispunct(ch)){
 
      printf("%c is punct.",ch);
 
   }else{
 
      printf("%c is not punct.",ch);
 
   } 
 
   putchar('\n');   
 
   return 0;  
 
}
```
(出自c語言網)



9.int isspace（int ch）;    //判斷字元是否為空白字元
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   char ch
 
   printf("input a character:");
 
   scanf("%c",&ch);
 
   if(isspace(ch)){
 
      printf("%c is space.",ch);
 
   }else{
 
      printf("%c is not space.",ch);
 
   } 
 
   putchar('\n');   
 
   return 0;  
 
}
```
(出自c語言網)



10.int isupper（int ch）;    //判斷字元是否為大寫英文字母
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   char ch;
 
   printf("input a character:");
 
   scanf("%c",&ch);
 
   if(isupper(ch)){
 
      printf("%c is upper.",ch);
 
   }else{
 
      printf("%c is not uppper.",ch);
 
   } 
 
   putchar('\n');   
 
   return 0;  
 
}
```
(出自c語言網)



11.int toascii（int ch）;    // 把一個字元轉換為ASCII，其實就是把八位二進位的最高變成0
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   int ch1,ch2;
 
   ch1='a'+128;
 
   ch2=toascii(ch1);
 
   printf("transform %c  to %c.\n",ch1,ch2);      
 
   return 0;  
 
}
```
(出自c語言網)


12.int tolower（int ch）;    //把大寫字母轉換為小寫字母，不是大寫字母的不變
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
   char ch1,ch2;
 
   printf("input a character:");
 
   scanf("%c",&ch1);
 
   ch2=tolower(ch1);
 
   printf("transform %c to %c.\n",ch1,ch2);
 
   return 0;  
 
}
```
(出自c語言網)



13.int touppper（int ch）;     //把小寫字母轉換為大寫字母，不是小寫字母的不變
```
#include<ctype.h>
 
#include<stdio.h>
 
int main(){
 
char ch1,ch2;
 
printf("input a character:");
 
scanf("%c",&ch1);
 
ch2=toupper(ch1);
 
printf("transform %c to %c.\n",ch1,ch2);
 
return 0;
 
}
```
(出自c語言網)
