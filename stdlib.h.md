1.rand(void)    //隨機產生亂數 ，不須給參數，只能呼叫它

```
#include <stdio.h>
#include <stdlib.h>
int main()
{
    int i;
    for(i=0;i<4;i++){    //重複執行四次，產生四個亂數
        printf("%d\n",rand());
    }
    return 0;
}
```
 (出自於c語言入門影片)



2.srand(unsigned int seed) //(1)基本上在呼叫rand()前會使用(2)用來初始化亂數產生器(指定rand函數的亂數種)
```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    srand(2); //給的值不一樣所產生的值就會不一樣
    int i;
    for(int i = 0; i <5; i++){
        printf("%d\n",rand());
    }

    return 0;
}
```
(出自c語言入門影片)



3.atoi() //用來將字符串轉換為整數
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



4.atof()  //用來將字串轉換成浮點數(double)
```
#include <stdio.h>
#include <stdlib.h>

typedef struct {

char integer[1000];

char decimal[1000];

} DeciVar;

int main()
{
    double sum, a, b;
    DeciVar n;
    scanf("%s", n.integer);  //存整數
    scanf("%s", n.decimal); //存小數
    
    a = atof(n.integer); //atof()用來將字串轉成浮點數
    b = atof(n.decimal);
    sum = a + b;
    printf("%.lf", sum);

    return 0;
}
```
(出自Oj week10-3)



5.void *malloc(size_t size)  //用來做動態記憶體配置，產生動態的記憶體空間，時常會搭配sizeof來計算所佔的記憶體空間大小
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* generateNext(const char* input) {  // 產生下一個look-and-say數列的項目
    int len = strlen(input);
    char* result = (char*)malloc(sizeof(char) * (len * 2 + 1));  // 預留空間給新的結果字串
    int index = 0;
    int resultIndex = 0; // 新增一個變量用於跟踪結果字符串的索引

    while (index < len) {
        int count = 1;
        while ((index + 1 < len) && (input[index] == input[index + 1])) {
            count++;
            index++;
        }

        result[resultIndex++] = count + '0';  // 將出現次數轉換為字符並存入結果字串
        result[resultIndex++] = input[index];   // 存入數字本身
        index++;
    }

    result[resultIndex] = '\0';
    return result;
}

void displayLookAndSay(int N, const char* term) { // 顯示look-and-say數列的前 N 項
    if (N <= 0) {
        return;
    }

    printf("%s\n", term);

    char* nextTerm = generateNext(term);  // 生成下一個項目
    displayLookAndSay(N - 1, nextTerm);  // 遞迴顯示剩餘的項目

    free(nextTerm);
}

int main() {
    int N;
    scanf("%d", &N);

    if (N <= 0 || N > 40) {
        printf("Invalid input!\n");
        return 1;
    }

    displayLookAndSay(N, "1");

    return 0;
}
```
(出自oj week11-3)



6.void free(void *ptr) //用來釋放記憶體，常與malloc()函式作搭配
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* generateNext(const char* input) {  // 產生下一個look-and-say數列的項目
    int len = strlen(input);
    char* result = (char*)malloc(sizeof(char) * (len * 2 + 1));  // 預留空間給新的結果字串
    int index = 0;
    int resultIndex = 0; // 新增一個變量用於跟踪結果字符串的索引

    while (index < len) {
        int count = 1;
        while ((index + 1 < len) && (input[index] == input[index + 1])) {
            count++;
            index++;
        }

        result[resultIndex++] = count + '0';  // 將出現次數轉換為字符並存入結果字串
        result[resultIndex++] = input[index];   // 存入數字本身
        index++;
    }

    result[resultIndex] = '\0';
    return result;
}

void displayLookAndSay(int N, const char* term) { // 顯示look-and-say數列的前 N 項
    if (N <= 0) {
        return;
    }

    printf("%s\n", term);

    char* nextTerm = generateNext(term);  // 生成下一個項目
    displayLookAndSay(N - 1, nextTerm);  // 遞迴顯示剩餘的項目

    free(nextTerm);
}

int main() {
    int N;
    scanf("%d", &N);

    if (N <= 0 || N > 40) {
        printf("Invalid input!\n");
        return 1;
    }

    displayLookAndSay(N, "1");

    return 0;
}

```
(出自oj week11-3)



