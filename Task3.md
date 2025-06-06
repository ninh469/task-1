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
| Bố trí bộ nhớ | Mỗi thành phần chia thành vùng riêng biệt | tất cả thành phần dùng chung vùng bộ nhớ | Các phần tử được lưu trữ liên tiếp trong bộ nhớ |
| Size | Bằng tổng size các kdl bên trong nó | Bằng size của kdl lớn nhất | Bằng size của mỗi phần tử nhân với số lượng phần tử |
| Kiểu dữ liệu | Chứa được nhiều kdl | Chỉ chứa được một kdl tại một thời điểm  | Chỉ chứa được các thành phần có cùng 1 KDL |
| Cách truy cập | Theo thuộc tính  | Theo thuộc tính | Theo chỉ số |
| Cách khai báo | struct ten_struct{ các thành phần }; | union ten_union{ các thành phần }; | kdl ten_mang[size] |
### Ví dụ trực quan về struct và union
```C
#include <stdio.h>
#include <string.h>
struct thuvien {
	int Nam;
	char tentg[100];
	char tentp[100];
};
int main(){
	struct thuvien tv;
	tv.Nam = 1900;
	strcpy ( tv.tentg, "ffhkgh");
	strcpy ( tv.tentp, "Drama");
	printf("Nam: %d\nTen tac gia: %s\nTen tac pham: %s",tv.Nam,tv.tentg,tv.tentp);
	
}
```
Output: 

