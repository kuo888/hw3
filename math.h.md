1  sqrt()  //開根號(比^0.5還要更精準)
```
#include <stdio.h>
#include <math.h>
int main()
{
    int n;
    float avg,b,c,sum,total,d;
    scanf("%d",&n);
    int a[n];
    for(int i=0;i<n;i++){
       scanf("%d",&a[i]);
       total=total+a[i];
    }
    avg = total/n;
    for(int i =0;i<n;i++){
        b=(a[i]-avg)*(a[i]-avg);
        sum = sum + b;
    }
    c = sum / n;
    d=sqrt(c);
    printf("%.2f",d);

    return 0;
}
```
(出自實驗課第四周第一題)

2 double ceil(double a) //無條件進位(浮點數)
```
#include <stdio.h>
#include <math.h>

int main ()
{
   float val1, val2, val3, val4;

   val1 = 1.6;
   val2 = 1.2;
   val3 = 2.8;
   val4 = 2.3;

   printf ("value1 = %.1lf
", ceil(val1));
   printf ("value2 = %.1lf
", ceil(val2));
   printf ("value3 = %.1lf
", ceil(val3));
   printf ("value4 = %.1lf
", ceil(val4));
   
   return(0);
}
```
(出自c語言網)



3  fabs()  //絕對值(用在求浮點數的) 1.double fabs(double); 2.float fabsf(float); 3.long double fabsl(long double);
```
#include <stdio.h>
#include <stdlib.h>

int main ()
{
   int a, b;

   a = abs(5);
   printf("value of a = %d
", a);

   b = abs(-10);
   printf("value of b = %d
", b);
   
   return(0);
}
```
(出自c語言網)



4.fmax()  //用來回傳兩個參數中的最大值，預設回傳值 (return value) 及參數的資料型態為 (1)double ，另有(2) float 型態的 fmaxf() ，(3) long double 型態的 fmaxl() 
```
#include <stdio.h>
#include <math.h>

int main(void)
{
    printf("%f\n", fmax(33, 22));
    printf("%f\n", fmax(-33, -22));
    printf("%f\n", fmax(33, -22));
    printf("%f\n", fmax(-33, 22));
    printf("%f\n", fmax(33 - 22, 22 - 33));
    printf("%f\n", fmax(33 + 22, 22 + 33));
    
    return 0;
}
```
(出自c語言網)



5.fmin()  //用來回傳兩個參數中的最小值，預設回傳值 (return value) 及參數的資料型態為 (1)double ，另有(2) float 型態的 fminf() ，(3) long double 型態的 fminl()
```
#include <stdio.h>
#include <math.h>

int main(void)
{
    printf("%f\n", fmin(33, 22));
    printf("%f\n", fmin(-33, -22));
    printf("%f\n", fmin(33, -22));
    printf("%f\n", fmin(-33, 22));
    printf("%f\n", fmin(33 - 22, 22 - 33));
    printf("%f\n", fmin(33 + 22, 22 + 33));
    
    return 0;
}
```
(出自c語言網)