7.void abort（void）;   //寫一個終止資訊到stderr，並異常終止程式
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void) {
 
   printf("Calling abort()\n");
 
   abort();
 
   printf("It is noneffective\n");
 
   return 0;
 
}
```
(出自c語言網)



8.int atexit（void （*func）（void）））;    //用於註冊終止
```
#include<stdio.h>
 
#include<stdlib.h>
 
void f1();
 
void f2();
 
typedef void (*f)();  //定義函數指針類型
 
int main(void) {
 
   f fun1=f1,fun2=f2;  //定義函數指針
 
   atexit(fun1);
 
   atexit(fun2); 
 
   return 0;
 
}
 
void f1(){
 
   printf("exit first called\n");  
 
}
 
void f2(){
 
   printf("exit second called\n");
 
}
```
(出自c語言網)



9.int atol（const char *s）;  // 將字串轉換成長整型數，const char *s 為要轉換的字串
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   long r;
 
   char *s="525713.14";
 
   r=atol(s);
 
   printf("string = %s\nint= %ld\n",s,r);
 
   return 0;
 
}
```
(出自c語言網)



10.bsearch（）  //用於二分法搜索
```
#include<stdio.h>
 
#include<stdlib.h>
 
#define SIZE(arr)  sizeof(arr)/sizeof(int)
 
int arr[]={123,456,789,654,312,714};
 
typedef int (*fc)(const void*,const void*);
 
int numcmp(const void* p1,const void* p2){
 
   int *pi1=(int*)p1;
 
   int *pi2=(int*)p2;
 
   return (*pi1-*pi2);
 
}
 
int search(int key){
 
   fc f=numcmp;
 
   int *ptr=bsearch(&key,arr,SIZE(arr),sizeof(int),f);
 
   return ptr!=NULL;
 
}
 
int main(void){
 
   if(search(456)){
 
      printf("456 is in the list.\n");
 
   }else{
 
      printf("456 isn't in the list\n");
 
   }
 
   return 0;
 
}
 
```
(出自c語言網)



11.void *calloc（size_t n，size_t s）;  //用於分配堆記憶體，size_t *n 分配空間的個數，size_t *m 分配空間的位元元組數
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   int *p=(int*)calloc(1,sizeof(int));
 
   *p=8;
 
   printf("the value is %d\n",*p);
 
   free(p);
 
   return 0;
 
}
```
(出自c語言網)



12.div_t div（int x，int y）;   //用於兩個整數相除
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   div_t a = div(210,25);
 
   printf("210 div 25 = %d remainder %d\n",a.quot,a.rem);  //输出结果
 
   return 0;
 
}
```
(出自c語言網)



13.char *ecvt（double f，int n，int *p，int *c）;    //把浮點數轉換為字串
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   double f=5.21;
 
   int p,c;
 
   int n=10;
 
   char *str1=ecvt(f,n,&p,&c);
 
   printf("string=%s    p=%d    c=%d\n",str1,p,c);
 
   f=-103.23;
 
   char *str2=ecvt(f,n,&p,&c);
 
   printf("string=%s    p=%d    c=%d\n",str2,p,c);
 
   f=0.123;
 
   char *str3=ecvt(f,n,&p,&c);
 
   printf("string=%s    p=%d    c=%d\n",str3,p,c);
 
   f=4e5;
 
   char *str4=ecvt(f,n,&p,&c);
 
   printf("string=%s    p=%d    c=%d\n",str4,p,c);
 
   return 0;
 
}
```
(出自c語言網)



14.char *fcvt（double f，int n，int *p，int *c）;   //將浮點數轉換為字串，int *p 一個指向變數返回數值的小數點的位址的指標，int *c 一個表示數值正負的指標
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   double f=5.21;
 
   int p,c;
 
   int n=10;
 
   char *str1=fcvt(f,n,&p,&c);
 
   printf("string=%s\tp=%d\tc=%d\n",str1,p,c);
 
   f=-103.23;
 
   char *str2=fcvt(f,n,&p,&c);
 
   printf("string=%s\tp=%d\tc=%d\n",str2,p,c);
 
   f=0.123;
 
   char *str3=fcvt(f,n,&p,&c);
 
   printf("string=%s\tp=%d\tc=%d\n",str3,p,c);
 
   f=4e5;
 
   char *str4=fcvt(f,n,&p,&c);
 
   printf("string=%s\tp=%d\tc=%d\n",str4,p,c);
 
   return 0;
 
}
```
(出自c語言網)



