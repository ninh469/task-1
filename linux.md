# I. Kiến trúc tổng quan

- Chia làm 3 phần: `Kernel` -> `Shell` -> `Applications`
  
   - `Kernel`(nhân): là phần quan trọng được coi như là trái tim của HĐH, chứa các module, thư viện quản lý và giao tiếp với phần cứng và các ứng dụng
   
   - `Shell`: Có chức năng thực thi các lệnh từ người dùng hoặc từ các ứng dụng yêu cầu chuyển đến cho Kernel xử lý, trung gian giữa Kernel và Appications
   
   - Có các loại `Shell` như sau: Bash, Zsh, Fish, Ksh, Csh. `Bash` là cái phổ biến nhất
 
   - Application: là các chương trình phần mềm được thiết kế để thực hiện các nhiệm vụ cụ thể hoặc cung cấp các các dịch vụ cho người dùng

# II. Các thao tác cơ bản 

`$` -> dùng cho người dùng thông thường

![image](https://github.com/user-attachments/assets/46f45397-5a7b-41ed-a25e-9852e31f224e)

`#` -> dùng cho `root`

- Tổng hợp các phím tắt

| Phím Tắt | Mô tả |
|----------|-------|
| `Ctrl + Alt + T`| mở |
|`Ctrl + Alt + D` | đóng |
|`Ctr + C`| dừng 1 câu lệnh đang chạy |
| `Ctrl + A` | di chuyển đến đầu dòng lệnh |
| `Ctrl + E` | di chuyển đến cuối dòng lệnh |
| `Ctrl + U` | xóa từ vị trí con trỏ đến đầu dòng |
| `Ctrl +  K` | xóa từ vị trí con trỏ đến cuối dòng | 
| `Ctrl + R` | tìm kiếm trong lịch sử |

## Các câu lệnh về thư mục và tập tin 

`ls`: xem nội dung của thư mục

![image](https://github.com/user-attachments/assets/18dcc86d-70e9-4f03-ab6f-904a44c1410a)

- `ls -a`: liệt kê các file ẩn

![image](https://github.com/user-attachments/assets/8b9ba2cb-c922-4d98-8ec9-cc33ae8d46af)

- `ls -l`: liệt kê các tệp 

![image](https://github.com/user-attachments/assets/8b8f92b7-7f2f-47ed-8f9a-b7b7c11d8ef1)

- `ls -R`: liệt kê nội dung của thư mục hiện tại và thư mục con của nó

`cd` : sử dụng để thay đổi thư mực làm việc hiện tại

`pwd` : được sử dụng để hiện thị thư mục làm việc hiện tại

![image](https://github.com/user-attachments/assets/cc380fd1-1e28-4da5-9f81-5af9dbf202fd)

ở đây chúng ta đang ở thư mục gốc

`mkdir` : cho phép tạo toàn bộ cấu trúc thư mục, bao gồm mọi thư mục cha cần thiết, chỉ trong một lệnh

`cp`  : được sử dụng để sao chép tệp và thư mục từ vị trí này sang vị trí khác.

`cat` : cho phép nối và hiển thị nội dung của các tệp văn bản.

![image](https://github.com/user-attachments/assets/8c5808f6-826d-401a-9280-27aaaa8b81f1)

- `cat -n` : Hiển thị đầu ra theo số dòng

![image](https://github.com/user-attachments/assets/00f5526b-f957-4553-926d-dfa13b4b0e00)

- `cat -E` : Hiển thị ký tự $ ở cuối mỗi dòng

![image](https://github.com/user-attachments/assets/c1503893-bd95-4c5b-b3f0-6faa01ddde5e)

- `cat -s`: Gộp nhiều dòng trống liền kề thành một

`nano` : chỉnh sửa nội dung

![image](https://github.com/user-attachments/assets/9c9ecd48-12b9-4a13-a4a6-7157203548c9)

`tree`: để hiển thị cấu trúc thư mục theo định dạng dạng cây.

![image](https://github.com/user-attachments/assets/b3a4134b-3950-44f3-bdba-9a5b2b065e54)

`ln` : Lệnh được sử dụng để tạo liên kết, là các tệp đặc biệt trỏ đến các tệp hoặc thư mục khác. Có hai loại liên kết: liên kết cứng và liên kết tượng trưng

continued để hè e bổ sung thêm nhé

