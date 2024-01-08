1.printf() //用於輸出

```
#include <stdio.h>

int main()
{
    printf("Hello World");

    return 0;
}
```

(此函數用來將雙引號裡的函數輸出出來) 

2.scanf() → 請使用者輸入，從鍵盤讀取資料

```
#include <stdio.h>

int main()
{
    int n;
    scanf("%d",&n);   //&是取址運算子(取得位置的意思)
    printf("%d",n);

    return 0;
}
```



3.fgets()  //類似於scanf()，用來讀取(使用者輸入)資料
```
#include <stdio.h>

int main()
{
   FILE *fp;
   char str[60];

   /* opening file for reading */
   fp = fopen("file.txt" , "r");
   if(fp == NULL) {
      perror("Error opening file");
      return(-1);
   }
   if( fgets (str, 60, fp)!=NULL ) {
      /* writing content to stdout */
      puts(str);
   }
   fclose(fp);
   
   return(0);
}
```
(出自c語言網)



4.getchar() //用來從標準輸入裝置接受使用者輸入的字元
```
#include <stdio.h>

int main(void)
{
    char c1;
    
    printf("請輸入任何一個字元....\n");    
    c1 = getchar();
    printf("剛剛輸入的字元： %c\n", c1);
    
    return 0;
}

```
(出自c語言網)



5.puts() //用來將字串傳送到標準輸出裝置
```
#include <stdio.h>

int main(void)
{
    char *c1 = "Hello";
    
    puts(c1);
    
    return 0;
}
```
(出自c語言網)



6.void clearerr(FILE *stream); //用來 複位錯誤標誌(注意:clearerr的作用是使文件錯誤標誌和文件結束標誌置為0.假設在調用一個輸入輸出函數時出現了錯誤，ferror函數值為一個非零值。 在調用clearerr（fp）后，ferror（fp）的值變為0。)
```
#include<stdio.h>
 
int main(){
 
   FILE *fp;
 
   char ch;
 
   fp = fopen("1.txt", "w"); //以只写的方式打开文件，此文件是不可读的
 
   ch = fgetc(fp);  //读取文件的一个字符
 
   printf("%c\n",ch);
 
   if (ferror(fp)){  //判断文件流是否出现错误
 
      printf("Error reading from 1.txt\n");  //输出错误信息
 
      clearerr(fp); //复位错误指针
 
   }
 
   fclose(fp);  //关闭文件
 
   return 0;
 
}
```
(出自c語言網)



7.int ferror（FILE *stream）;   // 檢測流上的錯誤，若檢測到給定流上的錯誤返回非0值。(成功返回0，失敗返回1)
```
#include<stdio.h>
 
int main(void){
 
   FILE *stream;
 
   stream = fopen("1.txt", "w");  //以只写的方式打开文件，此文件是不可读的 
 
   (void) getc(stream);  //读取文件的一个字符
 
   if (ferror(stream)){   //判断流中是否有错误
 
      printf("Error reading from 1.txt\n");
 
      clearerr(stream); //复位错误指针
 
   }
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



8.int fclose（FILE *stream）;  //關閉流 stream，刷新所有的緩衝區，stream指定了要被關閉的流(成功返回0，失敗返回EOF)
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   FILE *fp;
 
   char buf[11] = "0123456789";
 
   fp = fopen("1.txt", "w");  //打开文件
 
   fwrite(&buf, strlen(buf), 1, fp);  //写入文件
 
   printf("write sucessful\n");
 
   fclose(fp);  //关闭文件
 
   return 0;
 
}
```
(出自c語言網)



9.int feof（FILE *stream）;    // 檢測流上的文件結束符。 檢測到檔尾標記EOF或Ctrl-z都為文件結束符，stream為要檢測的流( 成功傳回非零值 ，失敗返回0)
```
#include<stdio.h>
 
int main(void){
 
   FILE *stream;
 
   stream = fopen("1.txt", "r");
 
   fgetc(stream);
 
   if(feof(stream)){
 
      printf("We have reached end-of-file\n");
 
   }
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



10.int fflush（FILE *stream）;    //用來 清除一個流。 清除輸入流的緩衝區，使它仍然打開，並把輸出流的緩衝區的內容寫入它所聯繫的檔中。，其中stream為要清除的流(成功返回0 ，失敗返回EOF)
```
#include<stdio.h>
 