![image](https://github.com/user-attachments/assets/7e0190b8-23f8-45b1-b4e9-0c4fb8057dda)

```C
#include <stdio.h>
#include <string.h>
union thuvien {
	int Nam;
	char tentg[100];
	char tentp[100];
};
int main(){
	union thuvien tv;
	tv.Nam = 1900;
	strcpy ( tv.tentg, "ffhkgh");
	strcpy ( tv.tentp, "Drama");
	printf("Nam: %d\nTen tac gia: %s\nTen tac pham: %s",tv.Nam,tv.tentg,tv.tentp);
	
}
```
Output:

![image](https://github.com/user-attachments/assets/a9a778b3-a1ab-4e20-94c5-47b68ac0a298)


## Bài tập
```C
#include<stdio.h>
#include<string.h>

typedef struct{
	char hoten[100];
	int tuoi;
	double diemtb;
}Qlsv;
Qlsv nhapthongtinSv(){
	Qlsv sv;
	printf("Nhap ho ten: ");
	fgets(sv.hoten, sizeof(sv.hoten), stdin);
	sv.hoten[strcspn(sv.hoten,"\n")] = '\0';
	printf("Nhap tuoi: ");
	scanf("%d", &sv.tuoi);
	printf("Nhap diem TB: ");
	scanf("%lf", &sv.diemtb);
	getchar();
	return sv;
};

void hienthithongtin(Qlsv sv){
	printf("%-20s%-10d%-10.2f\n",sv.hoten, sv.tuoi, sv.diemtb);
}

void hienthidanhsach(Qlsv sinhvien[], int n){
	printf("DANH SACH SINH VIEN\n");
	printf("%-5s%-20s%-10s%-10s\n","STT","Ho Ten","Tuoi","Diem TB");
	for( int i = 0; i < n;i++){
		printf("%-5d", i + 1);
		hienthithongtin(sinhvien[i]);
	}
}

int timsinhvien (Qlsv sinhvien[], int n, char hotencantim[]){
	for ( int i = 0; i < n; i++){
		if (strcmp(hotencantim,sinhvien[i].hoten) == 0) return i;
	} return -1;
}

int chensvbatky(Qlsv sinhvien[], int n, char hotencanchen[]) {
    int kiepnan = timsinhvien(sinhvien, n, hotencanchen);
	if ( kiepnan < 0){
		printf("Khong tim thay sinh vien %s\n",hotencanchen);
	} else {
		Qlsv svmoi = nhapthongtinSv();
		for (int i = n; i > kiepnan + 1; i--){
			sinhvien[i] = sinhvien[i - 1];
		}sinhvien[kiepnan + 1] = svmoi;
		n++;
	} 
	return n;
}

int xoasinhvien(Qlsv sinhvien[], int n, char hotencanxoa[]) {
    int kiepnan = timsinhvien(sinhvien, n, hotencanxoa);
	if ( kiepnan < 0){
		printf("Khong tim thay sinh vien %s\n",hotencanxoa);
	} else {
		while ( kiepnan < n - 1){
			sinhvien[kiepnan] = sinhvien[kiepnan + 1];
			kiepnan++;
		} n--;
	} return n;
}

void suasinhvien(Qlsv sinhvien[], int n, char hotencansua[]){
	int kiepnan = timsinhvien(sinhvien,n,hotencansua);
	if ( kiepnan < 0){
		printf("Khong tim thay sinh vien %s\n",hotencansua);
	} else {
		printf("Nhap thong tin moi cua sinh vien\n");
		Qlsv suasv = nhapthongtinSv();
		sinhvien[kiepnan] = suasv;
	}
}
void menu(){
	printf("Menu\n");
	printf("1. Tao danh sach sinh vien\n");
	printf("2. Hien thi danh sach sinh vien\n");
	printf("3. Chen them mot sinh vien vao sau sinh vien bat ki\n");
    printf("4. Xoa mot sinh vien\n");
    printf("5. Sua mot sinh vien\n");
    printf("6. Thoat\n");
    printf("Lua chon: ");
}
int main (){
	int n, quaylai_1 = 0;
	Qlsv sinhvien[100];
	menu();
	while (1){
		int chon;
		scanf("%d", &chon);
		getchar();
		char hotencantim[100];
		switch(chon){
			case 1: 
			quaylai_1 = 1;
			printf("Ban vua chon chuc nang 1: Tao danh sach sinh vien\n");
			printf("Nhap so luong sinh vien: ");
			scanf("%d",&n);
			getchar();
			for (int i = 0; i < n; i++){
                    sinhvien[i] = nhapthongtinSv();
            } break;
            case 2: 
			if (quaylai_1 == 0){
				printf("Vui long tao danh sach sinh vien\n");
				break;
			} else {
				printf("Ban vua chon chuc nang 2: Hien thi danh sach sinh vien\n");	
			hienthidanhsach(sinhvien,n);
            break;
			}
			case 3:
			if (quaylai_1 == 0){
				printf("Vui long tao danh sach sinh vien\n");
				break;
			} else {
			printf("Ban vua chon chuc nang 3: Chen them mot sinh vien vao sau sinh vien bat ki\n");	
			printf("Nhap ho ten sinh vien o truoc: ");
            fgets(hotencantim, sizeof(hotencantim), stdin);
            hotencantim[strcspn(hotencantim,"\n")] = '\0';
			n = chensvbatky(sinhvien,n,hotencantim);
			printf("Danh sach da duoc cap nhat\n");
			hienthidanhsach(sinhvien,n);
			break;
			}
		    case 4: 
		    if (quaylai_1 == 0){
				printf("Vui long tao danh sach sinh vien\n");
				break;
			} else {
			printf("Ban vua chon chuc nang 4: Xoa mot sinh vien\n");
			printf("Nhap ho ten sinh vien can xoa: ");
			fgets(hotencantim, sizeof(hotencantim), stdin);
			hotencantim[strcspn(hotencantim,"\n")] = '\0';
			n = xoasinhvien(sinhvien,n,hotencantim);
			printf("Danh sach da duoc cap nhat\n");
			hienthidanhsach(sinhvien,n);
			break;
		    }
			case 5: 
			if (quaylai_1 == 0){
				printf("Vui long tao danh sach sinh vien\n");
				break;
			} else {
			printf("Ban vua chon chuc nang 5: Sua mot sinh vien\n");
			printf("Nhap ho ten sinh vien can sua: ");
			fgets(hotencantim, sizeof(hotencantim), stdin);
			hotencantim[strcspn(hotencantim,"\n")] = '\0';
			suasinhvien(sinhvien,n,hotencantim);
			printf("Danh sach da duoc cap nhat\n");
			hienthidanhsach(sinhvien,n);
			break;
			case 6: return 0;
	     	}
		    default : printf("Xin hay tha cho toi, Vui long nhap lai\n");	
	    } menu();
	}
}
```



  
