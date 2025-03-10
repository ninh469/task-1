# Task1
Tổng hợp kiến thức.
## Kiểu dữ liệu là gi?
- Được chia thành 2 lớp:
   - Kiểu dữ liệu đơn giản Là kiểu biểu diễn được lưu trong 1 biến và chỉ biểu diễn được 1 giá trị.
   - Kiểu dữ liệu cấu trúc là kiểu biển diễn được nhiều thành phần dữ liệu( mảng, cấu trúc, hợp và tệp).
## Các kiểu dữ liệu nguyên thủy:
| Kiểu dữ liệu | Đặc tính biểu diễn | Độ lớn | Đặc tả | 
| ------------ | ------------------ | ------ | ------ |
| bool | Giá trị logic | 1 byte |  |
| char | Ký tự | 1 byte | %c | 
| short | Số nguyên | 2 byte |  |
| int | Số nguyên | 4 byte | %d |
| long long | Số nguyên | 8 byte | %lld |
| float | Số thực (nó lưu được 6 chữ số ở phần thập phân) | 4 byte | %f |
| double | Số thực (nó lưu được 15 chữ số ở phần thập phân) | 8 byte | %lf |
-----------------------------------------------------
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
- Output:

![image](https://github.com/user-attachments/assets/d823da92-97de-4ca1-b7f8-711930b4a624)


## Ép kiểu là gì?
- Là chuyển đổi kiểu dữ liệu của một biến từ kiểu này sang kiểu khác.
- VD1:
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
- Output:

![image](https://github.com/user-attachments/assets/c62448d7-393b-4a81-87a1-77e244ec54cf)

- VD2:

| ![image](https://github.com/user-attachments/assets/8a8f819c-7682-46be-aabb-4202646a21c8) | ![image](https://github.com/user-attachments/assets/a37fc533-b0d3-4c31-9c18-962d66dac54d) |
|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|

E thấy là float hay double mà về long long thì nó làm tròn xuống phần nguyên vì long long nó chỉ biểu diễn số nguyên, còn về cách ép thì biểu diễn chính xác được 5 số sau phần thập phân kể cả float hay double.
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
- Output:
  
![image](https://github.com/user-attachments/assets/1aec92da-c948-4d52-bbce-5f9279276806)

## Các biến được khai báo lệch bao nhiêu đơn vị?
 - @@ mình sẽ thêm đoạn code này vào để tính sự chênh lệch đơn vị(byte) T_T
``` C
    printf("a -> b: %d byte\n", (char*)&a - (char*)&b); 
    printf("b -> c: %d byte\n", (char*)&b - (char*)&c);
    printf("c -> d: %d byte\n", (char*)&c - (char*)&d);
    printf("d -> e: %d byte\n", (char*)&d - (char*)&e);
    printf("e -> f: %d byte\n", (char*)&e - (char*)&f);
    printf("f -> g: %d byte\n", (char*)&f - (char*)&g);
    printf("g -> h: %d byte\n", (char*)&g - (char*)&h);
```
- Đây sẽ là kết quả chúng ta có được:
 
![image](https://github.com/user-attachments/assets/86f08f6e-af90-474f-a10a-ec5634db0de4)

- Để giải thích cho kết quả trên:
   - Do vị trí của bộ nhớ các biến được cấp phát vị trí trong bộ nhớ theo thứ tự khai báo biến a được cấp phát trước, lần lượt là b -> h.
   - Kết quả là 1,2,4,4,...,4. Điều này có thể xảy ra vì: char chỉ chiếm 1 byte. int chiếm 4 byte....
- Cụ thể hơn tham khảo ví dụ của a Sơn:
  
![image](https://github.com/user-attachments/assets/4c17f531-8ffe-48f3-a962-fb0696f40b89)
- Khi mà cái float nó khai báo trước cái char thì float đang ở địa chỉ cao hơn. Giả sử thằng float đang ở 48 thì 4 byte thằng float là 51 50 49 48, char khai báo sau nên nó sẽ đưa vào địa chỉ thấp hơn là 47. int là 4 byte nên để tối ưu bộ nhớ thì nó sẽ lưu ở ô chia hết cho 4, 47 - 4 = 43 không thỏa mãn nên buộc nó phải xuống ô 40 nên cách nhau 7 byte. 
- Tại sao lại có sự chênh lệch?
   - Vì 8 biến có kiểu dữ liệu khác nhau, kích thước mà bộ nhớ dành cho chúng cũng khác nên khoảng cách giữa các địa chỉ không đồng đều.
    

## Chỉ ra điểm khác biệt giữa biến toàn cục, biến cục bộ.
Theo ý e hiểu ý thì nó giống như là 1 thằng trong tù(cục bộ) và 1 thằng lang thang đầu đường xó chợ(toàn cục).
- Toàn cục:
    - Được khai báo ngoài tất cả các hàm.
    - Đặt khai báo biến trước rồi mới đến khai báo hàm.
    - Giá trị của nó được giữ nguyên trong suốt quá trình chạy chương trình.
    - Khi không khởi tạo giá trị biến toàn cục sẽ gắn nó bằng 0.
-  Cục bộ 
   - Được khai báo bên trong một hàm hoặc một khối {}.
   - Chỉ có thể sử dụng trong phạm vi hàm chứa nó.
   - Biến sẽ bị xóa khỏi bộ nhớ khi kết thúc phạm vi của nó.
   - Để sử dụng thì mình sẽ dùng return để nó trả về giá trị.
   - Khi không khởi tạo giá trị biến cục bộ sẽ coi nó là giá trị rác.

  

