#include<string.h>
 
#include<conio.h>
 
#include<windows.h>
 
int main(void){
 
   FILE *stream;
 
   char msg[] = "This is a test";
 
   stream = fopen("1.txt", "w");  //创建文件
 
   fwrite(msg, strlen(msg), 1, stream);  //将文件写入一些字符
 
   system("cls");  //清屏
 
   printf("Press any key to flush 1.txt:\n");  
 
   getch();
 
   fflush(stream);  //清除流
 
   printf("File was flushed, Press any key to quit\n");
 
   getch();
 
   return 0;
 
}
```
(出自c語言網)



11.int fgetpos（FILE *stream）;    //用來 取得當前文件指標（句柄）， stream為要操作的檔流(成功返回0 ，失敗返回非0值)
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   FILE *stream;
 
   char string[] = "This is a test";
 
   fpos_t filepos;
 
   stream = fopen("DUMMY.FIL", "w+");
 
   fwrite(string, strlen(string), 1, stream);
 
   fgetpos(stream, &filepos);
 
   printf("The file pointer is at byte %ld\n", filepos);
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



12.FILE *fopen（char *filename， char *mode）;   //用來打開一個流 出錯返回NULL，
 char *filename 指定文件的絕對路徑，char *mode mode字串的可取值)
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char *s;
 
   FILE *fp;
 
   fp=fopen("1.txt","rw");
 
   if(!fp){
 
      printf("can not open the file\n");
 
      return 0;
 
   }
 
   fputs("www.dotcpp.com!\n",fp);
 
   fclose(fp);
 
   return 0;
 
}
```
(出自c語言網)



13.int fprintf（FILE *stream， char *format[， argument,...]）;    //格式化輸出到一個流中，照原樣抄寫格式串format的內容到流stream中，每遇到一個%，就按規定的格式，依次輸出一個表達式argument的值到流stream中;
```
#include<stdio.h>
 
int main(void){
 
   FILE *in=fopen("D:\\test.txt", "r");
 
   FILE *out= fopen("D:\\a.txt", "w");
 
   if (!in){
 
      fprintf(stderr, "Cannot open input file.\n"); //将字符串输出到标准错误流中
 
      return 1;
 
   }
 
   if (!out){
 
      fclose(in);
 
      in=NULL;
 
      fprintf(stderr, "Cannot open output file.\n");  //将字符串输出到标准错误流中
 
      return 1;
 
   }
 
   while (!feof(in)) {
 
      fputc(fgetc(in), out);
 
   }
 
   fclose(in);
 
   in=NULL;
 
   fclose(out);
 
   out=NULL;
 
   return 0;
 
}
```
(出自c語言網)



14.int fputchar（char ch）;  // 送一個字元到標準輸出流（stdout）中，送一個字元到螢幕。 等價於fputc（c，stdout）， ch 為要輸出到螢幕的字元
```
#include<stdio.h>
 
int main(void){
 
   char msg[] = "This is a test";
 
   int i = 0;
 
   while (msg[i]){
 
      fputchar(msg[i]);
 
      i++;
 
   }
 
   putchar('\n');
 
   return 0;
 
}
```
(出自c語言網)



15.int fputs（char *str， FILE *stream）;     // 送一個字元到一個流中 把str所指的以'\0'結尾的字串送入流中，不加換行符'\n'，不拷貝串結束符'\0'，str 要輸出的字串，stream 要輸出的流
```
#include<stdio.h>
 
int main(void){
 
   fputs("www.dotcpp.com\n", stdout);
 
   return 0;
 
}
```
(出自c語言網)



16.fread（）  // 從一個流中讀數據，從所給的輸入流流中讀取的n項數據，每一項數據長度為size位元組，到由ptr所指的塊中
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   FILE *stream;
 
   char msg[] = "www.dotcpp.com";
 
   char buf[20];
 
   if ((stream = fopen("DUMMY.FIL", "w+"))== NULL){
 
      fprintf(stderr,"Cannot open output file.\n");
 
      return 1;
 
   }
 
   fwrite(msg, strlen(msg)+1, 1, stream);  //将字符串写入文件中
 
   fseek(stream, SEEK_SET, 0);   //定位到文件的开头部分
 
   fread(buf, strlen(msg)+1, 1, stream);  //读取文件的字符串
 
   printf("%s\n", buf);
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



