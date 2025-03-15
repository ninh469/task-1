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
- Đảo giá trị của nhiều biến
- Kiểm soát địa chỉ
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
- Là tập hợp gồm nhiều phần tử có cùng 1 kiểu dữ liệu và chung 1 tên gọi, nhưng được phân biệt bởi chỉ số.
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
- Hàm là một các khối lệnh có nhiệm vụ thực hiện một chức năng nào đó.
## Nêu ý nghĩa của việc xây dựng hàm 
- Chia công việc nhóm
- Có thể tái sử dụng nhiều lần 
## Chỉ ra vì sao chương trình dưới đây không thực hiện thành công mục đích đảo đổi giá trị 2 biến? 
- Chương trình không thực hiện được là vì hàm void swap là hàm không trả giá trị về nên ta sẽ sử dụng con trỏ để trả giá trị lại về cho hàm main, cụ thể thêm:
   - Nếu mà k sử dụng con trỏ thì chương trình sẽ hiểu là mình đổi biến trên hàm swap nó là biến ảo nên nó k ảnh hưởng đến a,b ở hàm main được. Chương trình nó chạy từ hàm main lên swap , nhma swap(a,b) nó chỉ truyền giá trị a,b vào swap chứ không đảo giá trị(trả giá trị).
   - Nếu có con trỏ thì thực chất chương trình nó sẽ hiểu được luôn là mình muốn đổi giá trị của biến a với biến b thông qua *a,*b.

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



