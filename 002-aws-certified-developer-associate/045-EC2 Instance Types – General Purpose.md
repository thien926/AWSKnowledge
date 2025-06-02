# EC2 Instance Types – Tính toán Chung (General Purpose)

- **Phù hợp cho nhiều loại workload**  
  Ví dụ: web server, kho mã nguồn (code repositories) hoặc các ứng dụng dùng tài nguyên cân bằng.

- **Cân bằng giữa:**  
  - **Compute** (CPU): hiệu năng xử lý tổng quát  
  - **Memory** (RAM): bộ nhớ làm việc  
  - **Networking** (Mạng): băng thông kết nối

- **Trong khóa học, chúng ta sẽ sử dụng `t2.micro`**  
  - Đây là instance thuộc lớp T2 (Burstable General Purpose)  
  - Thông thường đi kèm **Free Tier** (dùng miễn phí giới hạn)  
  - Cung cấp hiệu năng cơ bản với khả năng “burst” tăng CPU khi cần.