6.double acos(double x);   //用來求余弦值為x的弧度數，而且[-1,1]中，如果x的值得超出此區間，將會產生域錯誤(domain error)
```
#include<math.h> 
#include<stdio.h> 
#define PI 3.14159265 //定義PI

int main(void){
   double result;
   double x = 0.5;
   result = acos(x)*180/PI;
   printf("The arc cosine of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



7.double asin(double x)   //用來求正弦值為x的弧度數，而且[-1,1]中，如果x的值得超出此區間，將會產生域錯誤(domain error)
```
#include<stdio.h> 
#include<math.h>
#define PI 3.14159265 
int main(){
   double result; 
   double x = 0.5; 
   result = asin(x)*180/PI; 
   printf("The arc sin of %lf is %lf\n", x, result);
 
   return(0);
 
}
```
(出自c語言網)



8.double atan(double x);  //求正切值為 x 的弧度數，區間應為(-PI/2,PI/2)
```
#include<math.h> 
#include<stdio.h>
#define PI 3.14159265 
int main(void){ 
   double result;
   double x = 1; 
   result = atan(x)*180/PI; 
   printf("The arc tangent of %lf is %lf\n", x, result);
 
   return(0);
 
}
```
(出自c語言網)



9.double floor(double x);  //用來浮點數向下捨入
```
#include<stdio.h>
#include<math.h> 
int main(){ 
   double number = 123.54; 
   double down, up;
   down = floor(number);
   up = ceil(number);  //此函數為無條件進位
   printf("original number %10.2lf\n", number);
   printf("number rounded down %10.2lf\n",  down);
   printf("number rounded up %10.2lf\n", up);
 
   return 0;
 
}
```
(出自c語言網)



10.labs() //用來取絕對值(用在取長整型的)
```
#include<stdio.h> 
#include<math.h> 
int main(){ 
   long result; 
   long x = -12345678L; 
   result= labs(x);
 
   printf("number: %ld abs value: %ld\n",x, result);
 
   return 0;
 
}
```
(出自c語言網)



11.pow(double x, double y)  //用來算函數(x的y次方)，其中x為底數，y為指數
```
#include<stdio.h> 
#include<math.h> 
int main(void){ 
   double x = 2.0, y = 3.0; 
   printf("%lf raised to %lf is %lf\n", x, y, pow(x, y));
 
   return 0;
 
}
```
(出自c語言網)



12.double sin(double x); //用來算正弦函數，x為要操作的正弦值(1度 = PI/180度弧度)
```
#include<stdio.h>
 
#include<math.h>
 #define PI 3.14159265 