17.freopen（）  //用來 替換一個流，用filename所指定的檔代替打開的流stream所指定的檔(成功返回stream，失敗返回NULL)
```
#include<stdio.h>
 
int main(void){
 
   if (freopen("D:\\out.txt", "w", stdout)== NULL){
 
      fprintf(stderr, "error redirecting stdout\n");
 
   }
 
   printf("www.dotcpp.com\n"); //原本要在控制台中输出的字符串，输出到了文件中
 
   fclose(stdout);
 
   return 0;
 
}
```
(出自c語言網)



18.int fscanf（FILE *stream， char *format[，argument...]）;   //用來從一個流中執行格式化輸入
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   int i;
 
   printf("Input an integer: ");
 
   if (fscanf(stdin, "%d", &i)){
 
      printf("The integer read was: %i\n",i);
 
   }else{
 
      fprintf(stderr, "Error reading an integer from stdin.\n");
 
      exit(1);
 
   }
 
   return 0;
 
}
```
(出自c語言網)



19.fseek（）  //用來重定位流上的文件指標
```
#include<stdio.h>
 
long filesize(FILE *stream);
 
int main(void){
 
   FILE *stream = fopen("myfile.txt", "w+");
 
   fprintf(stream, "www.dotcpp.com");
 
   fseek(stream, 0, SEEK_END);
 
   printf("Filesize of myfile.txt is %ld bytes\n", ftell(stream));
 
   fclose(stream);
 
   return 0;
 
}
 
```
(出自c語言網)



20.fsetpos()    //將文件指標定位在指定的位置上
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char string[] = "www.dotcpp.com";
 
   fpos_t filepos;
 
   FILE *stream = fopen("test.txt", "w+");
 
   fwrite(string, strlen(string), 1, stream); //将字符串写入文件流中
 
   fgetpos(stream, &filepos);  //获取文件的指针位置
 
   printf("The file pointer is at byte %ld\n", filepos);
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



21.long ftell（FILE *stream）;   //用來偏移量是從文件開始算起的位元組數
```
#include<stdio.h>
 
