# task4
Trình bày về cấu trúc dữ liệu danh sách liên kết, làm các yêu cầu dưới đây.
- Code task 3 nhưng với danh sách liên kết thay vì biểu diễn dạng mảng, thêm option sắp xếp theo điểm
- Code chương trình xây dựng lại stack bằng danh sách liên kết(khởi tạo các node bằng malloc()), thực hiện chuyển đổi cơ số từ 10 sang các cơ số khác
cuu toi khoi dia nguc tra gian
## 1
```C
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

typedef struct{
    char hoten[100];
    int tuoi;
    double diemtb;
}sinhvien;

typedef struct Node{
    sinhvien data;
    struct Node* next;
}Node;


Node* taoNode(sinhvien sv) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = sv;
    newNode->next = NULL;
    return newNode;
}


sinhvien nhapthongtinSv() {
    sinhvien sv;
    printf("Nhap ho ten: ");
    fgets(sv.hoten, sizeof(sv.hoten), stdin);
    sv.hoten[strcspn(sv.hoten,"\n")] = '\0';
    printf("Nhap tuoi: ");
    scanf("%d", &sv.tuoi);
    printf("Nhap diem TB: ");
    scanf("%lf", &sv.diemtb);
    getchar(); 
    return sv;
}

void hienthithongtin(sinhvien sv) {
    printf("%-20s%-10d%-10.2f\n", sv.hoten, sv.tuoi, sv.diemtb);
}

void hienthidanhsach(Node* head) {
    printf("DANH SACH SINH VIEN\n");
    printf("%-5s%-20s%-10s%-10s\n", "STT", "Ho Ten", "Tuoi", "Diem TB");
    
    Node* kiepnan = head;
    int i = 1;
    while (kiepnan != NULL) {
        printf("%-5d", i++);
        hienthithongtin(kiepnan->data);
        kiepnan = kiepnan->next;
    }
}

Node* timsinhvien(Node* head, char hotencantim[]) {
    Node* kiepnan = head;
    while (kiepnan != NULL) {
        if (strcmp(hotencantim, kiepnan->data.hoten) == 0) 
            return kiepnan;
        kiepnan = kiepnan->next;
    }
    return NULL;
}

Node* chensvbatky(Node* head, char hotencanchen[]) {
    Node* svtruoc = timsinhvien(head, hotencanchen);
    if (svtruoc == NULL) {
        printf("Khong tim thay sinh vien %s\n", hotencanchen);
        return head;
    } else {
        printf("Nhap thong tin sinh vien moi:\n");
        sinhvien svmoi = nhapthongtinSv();
        Node* newNode = taoNode(svmoi);
        newNode->next = svtruoc->next;
        svtruoc->next = newNode;
    }
    return head;
}

Node* xoasinhvien(Node* head, char hotencanxoa[]) {
    if (head == NULL) {
        printf("Danh sach rong!\n");
        return NULL;
    }
    if (strcmp(head->data.hoten, hotencanxoa) == 0) {
        Node* temp = head;
        head = head->next;
        free(temp);
        return head;
    }
    Node* kiepnan = head;
    while (kiepnan->next != NULL && strcmp(kiepnan->next->data.hoten, hotencanxoa) != 0) {
        kiepnan = kiepnan->next;
    }

    if (kiepnan->next != NULL) {
        Node* temp = kiepnan->next;
        kiepnan->next = temp->next;
        free(temp);
    } else {
        printf("Khong tim thay sinh vien %s\n", hotencanxoa);
    }
    
    return head;
}

Node* suasinhvien(Node* head, char hotencansua[]) {
    Node* nodeCanSua = timsinhvien(head, hotencansua);
    
    if (nodeCanSua == NULL) {
        printf("Khong tim thay sinh vien %s\n", hotencansua);
    } else {
        printf("Nhap thong tin moi cua sinh vien:\n");
        nodeCanSua->data = nhapthongtinSv();
    }
    
    return head;
}


int sosanh(sinhvien a, sinhvien b) {
    if (a.diemtb < b.diemtb) return 1;
    if (a.diemtb > b.diemtb) return -1;
    return 0;
}

Node* sapxepTheoDiem(Node* head) {
    if (head == NULL || head->next == NULL) {
        return head; 
    }
    int a;
    Node* ptr1;
    Node* ptr2 = NULL;
    
    do {
        a = 0;
        ptr1 = head;
        
        while (ptr1->next != ptr2) {
            if (sosanh(ptr1->data, ptr1->next->data) > 0) {
                sinhvien temp = ptr1->data;
                ptr1->data = ptr1->next->data;
                ptr1->next->data = temp;
                a = 1;
            }
            ptr1 = ptr1->next;
        }
        ptr2 = ptr1;
    } while (a);
    
    return head;
}

void giaiphongbonho(Node* head) {
    Node* temp;
    while (head != NULL) {
        temp = head;
        head = head->next;
        free(temp);
    }
}

void menu() {
    printf("\nMenu\n");
    printf("1. Tao danh sach sinh vien\n");
    printf("2. Hien thi danh sach sinh vien\n");
    printf("3. Chen them mot sinh vien vao sau sinh vien bat ki\n");
    printf("4. Xoa mot sinh vien\n");
    printf("5. Sua mot sinh vien\n");
    printf("6. Sap xep sinh vien theo diem\n");
    printf("7. Thoat\n");
    printf("Lua chon: ");
}

int main() {
    Node* head = NULL;
    int daKhoiTao = 0;
    
    menu();
    while (1) {
        int chon;
        scanf("%d", &chon);
        getchar();
        char hotencantim[100];
        
        switch(chon) {
            case 1: 
                daKhoiTao = 1;
                if (head != NULL) {
                    giaiphongbonho(head);
                    head = NULL;
                }
                
                printf("Ban vua chon chuc nang 1: Tao danh sach sinh vien\n");
                printf("Nhap so luong sinh vien: ");
                int n;
                scanf("%d", &n);
                getchar();
                
                for (int i = 0; i < n; i++) {
                    printf("Nhap thong tin sinh vien thu %d:\n", i+1);
                    sinhvien sv = nhapthongtinSv();
                    Node* newNode = taoNode(sv);
                    
                    
                    if (head == NULL) {
                        head = newNode;
                    } else {
                        Node* temp = head;
                        while (temp->next != NULL) {
                            temp = temp->next;
                        }
                        temp->next = newNode;
                    }
                }
                break;
                
            case 2: 
                if (!daKhoiTao) {
                    printf("Vui long tao danh sach sinh vien truoc\n");
                } else {
                    printf("Ban vua chon chuc nang 2: Hien thi danh sach sinh vien\n");    
                    hienthidanhsach(head);
                }
                break;
                
            case 3:
                if (!daKhoiTao) {
                    printf("Vui long tao danh sach sinh vien truoc\n");
                } else {
                    printf("Ban vua chon chuc nang 3: Chen them mot sinh vien vao sau sinh vien bat ki\n");    
                    printf("Nhap ho ten sinh vien o truoc: ");
                    fgets(hotencantim, sizeof(hotencantim), stdin);
                    hotencantim[strcspn(hotencantim,"\n")] = '\0';
                    head = chensvbatky(head, hotencantim);
                    printf("Danh sach da duoc cap nhat\n");
                    hienthidanhsach(head);
                }
                break;
                
            case 4: 
                if (!daKhoiTao) {
                    printf("Vui long tao danh sach sinh vien truoc\n");
                } else {
                    printf("Ban vua chon chuc nang 4: Xoa mot sinh vien\n");
                    printf("Nhap ho ten sinh vien can xoa: ");
                    fgets(hotencantim, sizeof(hotencantim), stdin);
                    hotencantim[strcspn(hotencantim,"\n")] = '\0';
                    head = xoasinhvien(head, hotencantim);
                    printf("Danh sach da duoc cap nhat\n");
                    hienthidanhsach(head);
                }
                break;
                
            case 5: 
                if (!daKhoiTao) {
                    printf("Vui long tao danh sach sinh vien truoc\n");
                } else {
                    printf("Ban vua chon chuc nang 5: Sua mot sinh vien\n");
                    printf("Nhap ho ten sinh vien can sua: ");
                    fgets(hotencantim, sizeof(hotencantim), stdin);
                    hotencantim[strcspn(hotencantim,"\n")] = '\0';
                    head = suasinhvien(head, hotencantim);
                    printf("Danh sach da duoc cap nhat\n");
                    hienthidanhsach(head);
                }
                break;
                
            case 6:
                if (!daKhoiTao) {
                    printf("Vui long tao danh sach sinh vien truoc\n");
                } else {
                    printf("Ban vua chon chuc nang 6: Sap xep sinh vien theo diem\n");
                    head = sapxepTheoDiem(head);
                    printf("Danh sach da duoc sap xep theo diem\n");
                    hienthidanhsach(head);
                }
                break;
                
            case 7: 
             
                giaiphongbonho(head);
                printf("Chuong trinh ket thuc\n");
                return 0;
                
            default: 
                printf("Lua chon khong hop le, vui long nhap lai\n");
        }
        menu();
    }
    
    return 0;
}
```
## 2
```C
#include<stdio.h>
#include<stdlib.h>
typedef struct Node{
	int data;
	Node* next;
}Node;

Node* top =NULL;

int isEmpty(){
	return top == NULL;
}

int pop()
{
	if (isEmpty()) return -1;
	Node* temp = top;
	int value = temp->data;
	top = top->next;
	free(temp);
	return value;
}
void push(int value)
{
	Node*newNode = (Node*)malloc(sizeof(Node));
	if(newNode == NULL) return;
	newNode->data = value;
	newNode->next = top;
	top = newNode;
}
int peek(){
	if(isEmpty()) return -1;
	return top->data;
}
void destroy()
{
	while (!isEmpty()){
		pop();
	}
}
void chuyencoso(int n, int a){
	destroy();
	while(n != 0)
	{
		push(n%a);
		n/=a;
	}
	while(!isEmpty())
	{
		int tmp = pop();
		if (tmp < 10)
		printf("%d", tmp);
		else{
			printf("%c", tmp - 10 + 'A');
		}
	}
}

int main(){

		int n,a;
		scanf("%d", &n);
		scanf("%d", &a);
		chuyencoso(n,a);
}
```
