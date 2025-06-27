# I. Crawl 
- Crawl ( hay spider/bot ) là quá trình tự động thu thập thông tin từ các trang web trên internet, nó sẽ truy cập mọi URL và thông tin có liên quan nội dụng của trang web và phản hồi để lấy các tài nguyên như văn bản, hình ảnh, video, âm thanh, tệp tin, vv.
- Những thông tin được crawl thu thập được sẽ được lưu vào `Index`, để xử lý, phân loại để chuẩn bị cho việc truy vấn tìm kiếm
- Crawl muốn truy cập mọi thông tin và index nhưng trong 1 số trường hợp chúng ta không muốn crwal truy cập và giải pháp để ngăn chặn là `robots.txt`.
# II. Robots.txt
Cấu trúc cơ bản của `robots.txt`
```
User-agent:
Allow:
Disallow:
```
VD: 
sao nhỏ này cấm nhiều thế @@

![image](https://github.com/user-attachments/assets/75e874d4-d51f-4bf9-9885-3e9748ce160b)

![image](https://github.com/user-attachments/assets/3863a937-801f-4550-8e55-bf6a849a39b5)

![image](https://github.com/user-attachments/assets/87178609-5586-4fed-92c5-b6a7c7844a3d)

Đây là cách ẩn nó khỏi crawl:
```
User-agent: *
Disallow: /*.conf$
```
# III. Cách để sử dụng GG nâng cao

E sẽ minh họa bằng chạy task btt cụ thể là về Blue Team T_T

![image](https://github.com/user-attachments/assets/387967be-61ce-4d56-ae0d-35966d39f292)

hmmm thấy cũng giảm giảm
![image](https://github.com/user-attachments/assets/79b1d8c2-fea1-450f-84b9-64dc4edc71ef)

site:cyberjutsu.io "blue team" có nghĩa là mình chỉ tìm `blue team` trong web `cyberjutsu.io` thôi.
![image](https://github.com/user-attachments/assets/b185cef2-9df0-4584-affb-1826bff037a8)

- Mình có thể dùng thêm cú pháp `filetype` nữa tùy vào mục đích 
- Mấy cái hay hay e mò mò được
![image](https://github.com/user-attachments/assets/a2807584-b7ad-4067-ad1b-87b6adb39975)
jvtr sao có mỗi AT21D bị lộ gmail act @@
![image](https://github.com/user-attachments/assets/96b9ba39-109b-4161-9f25-02cb9cc9eb7e)
![image](https://github.com/user-attachments/assets/b3a7285f-2be4-4674-8f73-7bb687ad3ef0)
![image](https://github.com/user-attachments/assets/91554e56-7f5e-4b63-bf97-1b6a3f5b9036)
sao k thấy itra :(((
![image](https://github.com/user-attachments/assets/e4e28c55-dbd6-4001-adaa-870b82a8a9e4)





