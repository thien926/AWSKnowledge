## Amazon EC2

1. **EC2 is one of the most popular of AWS’ offering**  
   - Dịch: EC2 là một trong những dịch vụ phổ biến nhất của AWS  
   - Giải thích: Phần lớn ứng dụng và workload trên AWS đều chạy dưới dạng máy ảo EC2.

2. **EC2 = Elastic Compute Cloud = Infrastructure as a Service**  
   - Dịch: EC2 = Elastic Compute Cloud = Hạ tầng như một Dịch vụ (IaaS)  
   - Giải thích: AWS cung cấp tài nguyên tính toán (CPU, RAM, mạng) dưới dạng dịch vụ, bạn thuê theo nhu cầu.

3. **It mainly consists in the capability of:**  
   - Dịch: EC2 chủ yếu bao gồm các khả năng sau:

   - **Renting virtual machines (EC2)**  
     - Dịch: Thuê máy ảo (EC2)  
     - Giải thích: Khởi tạo instance với nhiều loại AMI, kích thước (instance type), vùng (region) khác nhau.

   - **Storing data on virtual drives (EBS)**  
     - Dịch: Lưu trữ dữ liệu trên ổ đĩa ảo (EBS)  
     - Giải thích: Gắn volume EBS vào instance để lưu dữ liệu bền vững, có thể tách rời và backup dễ dàng.

   - **Distributing load across machines (ELB)**  
     - Dịch: Phân phối tải trên nhiều máy (ELB)  
     - Giải thích: Dùng Elastic Load Balancer để cân bằng lưu lượng giữa nhiều instance, tăng tính sẵn sàng và khả năng chịu lỗi.

   - **Scaling the services using an auto-scaling group (ASG)**  
     - Dịch: Tự động mở rộng dịch vụ bằng nhóm Auto Scaling (ASG)  
     - Giải thích: Tự động thêm hoặc bớt instance dựa trên chính sách (CPU, request count…) để tối ưu chi phí và hiệu năng.

4. **Knowing EC2 is fundamental to understand how the Cloud works**  
   - Dịch: Hiểu EC2 là nền tảng cơ bản để nắm bắt cách thức hoạt động của điện toán đám mây  
   - Giải thích: EC2 thể hiện rõ mô hình thuê tài nguyên on-demand, cho phép bạn linh hoạt triển khai, vận hành hệ thống trên AWS.

---

> **Tóm tắt:**  
> Amazon EC2 cung cấp khả năng thuê máy ảo linh hoạt, lưu trữ bền vững, cân bằng tải và tự động mở rộng – là cốt lõi cho mọi kiến trúc hạ tầng trên AWS.