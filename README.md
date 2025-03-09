# Task-1
Tổng hợp kiến thức.

## Kiểu dữ liệu là gi?

### Được chia thành 2 lớp:
- Kiểu dữ liệu đơn giản Là kiểu biểu diễn được lưu trong 1 biến và chỉ biểu diễn được 1 giá trị.
-  Kiểu dữ liệu cấu trúc là kiểu biển diễn được nhiều thành phần dữ liệu( mảng, cấu trúc, hợp và tệp).

## Các kiểu dữ liệu nguyên thủy:
| Kiểu dữ liệu | Đặc tính biểu diễn | Độ lớn | Giá trị tối thiểu | Giá trị tối đa | 
| ------------ | ------------------ | ------ | ----------------- | -------------- |
| bool | Giá trị logic | 1 byte | false(0) | true(1) |
| char | Ký tự | 1 byte | -2^7 | 2^7 - 1 | 
| short | Số nguyên | 2 byte | -2^15 | 2^15 - 1 |
| int | Số nguyên | 4 byte | -2^31 | 2^31 - 1 |
| long | Số nguyên | 8 byte | -2^ 63 | 2^63 - 1|
| float | Số thực | 4 byte | ~1.2E-38 | ~3.4E+38 |
| double | Số thực | 8 byte | ~2.3E-308 | ~1.7E+308 |
-----------------------------------------------------
( e cũng k hiểu đặc tả dữ liệu là gi nên hỏi chatgpt :))) vẫn k hiểu rõ lắm nhma thấy qua các nó trình bày chắc chắc là gt tối thiểu và tối đa )

## Sự khác nhau giữa kiểu dữ liệu có dấu và không dấu
- Kiểu dữ liệu có dấu (signed) có thể lưu trữ cả số âm và số dương.
- Kiểu dữ liệu không dấu (unsigned) chỉ lưu trữ số dương, giúp tăng phạm vi giá trị có thể lưu trữ.

## Chương trình in ra các kiểu dữ liệu
 ``` C
#include <stdio.h>
#include <stdbool.h>
int main(){
	bool a = true;
	char giaicuuNeng = 'b';
	short c = 2;
	int d = 3;
	float e = 4.5;
	double f = 6.78999;
	long w = 123456766; 
	printf("%d\n", a);
	printf("%c\n", giaicuuNeng);
	printf("%d\n", c);
	printf("%d\n", d);
	printf("%.2f\n", e);
	printf("%lf\n", f);
	printf("%ld", w);
}
```
## Ép kiểu là gì?
- Là chuyển đổi kiểu dữ liệu của một biến từ kiểu này sang kiểu khác.
- VD:
```C
#include <stdio.h>
int main (){
	char vldc = 'm';
	int d = vldc;
	int a = 28;
	float b = a;
	printf("%.2f\n", b);
	printf("%d", d);
}
```

## Địa chỉ, giá trị của biến là gì?
- Địa chỉ của biến là vị trí lưu giá trị của biến.
- Giá trị của biến là dữ liệu được biến lưu trữ.

## Chương trình khai báo 8 biến
``` C
#include <stdio.h>
#include <stdbool.h>
int main (){
	bool a = false;
	char b = 'b';
	short c = 1;
	int d = 2;
	long e = 34444;
	float f = 5.6;
	double g = 7.89999;
	unsigned int h = 100;
    printf("Gia tri: %d, Dia chi: %p\n", a, &a);
    printf("Gia tri: %d, Dia chi: %p\n", b, &b);
    printf("Gia tri: %d, Dia chi: %p\n", c, &c);
    printf("Gia tri: %d, Dia chi: %p\n", d, &d);
    printf("Gia tri: %d, Dia chi: %p\n", e, &e);
    printf("Gia tri: %.2f, Dia chi: %p\n", f, &f);
    printf("Gia tri: %lf, Dia chi: %p\n", g, &g);
    printf("Gia tri: %d, Dia chi: %p\n", h, &h);

}
```

## Các biến được khai báo lệch bao nhiêu đơn vị?
 - @@ mình sẽ thêm đoạn code này vào để tính sự chênh lệch nha T_T
``` C
    printf("a -> b: %d byte\n", (char*)&a - (char*)&b); // ép kiểu về char để giúp mình tính chinh xác hơn
    printf("b -> c: %d byte\n", (char*)&b - (char*)&c);
    printf("c -> d: %d byte\n", (char*)&c - (char*)&d);
    printf("d -> e: %d byte\n", (char*)&d - (char*)&e);
    printf("e -> f: %d byte\n", (char*)&e - (char*)&f);
    printf("f -> g: %d byte\n", (char*)&f - (char*)&g);
    printf("g -> h: %d byte\n", (char*)&g - (char*)&h);
```
- Đây sẽ là kết quả chúng ta có được
 
![image](https://github.com/user-attachments/assets/86f08f6e-af90-474f-a10a-ec5634db0de4)

 
- Tại sao lại có sự chênh lệch?
  - Vì 8 biến có kiểu dữ liệu khác nhau, kích thước mà bộ nhớ dành cho chúng cũng khác nên khoảng cách giữa các địa chỉ không đồng đều.

## Chỉ ra điểm khác biệt giữa biến toàn cục, biến cục bộ.
  

















