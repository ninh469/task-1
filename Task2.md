# Task 2
## Con trỏ là gi?
Con trỏ là biến thông thường nhưng mà giá trị được lưu của nó lại là địa chỉ của biến khác.
## Cách sử dụng
- Cú pháp:
  - Xem giá trị tại vùng nhớ trỏ tới: *<con_tro>
  - Địa chỉ được trỏ tới: <con_tro>
``` C
#include<stdio.h>
int main(){
int a = 505;
int *p = &a; // *p la con tro
printf("gia tri tai vung nho con tro toi %d", *p); // gia tri tai vung nho con tro toi la gia tri cua bien a
printf("dia chi duoc tro toi %p", p); // dia chi duoc tro toi là dia chi cua a
}
```
## Ứng dụng của con trỏ 
- Truyền tham chiếu trong hàm.
- Kiểm soát địa chỉ.
- Thao tác với mảng và chuỗi.
- Xây dựng cấu trúc dữ liệu phức tạp
- Tối ưu hóa hiệu suất.
- continue
## Xây dựng chương trình ứng dụng
- Sắp xếp 3 số theo thứ tự tăng dần
```c
#include <stdio.h> 
void swap(int *x, int *y) 
{
    int tmp = *x;
    *x = *y;
    *y = tmp;
}

void check (int *a, int *b, int *c)
{
	if( *a > *b)
		swap( a, b);
	if ( *b > *c)
		swap( b, c);
	if ( *a > *b)
	 	swap( a, b);
}
int main()
{
    int a,b,c;
    scanf("%d%d%d", &a, &b, &c);
    check(&a,&b,&c);
    printf("%d %d %d", a,b,c);
}
```
## Mảng 1 chiều là gì?
- Mảng là một tập hợp các phần tử có cùng kiểu dữ liệu, được lưu trữ liên tiếp trong bộ nhớ và được quản lý dưới một tên chung.
## Cách truy cập tới phần tử thứ n mà không dùng cú pháp cơ bản(arr[n]) thay vào đó sử dụng con trỏ.
``` C
#include<stdio.h>
int main(){
int n, a[100],b;
scanf("%d", &n);
for(int i = 0; i < n; i++){
	scanf("%d", &a[i]);
} printf ("Chao mung ngai den voi nha hang NengNeng\nMoi ngai xem menu cua chung toi\n");
  printf ("Mon ma ngai muon chon la: ");
  scanf("%d", &b);
  printf("Mon an da %d san sang chuc ngai ngon mieng!, cua ngai het %d$ chuyen khoan hay tien mat ",b,*(a + b));
}
```
## Hàm là gì? 
- Hàm là một khối lệnh thực hiện một nhiệm vụ cụ thể nào đó và có thể được gọi nhiều lần trong chương trình.
- Cú pháp xây dựng hàm: ten_ham(tham_so)
## Nêu ý nghĩa của việc xây dựng hàm 
- Chia nhỏ chương trình thành các phần nhỏ hơn để dễ quản lý.
- Có thể tái sử dụng nhiều lần.
- Dễ dàng sửa lỗi hơn thay vì phải sửa cả chương trình.
- Tăng độ rõ ràng của chương trình.
## Các loại hàm, cú pháp xây dựng hàm:
- Hàm trả về giá trị:
``` C
#include <stdio.h>
int check( int a, int b){
	if ( a > b){
		return a;
	} if ( b > a){
		return b;
	} return a;
} 

int main(){
	int a,b;
	scanf("%d%d", &a,&b);
	int c = check(a,b);
	printf ("%d", c);
}
```
- Hàm không trả giá trị:
``` C
#include <stdio.h>
void check( int a, int b){
	if ( a > b){
	printf("%d", a);
	} if ( b > a){
	printf("%d", b);
	} printf ("%d", a);
} 

int main(){
	int a,b;
	scanf("%d%d", &a,&b);
    check(a,b);
}
```
## Chỉ ra vì sao chương trình dưới đây không thực hiện thành công mục đích đảo đổi giá trị 2 biến? 
cái này Ninh sẽ sửa khi ăn cơm xong :((( ai lại băt người đói không có năng lượng làm việc

## Thực hiện sửa lại chương trình để chương trình hoạt động bình thường.
``` C
#include <stdio.h>

void swap(int *a, int *b)
{
    int tmp = *a;
    *a = *b;
    *b = tmp;
}
int main()
{
    int a = 100, b = 123456;
    swap(&a, &b);
    printf("a = %d\nb = %d", a, b);
}
```