int main(){ 
   double result, x = 30*PI/180; //將30度角轉換成弧度 
   result = sin(x); 
   
   printf("The sin() of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



13.double cos(double x);  //用來算餘弦函數，x為要操作的弧度(1度 = PI/180度弧度)
```
#include<math.h> 
#include<stdio.h>
#define PI 3.14159265
int main(){
   double result; 
   double x = 60*PI/180;  //將60度角轉換為弧度
 
   result = cos(x);
   printf("The cosine of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



14.double tan(double x); //用來算正切函數，x為要操作的弧度(1度 = PI/180度弧度)
```
#include<math.h>
#include<stdio.h> 
#define PI 3.14159265
int main(){
   double result,x;
 
   x = 30*PI/180; //將30度角轉換成弧度
   result = tan(x);
 
   printf("The tan of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



15.double log10(double x);  //用來求指定數值的以10為底數的對數，其中x必須為真數，且必須大於0(公式:loge x =b)
```
#include<math.h> 
#include<stdio.h>
int main(void){
   double result;
   double x = 800.6872;
   result = log10(x);
 
   printf("The common log of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



16.double log(double x); //用來求以自然數為底數的對數，其中x為真數，且必須大於0(公式:自然數e為常數2.71828)
```
#include<math.h> 
#include<stdio.h> 
int main(void){
   double result;
   double x = 8.6872; 
   result = log(x);
 
   printf("The natural log of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



17.double modf(double value, double *iptr);  //用來求雙精度數的小數部分，value為要操作的雙精度數，*iptr為要傳回整數部分的變量指針
```
#include<math.h>
#include<stdio.h> 
int main(){ 
   double fraction, integer; 
   double number = 100000.567; 
   fraction = modf(number, &integer);
 
   printf("The whole and fractional parts of %lf are %lf and %lf\n",
 
   number, integer, fraction);
 
   return 0;
 
}
```
(出自c語言網)



18.double fmod(double x, double y);  //用來計算x對y的模，及x/y的餘數，x為雙精度除數，y雙精度被除數(返回值為x/y的餘數)
```
#include<math.h> 
#include<stdio.h> 
int main(void){ 
   double x = 5.0, y = 2.0; 
   double result; 
   result = fmod(x,y);
 
   printf("The remainder of (%lf / %lf) is %lf\n", x, y, result);
 
   return 0;
 
}
```
(出自c語言網)



19.double frexp(double value, int *eptr);   //用來把一個雙精度數分解為尾數和指數，value為要分解的雙精度浮點數，int *eptr為傳回解好的指數的指針變量(返回分解好的尾數)
```
#include<math.h> 
#include<stdio.h> 
int main(void){
   double mantissa, number;
   int exponent;
   number = 8.0; 
   mantissa = frexp(number, &exponent);
   printf("The number %lf is ", number); 
   printf("%lf times two to the ", mantissa); 
   printf("power of %d\n", exponent);
 
   return 0;
 
}
```
(出自c語言網)



20.double hypot(double x, double y);   //用來計算值解三角形的斜邊長度，x&y為直角三角形的直角邊
```
#include<math.h> 
#include<stdio.h> 
int main(void){ 
   double x = 3.0; 
   double y = 4.0;
   double result = hypot(x, y); 
   printf("The hypotenuse is: %lf\n", result);
 
   return 0;
 
}
```
(出自c語言網)



21.double ldexp(double value, int exp);  //用來計算指定的2^exp倍數，value為雙精度時數，exp為2的整型指數
```
#include<math.h>
#include<stdio.h> 
int main(void){
   double value;
   double x = 2;
   value = ldexp(x,3);
   printf("The ldexp value is: %lf\n", value);
 
   return 0;
 
}
```
(出自c語言網)



22.double atan2(double y, double x);     //計算Y/X的反正切值，y代表x軸座標的浮點值，x代表y軸座標的浮點值(返回值為原點到點(x,y)的方位角，也就是與x軸的夾角，取值範圍為(-PI,PI]
```
#include<stdio.h>
#include<math.h> 
#define  PI  3.14159265 
int main(){
   double result;
   double x1 = 1, y1 = 1;
   result = atan2(y1, x1)*180/PI; //通过一个点求正切值的弧度
   printf("atan2(%lf) is %lf\n", (y1 / x1), result);
 
   //如果有两个点
   double x2=3,y2=5;
   result=atan2(y2-y1,x2-x1)*180/PI; //通过两个点求正切值的弧度\
   printf("atan2(%lf) is %lf\n", ((y2-y1) / (x2-x1)), result);
 
   return 0;
 
}
```
(出自c語言網)



23.double cosh(double x);  //用來計算雙曲正弦值(公式:cosh(x)=(e^x+e^(-x))/2 )
```
#include<math.h> 
#include<stdio.h> 
int main(void){
   double result; 
   double x = 0.5;
   result = cosh(x);
 
   printf("The hyperboic cosine of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



24.double sinh(double x);  //用來求出指定值的雙曲正弦值(公式: sinh(x)=(e^x-e^(-x))/2)
```
#include<math.h> 
#include<stdio.h>
int main(void){
   double result, x = 0.5;
   result = sinh(x);
 
   printf("The hyperbolic sin() of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



25.double tanh(double x);   //用來計算雙曲正切值
```
#include<math.h> 
#include<stdio.h>
int main(void){
   double result, x;
   x = 0.5;
   result = tanh(x);
 
   printf("The hyperbolic tangent of %lf is %lf\n", x, result);
 
   return 0;
 
}
```
(出自c語言網)



26.cbrtf() //用來算立方根，函數原型為1.double cbrt(double);2.float cbrtf(float);3.long double cbrtl(long double);
```
#include <stdio.h>
#include <math.h>

int main(void)
{
    printf("%f\n", cbrt(125.0));
    printf("%f\n", cbrt(35.937));
    printf("%f\n", cbrt(27));
    printf("%f\n", cbrt(42.2));
    printf("%f\n", cbrt(97.325));
    printf("%f\n", cbrt(88.025));
    
    return 0;
}
```
(出自c語言網)