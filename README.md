# Task-1
Tổng hợp kiến thức
Ép kiểu là gì? cho ví dụ.

Địa chỉ, giá trị của biến là gì? Xây dựng chương trình khai báo 8 biến a,b,c,d,e,f,g,h là 8 biến có kiểu dữ liệu khác nhau, in ra địa chỉ và giá trị của chúng, chỉ ra các biến được khai báo lệch bao nhiêu đơn vị và tại sao?

Chỉ ra điểm khác biệt giữa biến toàn cục, biến cục bộ.
## Kiểu dữ liệu là gi?

### Được chia thành 2 lớp:
- Kiểu dữ liệu đơn giản Là kiểu biểu diễn được lưu trong 1 biến và chỉ biểu diễn được 1 giá trị.
-  Kiểu dữ liệu cấu trúc là kiểu biển diễn được nhiều thành phần dữ liệu( mảng, cấu trúc, hợp và tệp)

## Các kiểu dữ liệu nguyên thủy:
| Kiểu dữ liệu | Đặc tính biểu diễn | Độ lớn | Giá trị tối thiểu | Giá trị tối đa | 
| ------------ | ------------------ | ------ | ----------------- | -------------- |
| bool | Giá trị logic | 1 bit | false(0) | true(1) |
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
	long w = 123456766; // cái này hiện tại e chưa dùng mấy :v
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








