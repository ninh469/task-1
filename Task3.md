# Task 3
Nêu cấu trúc, tính chất, ý nghĩa, cách sử dụng của struct.
Phân biệt struct với union, array.

Làm bài dưới đây;
Viết chương trình tạo ra một danh sách dạng mảng để quản lý danh sách sinh viên. Cấu trúc sinh viên gồm các thành phần: Ho_ten, Tuoi, Diem_TB. Chương trình được tổ chức thành các chương trình con sau: 
1) Tạo danh sách sinh viên 
2) Hiển thị danh sách ra màn hình theo dạng 
    DANH SACH SINH VIEN
STT    Ho ten    Tuoi    Diem TB
        . . .    . . .
3) Chèn thêm một sinh viên vào sau sinh viên nào đó (có tên nhập vào từ bàn phím) 
4) Xóa một sinh viên
5) Sửa một sinh viên
## Cấu trúc, tính chất, ý nghĩa, cách sử dụng của struct.
- Cấu trúc:
```C
struct ten_struct{
       kieu_du_lieu_1 ten_bien_1;
       ...
       kieu_du_lieu_n ten_bien_n;
};
```
- Tính chất:
  + Cho phép khai báo nhiều kiểu dữ liệu khác nhau trong cùng 1 cấu trúc.
  + Truy cập tới các thành phần bằng ".", nếu là con trỏ thì truy cập bằng "->"
  + Được lưu trữ liên tiếp theo thứ tự khai báo trong bộ nhớ
  + Có thể thực được phép gán giữa những struct cùng kiểu.
- Ý nghĩa:
  + Tối ưu hơn trong việc quản lý
  + Có thể tái sử dụng nhiều lần
  + 
- Cách sử dụng
```C
#include<stdio.h>
struct phim{
	char tenphim[100];
	int namchieu;
};
int main(){
	struct phim phim;
	fgets ( phim.tenphim, sizeof(phim.tenphim), stdin);
	scanf("%d", &phim.namchieu);
	printf("Ten phim: %s", phim.tenphim);
	printf("Nam chieu: %d", phim.namchieu);
}
```
## Phân biệt struct với union, array.
|             | struct | union | array |
| ----------- | ------ | ----- | ----- |
| Bố trí bộ nhớ | Mỗi thành phần chia thành vùng riêng biệt | Các thành phần dùng chung | Các phần tử được lưu trữ liên tiếp trong bộ nhớ |
| Kiểu dữ liệu | Chứa được nhiều KDL | Tương tự struct | Chỉ chứa được các thành phần có cùng 1 KDL |
| Cách truy cập | Theo thuộc tính ( truy cập đồng thời tới tất cả các thành phần )  | Theo thuộc tính ( tại một thời điểm chỉ chứa giá trị của 1 thuộc tính duy nhất  | Theo chỉ số |

## Bài tập
```C

```



  
