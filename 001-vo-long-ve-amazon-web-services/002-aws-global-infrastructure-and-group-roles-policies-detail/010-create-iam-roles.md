# **Hướng Dẫn Chi Tiết Tạo IAM Roles Trong AWS** 🚀  

IAM Role là một **danh tính IAM (Identity and Access Management)** trong AWS, cho phép **dịch vụ AWS hoặc người dùng được ủy quyền thực hiện các hành động cụ thể** mà không cần sử dụng username/password hoặc access key.  

Ví dụ:  
- **EC2 Instance Role**: EC2 có thể truy cập S3 mà không cần lưu credentials trong code.  
- **Lambda Execution Role**: Lambda có thể đọc dữ liệu từ DynamoDB.  
- **Cross-Account Role**: Một tài khoản AWS có thể truy cập tài nguyên của tài khoản AWS khác.  

---

## **1️⃣ Tạo IAM Role Bằng AWS Console**  

### **🔹 Bước 1: Truy Cập IAM Console**
- Vào **AWS Management Console**  
- Chọn **IAM**  
- Trong menu bên trái, chọn **Roles** → **Create role**  

---

### **🔹 Bước 2: Chọn Kiểu Role**
AWS sẽ hỏi **role này được sử dụng cho ai?**  
Bạn có thể chọn một trong các tùy chọn:  

1. **AWS service** (Dùng khi cấp quyền cho dịch vụ AWS như EC2, Lambda, ECS, v.v.)  
2. **Another AWS account** (Dùng để chia sẻ quyền giữa các tài khoản AWS)  
3. **Web identity** (Dùng cho các ứng dụng đăng nhập bằng Google, Facebook, Cognito, v.v.)  
4. **SAML 2.0 federation** (Dùng cho Single Sign-On - SSO)  
5. **Custom trust policy** (Tùy chỉnh chính sách trust theo yêu cầu)  

💡 **Ví dụ:** Nếu tạo IAM Role cho **EC2**, chọn **AWS service** → Chọn **EC2**.  

---

### **🔹 Bước 3: Gán Quyền (Attach Permissions Policies)**
- Chọn các **IAM Policies** để gán quyền cho Role.  
- Nếu muốn **EC2 có quyền đọc S3**, chọn **AmazonS3ReadOnlyAccess**.  
- Nếu cần chính sách tùy chỉnh, chọn **Create policy** và nhập JSON Policy.  

📌 **Ví dụ JSON Policy cho phép EC2 đọc S3 bucket cụ thể**:  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::my-secure-bucket",
                "arn:aws:s3:::my-secure-bucket/*"
            ]
        }
    ]
}
```

---

### **🔹 Bước 4: Định Nghĩa Trust Policy (Chính Sách Ủy Quyền)**
Trust Policy quyết định **ai có thể assume role này**.  
- Nếu tạo role cho **EC2**, AWS sẽ tự động thêm Trust Policy phù hợp.  
- Nếu tạo role cho **tài khoản AWS khác**, cần chỉ định tài khoản đó.  

📌 **Ví dụ Trust Policy cho phép EC2 assume role**:  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

📌 **Ví dụ Trust Policy cho phép tài khoản AWS khác assume role**:  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::123456789012:root"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```
(Thay `123456789012` bằng AWS Account ID muốn ủy quyền).  

---

### **🔹 Bước 5: Đặt Tên Và Tạo Role**
- Nhập **Role name** (ví dụ: `EC2-S3-ReadOnly-Role`).  
- Nhấn **Create role** để hoàn tất.  

---

## **2️⃣ Tạo IAM Role Bằng AWS CLI**  

### **📌 Bước 1: Tạo Trust Policy**  
Lưu JSON sau vào file `trust-policy.json`:  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

Chạy lệnh tạo IAM Role:  
```bash
aws iam create-role --role-name EC2-S3-ReadOnly-Role --assume-role-policy-document file://trust-policy.json
```

---

### **📌 Bước 2: Gán Policy Cho Role**  
Gán policy có sẵn:  
```bash
aws iam attach-role-policy --role-name EC2-S3-ReadOnly-Role --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```
Hoặc tạo policy mới và gán vào role:  
```bash
aws iam create-policy --policy-name MyCustomS3Policy --policy-document file://policy.json
aws iam attach-role-policy --role-name EC2-S3-ReadOnly-Role --policy-arn arn:aws:iam::123456789012:policy/MyCustomS3Policy
```

---

## **3️⃣ Gán IAM Role Cho EC2 Instance**  

### **Cách 1: Qua AWS Console**
- Vào **EC2 Dashboard** → Chọn **Instance**  
- Nhấn **Actions** → **Security** → **Modify IAM Role**  
- Chọn Role vừa tạo (`EC2-S3-ReadOnly-Role`) → Nhấn **Update IAM Role**  

### **Cách 2: Qua AWS CLI**
```bash
aws ec2 associate-iam-instance-profile --instance-id i-0123456789abcdef --iam-instance-profile Name=EC2-S3-ReadOnly-Role
```

---

## **4️⃣ Kiểm Tra IAM Role Đã Hoạt Động Hay Chưa**  

### **Dùng AWS CLI Trong EC2 Instance**  
- SSH vào EC2 instance  
- Kiểm tra IAM Role đã gán:  
  ```bash
  curl http://169.254.169.254/latest/meta-data/iam/security-credentials/
  ```
- Nếu thấy **Role name**, nghĩa là IAM Role đã được gán thành công.  
- Kiểm tra quyền bằng cách thử truy xuất file từ S3:  
  ```bash
  aws s3 ls s3://my-secure-bucket/
  ```

---

## **5️⃣ Khi Nào Nên Dùng IAM Role?**  

✔ **Nên dùng IAM Role khi:**  
✅ Cấp quyền truy cập AWS cho **dịch vụ AWS** mà không cần access key.  
✅ Cấp quyền truy cập **giữa các tài khoản AWS**.  
✅ Dùng với **AWS STS (Security Token Service)** để cấp quyền tạm thời.  

❌ **Không nên dùng IAM Role nếu:**  
🚫 Bạn cần cấp quyền cho **người dùng cụ thể** → Dùng IAM User thay vì Role.  
🚫 Bạn muốn truy cập từ bên ngoài AWS (trừ khi dùng STS AssumeRole).  

---

## **6️⃣ Tổng Kết**
✔ IAM Role giúp cấp quyền **bảo mật hơn** mà không cần lưu trữ access key.  
✔ Có thể tạo bằng **AWS Console hoặc AWS CLI**.  
✔ Cần cấu hình **Trust Policy** để cho phép AWS service hoặc tài khoản khác assume role.  
✔ Có thể gán Role cho **EC2, Lambda, ECS, hoặc tài khoản AWS khác**.  
