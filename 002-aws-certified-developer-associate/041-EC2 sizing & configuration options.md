## Lựa chọn kích thước & cấu hình EC2

1. **Operating System (OS): Linux, Windows hoặc Mac OS**  
   - Dịch: Hệ điều hành (OS): Linux, Windows hoặc Mac OS  
   - Giải thích: Chọn Amazon Machine Image (AMI) tương ứng với hệ điều hành cần chạy ứng dụng.

2. **How much compute power & cores (CPU)**  
   - Dịch: Sức mạnh xử lý & số lõi (CPU)  
   - Giải thích: Lựa chọn `instance type` (ví dụ: t3.micro, m5.large…) phù hợp với nhu cầu tính toán và song song.

3. **How much random-access memory (RAM)**  
   - Dịch: Dung lượng bộ nhớ truy cập ngẫu nhiên (RAM)  
   - Giải thích: Cân đối RAM để chạy được ứng dụng, database hoặc cache mượt mà.

4. **How much storage space:**  
   - Dịch: Dung lượng lưu trữ:  
     - **Network-attached (EBS & EFS)**  
       - *Giải thích:*  
         - **EBS (Elastic Block Store):** Ổ đĩa block bền, gắn vào 1 instance.  
         - **EFS (Elastic File System):** Ổ chia sẻ file giữa nhiều instance.  
     - **Hardware (EC2 Instance Store)**  
       - *Giải thích:* Ổ lưu trữ cục bộ (ephemeral), cho I/O rất cao nhưng dữ liệu mất khi dừng/terminate instance.

5. **Network card: speed of the card, Public IP address**  
   - Dịch: Card mạng: tốc độ kết nối, địa chỉ IP công khai  
   - Giải thích: Chọn băng thông (Mbps/Gbps) phù hợp. Gán Elastic IP hoặc Public IP để truy cập từ Internet.

6. **Firewall rules: security group**  
   - Dịch: Luật tường lửa: security group  
   - Giải thích: Định nghĩa inbound/outbound, mở/đóng port (HTTP, SSH, database…) cho instance.

7. **Bootstrap script (configure at first launch): EC2 User Data**  
   - Dịch: Script khởi tạo (cấu hình khi lần đầu khởi chạy): EC2 User Data  
   - Giải thích: Cho phép chạy tự động shell script hoặc cloud-init để cài đặt phần mềm, cập nhật, kéo code… ngay khi instance chạy lần đầu.

---

> **Tóm tắt:**  
> Khi tạo EC2, bạn cần cân nhắc hệ điều hành, CPU, RAM, lưu trữ, mạng, bảo mật và script khởi tạo để đảm bảo instance hoạt động ổn định, bảo mật và đáp ứng đúng nhu cầu ứng dụng.