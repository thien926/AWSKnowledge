## Kết quả cuối cùng (Final Answer)

# Thực hành: Khởi chạy EC2 Instance chạy Linux

- **Chúng ta sẽ khởi chạy server ảo đầu tiên bằng AWS Console**  
  Giải thích: Dùng giao diện web AWS Management Console để tạo một EC2 instance.

- **Chúng ta sẽ có cái nhìn tổng quan cấp cao về các tham số khác nhau**  
  Giải thích: Tìm hiểu và cấu hình các tùy chọn như AMI (hệ điều hành), instance type (CPU/RAM), VPC, subnet, security group…

- **Chúng ta sẽ thấy web server của mình được khởi tạo bằng EC2 User Data**  
  Giải thích: Chèn script tự động (User Data) để cài đặt Apache/Nginx, triển khai website ngay khi instance chạy lần đầu.

- **Chúng ta sẽ học cách Start / Stop / Terminate instance**  
  Giải thích: Thực hành các thao tác quản lý vòng đời instance:
  1. **Start**: Bật lại instance đã tắt.  
  2. **Stop**: Dừng instance để tắt máy nhưng vẫn giữ dữ liệu EBS.  
  3. **Terminate**: Xóa hẳn instance và giải phóng tài nguyên.