15.void exit（int status）;  //用於正常終止程式，int status 為終止狀態
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   int a,status;
 
   printf("Input a order: 1--go  others--exit\n");
 
   while(scanf("%d",&a)==1){
 
      if(a!=1){
 
         exit(0);
 
      }
 
      printf("Input a order: 1--go  others--exit\n");   
 
   }
 
   return 0;
 
}
```
(出自c語言網)



16.char *gcvt(double f,int n,char *c);   //把浮點數轉換為字串，四捨五入，*c 是存放結果的臨時緩衝區
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   double f=5.21;
 
   int n=7;
 
   char c[20]={"\0"};
 
   char *str1=gcvt(f,n,c);
 
   printf("string=%s   c=%s\n",str1,c);
 
   f=-103.23;
 
   char *str2=gcvt(f,n,c);
 
   printf("string=%s   c=%s\n",str2,c);
 
   f=0.123;
 
   char *str3=gcvt(f,n,c);
 
   printf("string=%s   c=%s\n",str3,c);
 
   f=4e5;
 
   char *str4=gcvt(f,n,c);
 
   printf("string=%s   c=%s\n",str4,c);
 
   return 0;
 
}
```
(出自c語言網)



17.char *getenv（char *name）;    //用於獲取當前環境中的字串
```
#include<stdio.h>
 
#include<stdlib.h>
 
#include<string.h>
 
int main(void){
 
   char *s = getenv("COMSPEC");
 
   printf("Command processor: %s\n",s);
 
   return 0;
 
}
```
(出自c語言網)



19.char *itoa（int i，char *s，int radix）;   //用於把整數轉換成字串
```
#include<stdio.h>
 
#include<stdlib.h>
 
#include<string.h>
 
int main(void){
 
   int i = 1725;
 
   char s[10]={"\0"};
 
   int radix=10;
 
   itoa(i,s,radix);
 
   printf("integer = %d  string = %s\n",i,s);
 
   return 0;
 
}
```
(出自c語言網)



20.ldiv_t ldiv（long lx，long ly）;   //用於兩個長整型數相除，long lx 為被除，long ly 為除數
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   ldiv_t lx = ldiv(165000L,35500L);
 
   printf("165000 div 35500 = %ld remainder %ld\n",lx.quot,lx.rem);
 
   return 0;
 
}
 
```
(出自c語言網)



21.lfind()   //用於在給定的區域內從頭到尾進行線性搜索
```
#include<stdio.h>
 
#include<stdlib.h>
 
typedef int (*fc)(const void*,const void*);
 
int compare(const void* p1,const void *p2){  //比较两个数的大小
 
   int *pi1=(int*)p1;
 
   int *pi2=(int*)p2;
 
   return (*pi1-*pi2);
 
}
 
int main(void){
 
   int arr[5]={25,14,29,68,55};
 
   size_t n=5;
 
   int key=29;
 
   fc f=compare;
 
   int* result=(int*)lfind(&key,arr,&n,sizeof(int),f);
 
   if(result){
 
      printf("Number %d is found\n",key);
 
   }else{
 
      printf("Number %d is not found\n",key);
 
   }
 
   return 0;
 
}
```
(出自c語言網)



22.lsearch（）  //用於在給定的區域內從頭到尾進行線性搜索
```
#include<stdio.h>
 
#include<stdlib.h>
 
typedef int (*fc)(const void*,const void*);
 
int compare(const void* p1,const void *p2){  //比较两个数的大小
 
   int *pi1=(int*)p1;
 
   int *pi2=(int*)p2;
 
   return (*pi1-*pi2);
 
}
 
