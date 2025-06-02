# IAM Roles cho Dịch vụ AWS

1. **Some AWS services will need to perform actions on your behalf**  
   - Dịch: *Một số dịch vụ AWS cần thực hiện các hành động thay bạn*  
   - Giải thích: Khi bạn khởi chạy EC2, Lambda, CloudFormation… các dịch vụ này phải gọi API AWS để đọc/ghi tài nguyên thay bạn.

2. **To do so, we will assign permissions to AWS services with IAM Roles**  
   - Dịch: *Để làm được điều đó, chúng ta gán quyền cho dịch vụ AWS thông qua IAM Role*  
   - Giải thích: Thay vì chia sẻ Access Key, bạn tạo một `IAM Role` chứa policy phù hợp rồi đính nó vào dịch vụ.

3. **Common roles:**  
   - **EC2 Instance Roles**  
     - Dành cho máy chủ ảo EC2, ví dụ: cho phép đọc file từ S3 hoặc ghi log vào CloudWatch.  
   - **Lambda Function Roles**  
     - Cấp quyền cho hàm Lambda để truy cập DynamoDB, Kinesis…  
   - **Roles for CloudFormation**  
     - Cho phép CloudFormation tự động tạo/điều chỉnh tài nguyên theo template.

---

### Sơ đồ minh họa

```mermaid
flowchart LR
  subgraph AWS Service
    EC2[EC2 Instance<br/>(Virtual Server)]
  end
  IAMRole[IAM Role]
  AWS[AWS APIs]
  
  IAMRole -- Gán cho --> EC2
  EC2 -- Thực hiện API gọi --> AWS
```

- **Giải thích sơ đồ:**  
  1. Tạo một `IAM Role` với policy xác định quyền (ví dụ: `AmazonS3ReadOnlyAccess`).  
  2. Đính role này vào EC2 instance khi khởi tạo hoặc về sau.  
  3. Ứng dụng chạy trên EC2 dùng role để gọi thẳng API AWS mà không cần Access Key.