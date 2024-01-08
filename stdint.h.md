主要式定義整數型別

1.int8_t    //8位有符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    int8_t num = 10;
    printf("Value of num: %d\n", num);
    return 0;
}

```
(來自維基百科)



2.int16_t    //16位有符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    int16_t num = 1000;
    printf("Value of num: %d\n", num);
    return 0;
}

```
(來自維基百科)



3.int32_t //32位有符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    int32_t num = 100000;
    printf("Value of num: %d\n", num);
    return 0;
}

```
(來自維基百科)



4.int64_t  //64位有符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    int64_t num = 1000000000;
    printf("Value of num: %lld\n", num);
    return 0;
}
```

(來自維基百科)



5.uint8_t   //8位無符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    uint8_t num = 255;
    printf("Value of num: %u\n", num);
    return 0;
}

```
(來自維基百科)



6.uint16_t   //16位無符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    uint16_t num = 65535;
    printf("Value of num: %u\n", num);
    return 0;
}

```
(來自維基百科)



7.uint32_t//32位無符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    uint32_t num = 4000000000;
    printf("Value of num: %u\n", num);
    return 0;
}

```
(來自維基百科)



8.uint64_t  //64位無符號整數
```
#include <stdio.h>
#include <stdint.h>

int main() {
    uint64_t num = 100000000000000;
    printf("Value of num: %llu\n", num);
    return 0;
}

```
(來自維基百科)