int main(void){
 
   FILE *stream = fopen("test.txt", "w+");
 
   if(!stream){
 
      printf("can not open the file\n");
 
      return 0;
 
   }
 
   fprintf(stream, "www.dotcpp.com");
 
  printf("The file pointer is at byte %ld\n", ftell(stream));
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



22.int fwrite（void *ptr， int size， int nitems， FILE *stream）;   //寫內容到流中，void *ptr 要寫入的內容，size 要寫入字元的長度，nitems 要寫入字元的數量，*stream 要寫入的檔流
```
#include<stdio.h>
 
struct mystruct{
 
   int i;
 
   char ch;
 
};
 
  
 
int main(void){
 
   FILE *stream= fopen("D:\\test.txt", "wb");
 
   struct mystruct s;
 
   if (!stream){
 
      fprintf(stderr, "Cannot open output file.\n");
 
      return 1;
 
   }
 
   s.i = 0;
 
   s.ch = 'A';
 
   if(fwrite(&s, sizeof(s), 1, stream)==1){//将结构体写入文件流中
 
      printf("write to successful\n");
 
   }else{
 
      printf("write to failure\n");
 
   }
 
   fclose(stream);
 
   return 0;
 
}
```
(出自c語言網)



23.getche()  //用來從控制台取字元
```
#include<stdio.h>
 
int main(void) {
 
   printf("Input a character:");
 
   char ch = getche();
 
   printf("\nYou input a '%c'\n", ch);
 
   return 0;
 
}
 
```
(出自c語言網)



24.int getw（FILE *strem）;    //用來從流中取一整數
```
#include<stdio.h>
 
#include<string.h>
 
#define FNAME "test.bat"
 
int main(void){
 
   FILE *fp = fopen(FNAME, "wb");
 
   if (fp == NULL) {
 
      printf("Error opening file %s\n", FNAME);
 
      exit(1);
 
   }
 
   int word = 94;
 
   putw(word,fp);
 
   if (ferror(fp)){
 
      printf("Error writing to file\n");
 
   }else{
 
      printf("Successful write %d\n",word);
 
   }
 
   fclose(fp);
 
   fp = fopen(FNAME, "rb");
 
   if (fp == NULL)   {
 
      printf("Error opening file %s\n", FNAME);
 
      exit(1);
 
   }
 
   word = getw(fp);
 
   if (ferror(fp)){
 
      printf("Error reading file\n");
 
   }else{
 
      printf("Successful read: word = %d\n", word);
 
   }
 
   fclose(fp);   
 
   return 0;
 
}
```
(出自c語言網)



25.void perror（char *str）;  //輸出系統錯誤資訊
```
#include<stdio.h>
 
int main(void){
 
   FILE *fp = fopen("perror.dat", "r");
 
   if (!fp){
 
      perror("Unable to open file for reading");
 
   }
 
   return 0;
 
}
```
(出自c語言網)



26.int putc（int ch， FILE *stream）;   //輸出一字元到指定流中(成功以無符號 char強制轉換為 int 的形式返回寫入的字元 ，失敗返回 EOF。)
```
#include<stdio.h>
 
int main(void){
 
   char msg[] = "www.dotcpp.com\n";
 
   int i = 0;
 
   while (msg[i]){
 
      putc(msg[i++], stdout);
 
   }
 
   return 0;
 
}
```
(出自c語言網)



27.int putchar（int ch）;  //在stdout上輸出字元
```
#include<stdio.h>
 
int main(void){
 
   putchar('w'); 
 
   putchar('w');
 
   putchar('w');
 
   putchar('.');
 
   putchar('d');
 
   putchar('o');
 
   putchar('t');
 
   putchar('c');
 
   putchar('p');
 
   putchar('p');
 
   putchar('.');
 
   putchar('c');
 
   putchar('o');
 
   putchar('m');
 
   putchar('\n');
 
   return 0;
 
}
```
(出自c語言網)



28.int puts（char *str）;   //把一個字串寫入到標準輸出 stdout
```
#include<stdio.h>
 
int main(void){
 
   char str[] = "www.dotcpp.com\n";
 
   puts(str);
 
   return 0;
 
}
```
(出自c語言網)



29.int putw（int w， FILE *stream）;  //把一字元或字送到流中
```
#include<stdio.h>
 
int main(void){
 
   int word=49;
 
   int res=putw(word,stdout);
 
   printf("\nThe return value is %d\n",res);
 
   return 0;
 
}
```
(出自c語言網)



30.int remove（char *filename）;  //刪除一個檔
```
#include<stdio.h>
 
int main(void){
 
   char file[80];
 
   printf("File to delete: ");
 
   gets(file);
 
   if (remove(file) == 0){
 
      printf("Removed %s.\n",file);
 
   }else{
 
      perror("remove");
 
   }
 
   return 0;
 
}
```
(出自c語言網)



31.int rename（char *oldname， char *newname）;   //重新命名檔
```
#include<stdio.h>
 
int main(void){
 
   char oldname[80], newname[80];
 
   printf("File to rename: ");
 
   gets(oldname);
 
   printf("New name: ");
 
   gets(newname);
 
   if (rename(oldname, newname) == 0){
 
      printf("Renamed %s to %s.\n", oldname, newname);
 
   }else{
 
      perror("rename");
 
   }
 
   return 0;
 
}
```
(出自c語言網)



32.int rewind（FILE *stream）;  //將文件指標重新指向一個流的開頭
```
#include<stdio.h>
 
int main(void){
 
   FILE *fp=fopen("D:\\a.txt","w+");
 
   if(!fp){
 
      printf("can not open the file\n");
 
      return 0;
 
   }
 
   fprintf(fp,"abcdefghijklmnopqrstuvwxyz");
 
   int first=ftell(fp);
 
   rewind(fp);
 
   int second=ftell(fp);
 
   printf("First pointer is %d,after call the rewind() is %d\n",first,second);
 
   fclose(fp);
 
   remove("D:\\a.txt");
 
   return 0;
 
}
```
(出自c語言網)



33.int ungetc（char c， FILE *stream）;   //把一個字元退回到輸入流中(成功 返回字元 ，失敗返回 EOF，且流 stream 保持不變)
```
#include <stdio.h>
 
#include <ctype.h>
 
int main( void ){
 
   int i=0;
 
   char ch;
 
   puts("Input an integer followed by a char:");
 
   if((ch = getchar()) != EOF && isdigit(ch)){ //獲取字符，如果是數字類型
 
      i = ch - 48;  
 
   }
 
   ungetc(ch, stdin);  //退回給输入緩衝區
 
  printf("i = %d, next char in buffer = %c\n", i, getchar());
 
   return 0;
 
}
```
(出自c語言網)



34.int ungetch（int c）;   // 把一個字元退回到鍵盤緩衝區中
```
#include<stdio.h>
 
#include<conio.h>
 
#include<ctype.h>
 
int main( void ){
 
   int i=0;
 
   char ch;
 
   puts("Input an integer followed by a char:");
 
   while((ch = getche()) != EOF && isdigit(ch)){
 
      i = 10 * i + ch - 48;
 
   }
 
   if (ch != EOF){
 
      ungetch(ch);
 
   }
 
  printf("\ni = %d, next char in buffer = %c\n", i, getch());
 
   return 0;
 
}
 
```
(出自c語言網)



35.FILE *tmpfile（void）;  // 以二進位方式打開暫存檔
```
#include<stdio.h>
 
int main(void){
 
   FILE *tempfp = tmpfile();
 
   if (tempfp){
 
      printf("Temporary file created\n");
 
   }else{
 
      printf("Unable to create temporary file\n");
 
      exit(1);
 
   }
 
   return 0;  
 
}
```
(出自c語言網)



36.char *tmpnam（char *sptr）;  //建立唯一的檔案名稱
```
#include<stdio.h>
 
int main(void){
 
   char name[13];
 
   tmpnam(name);
 
   printf("Temporary name: %s\n", name);
 
   return 0;
 
}
```
(出自c語言網)



37.void setbuf（FILE *steam， char *buf）;  //把緩衝區與流相聯，FILE *stream 為要處理的流，char *buf 為要處理的緩衝區
```
#include<stdio.h>
 
char outbuf[BUFSIZ];
 
int main(void){
 
   setbuf(stdout, outbuf);  //將緩衝區與流相關聯
 
   puts("This is a test of buffered output.\n\n");  //將字符寫入緩衝區
 
   puts("This output will go into outbuf\n");
 
   puts("and won't appear until the buffer\n");
 
   puts("fills up or we flush the stream.\n");
 
   fflush(stdout);  //刷新緩衝區
 
   return 0;
 
}
```
(出自c語言網)



38.setvbuf（）  //把緩衝區與流相關
```
#include<stdio.h>
 
int main(void){ 
 
   char bufr[512];
 
   FILE *input = fopen("file.in", "rb+");
 
   if(!input){
 
      printf("can not open the file\n");
 
   }
 
   FILE *output = fopen("file.out", "w");
 
   if(!output){
 
      printf("can not open the file\n");
 
   }
 
   if (setvbuf(input, bufr, _IOFBF, 512)){
 
      printf("failed to set up buffer for input file\n");
 
   }else{
 
      printf("buffer set up for input file\n");
 
   }
 
   if (setvbuf(output, NULL, _IOLBF, 512)) {
 
      printf("failed to set up buffer for output file\n");
 
   }else{
 
      printf("buffer set up for output file\n");
 
   }
 
   fclose(input);
 
   fclose(output);
 
   return 0;
 
}
```
(出自c語言網)



39.sprintf()   //输出到字符串中
```
#include<stdio.h>
 
#include<math.h>
 
int main(void){
 
   char buffer[80];
 
   sprintf(buffer, "An approximation of Pi is %f", M_PI);
 
   puts(buffer);
 
   return 0;
 
}
```
(出自c語言網)



40.sscanf()  //執行從字串中的格式化輸入
```
#include<stdio.h>
 
#include<string.h>
 
int main(void){
 
   char s1[]="9.4 8.2 7...";
 
   char s2[50];
 
   char c;
 
   int i;
 
   float f;
 
   sscanf(s1,"%s",s2);  //从缓冲区中读取数据
 
   sscanf(s1,"%c",&c); 
 
   sscanf(s1,"%d",&i); 
 
   sscanf(s1,"%f",&f);
 
   printf("string=%s\n",s1);
 
   printf("str=%s\n",s2);
 
   printf("character=%c\n",c);
 
   printf("integer=%d\n",i);
 
   printf("real=%f\n",f);
 
   return 0;
 
}
```
(出自c語言網)