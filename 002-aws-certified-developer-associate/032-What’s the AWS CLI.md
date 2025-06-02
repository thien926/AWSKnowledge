# AWS CLI là gì?

1. **A tool that enables you to interact with AWS services using commands in your command-line shell**  
   - Dịch: Một công cụ cho phép bạn tương tác với các dịch vụ AWS bằng cách sử dụng lệnh ngay trong shell dòng lệnh.  
   - Giải thích: Thay vì vào Console web, bạn gõ lệnh `aws <service> <operation>` để thao tác trực tiếp.

2. **Direct access to the public APIs of AWS services**  
   - Dịch: Truy cập trực tiếp vào các API công khai của dịch vụ AWS.  
   - Giải thích: CLI gọi thẳng đến endpoint API AWS nên hỗ trợ đầy đủ các chức năng tương tự SDK hoặc Console.

3. **You can develop scripts to manage your resources**  
   - Dịch: Bạn có thể viết script để quản lý tài nguyên.  
   - Giải thích: Tự động hóa quy trình triển khai, sao lưu, giám sát… thông qua shell script hoặc file `.bat`, `.sh`.

4. **It’s open-source https://github.com/aws/aws-cli**  
   - Dịch: Đây là phần mềm mã nguồn mở tại https://github.com/aws/aws-cli  
   - Giải thích: Bạn có thể xem, đóng góp hoặc fork code trên GitHub.

5. **Alternative to using AWS Management Console**  
   - Dịch: Thay thế cho việc sử dụng Bảng điều khiển quản lý AWS.  
   - Giải thích: Thích hợp với DevOps, CI/CD, khi làm việc trên server không có giao diện đồ họa.

---

### Ví dụ sử dụng AWS CLI
```bash
# Tải file lên S3
aws s3 cp myfile.txt s3://ccp-mybucket/myfile.txt

# Liệt kê nội dung bucket
aws s3 ls s3://ccp-mybucket
```

> **Lưu ý:** Trước khi chạy, bạn cần cấu hình Access Key bằng `aws configure` để CLI biết thông tin xác thực.