int main(void){
 
   int arr[5]={25,14,29,68,55};
 
   size_t n=5;
 
   int key=27;
 
   fc f=compare;
 
   int* result=(int*)lsearch(&key,arr,&n,sizeof(int),f);
 
   if(result){
 
      printf("Number %d is found\n",key);
 
   }else{
 
      printf("Number %d is not found\n",key);
 
   }
 
   return 0;
 
}
```
(出自c語言網)



23.void *realloc（void *p，unsigned size）;    //用於重新分配指定大小的堆記憶體空間
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
   double *d = (double*)malloc(sizeof(double));
 
   *d=3.14;
 
   printf("the value is %lf\n",*d);
 
   int* i=(int*)realloc(d,sizeof(int));
 
   *i=90;
 
   printf("the value is %d\n",*i);
 
   free(d);
 
   return 0;
 
}

```
(出自c語言網)



24.void *putenv（char *name）;    //用於改變或增加環境變數的內容( 成功返回0 ，失敗返回-1)
```
#include<stdio.h>
 
#include<stdlib.h>
 
#include<string.h>
 
int main(void){
 
   char *path,*ptr;
 
   int i=0;
 
   ptr=getenv("PATH");
 
   path=malloc(strlen(ptr)+15);
 
   strcpy(path,"PATH=");
 
   strcat(path,ptr);
 
   strcat(path,"c:\\temp");
 
   putenv(path);
 
   while(environ[i]){
 
      printf("%s\n",environ[i++]);
 
   }
 
   return 0;
 
}
```
(出自c語言網)



25.qsort（）   //用於對記錄從小到大快速排序(似泡沫排序法)
```
#include<stdio.h>
 
#include<stdlib.h>
 
typedef int (*fc)(const void*,const void*);
 
int compare(const void* p1,const void* p2){
 
   return (*(int*)p1)-(*(int*)p2);
 
}
 
int main(void){
 
   int i,arr[10]={1,6,5,7,8,9,11,24,3,10};
 
   fc f=compare;
 
   qsort(arr,10,sizeof(int),f);
 
   for(i=0;i<10;i++){
 
      printf("%d\t",arr[i]);
 
   }
 
   putchar('\n');
 
   return 0;
 
}
```
(出自c語言網)



26.double strtod（char *s，char ptr）;    // 用於將字串轉換為浮點數
```
#include<stdio.h>
 
#include<stdlib.h>
 
#include<time.h>
 
int main(void){
 
    char *endptr;
 
    char a[] = "12345.6789";
 
    char b[] = "1234.567qwer";
 
    char c[] = "-232.23e4";
 
    printf( "a=%lf\n", strtod(a,NULL) );
 
    printf( "b=%lf\n", strtod(b,&endptr) );
 
    printf( "endptr=%s\n", endptr );
 
    printf( "c=%lf\n", strtod(c,NULL) );
 
    return 0;
 
}
```
(出自c語言網)



27.long strtol（char s，char ptr，int radix）;     //用於將字串換成長整型數
```
#include<stdio.h>
 
#include<stdlib.h>
 
#include<time.h>
 
int main(void){
 
    char *a="100000";
 
   char *b="100000";
 
   char c[]="cd";
 
   printf("a=%d\n",strtol(a,NULL,10));
 
   printf("b=%d\n",strtol(b,NULL,2));
 
   printf("c=%d\n",strtol(c,NULL,16));
 
   return 0;
 
}
```
(出自c語言網)



28.void swab（char *from，char to，int n）;    //從源和目標區域交換位元組
```
#include<stdio.h>
 
#include<stdlib.h>
#include<string.h>
 
#include<time.h>
 
int main(void){
 
    char suc[20]={"ww.wodctppc.mo"};
 
    char des[20];
 
    swab(suc,des,strlen(suc));
 
    printf("This is dest: %s\n",des);
 
    return 0;
 
}
 
```
(出自c語言網)



29.system（）   //用於發出一個DOS命令(成功返回0，失敗返回-1)
```
#include<stdio.h>
 
#include<stdlib.h>
 
int main(void){
 
    printf("About to spawn command.com and run a DOS command\n");
 
   system("dir");  //执行dos命令
 
   return 0;
 
}
```
(出自c語言網)
