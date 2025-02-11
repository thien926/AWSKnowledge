# **Hướng Dẫn Chi Tiết Tạo IAM Policies Trên AWS** 🚀  

IAM Policies là các tập hợp quyền xác định những gì một IAM User, Group hoặc Role có thể làm trong AWS. Policies giúp kiểm soát truy cập chặt chẽ và bảo mật hơn.  

Dưới đây là hướng dẫn chi tiết từng bước để tạo IAM Policy trên AWS.  

---

## **1️⃣ Các loại IAM Policies trên AWS**  
AWS hỗ trợ nhiều loại policies, phổ biến nhất gồm:  
🔹 **AWS Managed Policies**: Policies do AWS tạo sẵn (ví dụ: `AmazonS3FullAccess`).  
🔹 **Customer Managed Policies**: Policies do người dùng tự tạo, linh hoạt hơn.  
🔹 **Inline Policies**: Policies gán trực tiếp vào User, Group hoặc Role (không thể tái sử dụng).  

👉 **Trong bài này, ta sẽ tập trung vào "Customer Managed Policies" (tự tạo)**.  

---

## **2️⃣ Tạo IAM Policy bằng AWS Console** (Giao diện Web)  

### 🔹 **Bước 1: Truy cập AWS IAM Console**  
- Đăng nhập AWS Console tại 👉 [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)  
- Ở menu bên trái, chọn **Policies** → Nhấn **Create policy**  

### 🔹 **Bước 2: Chọn dịch vụ AWS cần cấp quyền**  
- Chọn **Service** (Dịch vụ cần cấp quyền), ví dụ **S3**  
- Chọn **Actions** (Hành động được phép làm)  
  - **List**: Xem danh sách S3 Buckets  
  - **Read**: Đọc dữ liệu từ S3  
  - **Write**: Ghi dữ liệu lên S3  

📌 **Ví dụ: Policy cho phép User chỉ có quyền đọc dữ liệu từ S3**  
- **Service**: S3  
- **Actions**: `ListBucket`, `GetObject`  
- **Resources**: Chọn **Specific** và nhập ARN của bucket, ví dụ:  
  ```
  arn:aws:s3:::my-example-bucket
  arn:aws:s3:::my-example-bucket/*
  ```

### 🔹 **Bước 3: Thêm điều kiện (Condition) nếu cần**  
📌 **Ví dụ: Chỉ cho phép truy cập từ một địa chỉ IP cụ thể**  
- Key: `aws:SourceIp`  
- Value: `192.168.1.1/32`  

### 🔹 **Bước 4: Kiểm tra JSON Policy**  
Bạn có thể xem JSON của policy đã tạo. Dưới đây là JSON cho policy trên:  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::my-example-bucket",
                "arn:aws:s3:::my-example-bucket/*"
            ],
            "Condition": {
                "IpAddress": {
                    "aws:SourceIp": "192.168.1.1/32"
                }
            }
        }
    ]
}
```

### 🔹 **Bước 5: Đặt tên và tạo Policy**  
- **Policy name**: `S3ReadOnlyPolicy`  
- Nhấn **Create policy** để hoàn tất.  

✅ **Policy đã được tạo thành công!** 🎉  

---

## **3️⃣ Tạo IAM Policy bằng AWS CLI** (Dòng lệnh)  

### 🔹 **Bước 1: Viết JSON Policy**  
Tạo file `s3-readonly-policy.json` với nội dung sau:  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::my-example-bucket",
                "arn:aws:s3:::my-example-bucket/*"
            ]
        }
    ]
}
```

### 🔹 **Bước 2: Tạo Policy bằng AWS CLI**  
Chạy lệnh sau để tạo IAM Policy:  
```bash
aws iam create-policy --policy-name S3ReadOnlyPolicy --policy-document file://s3-readonly-policy.json
```

📌 **Kết quả mong đợi:**  
```json
{
    "Policy": {
        "PolicyName": "S3ReadOnlyPolicy",
        "PolicyId": "ANPAEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy",
        "Path": "/",
        "DefaultVersionId": "v1",
        "AttachmentCount": 0,
        "PermissionsBoundaryUsageCount": 0,
        "IsAttachable": true,
        "CreateDate": "2025-02-11T12:00:00Z",
        "UpdateDate": "2025-02-11T12:00:00Z"
    }
}
```

✅ **IAM Policy đã được tạo thành công bằng AWS CLI!** 🚀  

---

## **4️⃣ Gán IAM Policy cho User, Group hoặc Role**  

📌 **Gán Policy cho User `developer_user`**  
```bash
aws iam attach-user-policy --user-name developer_user \
    --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
```

📌 **Gán Policy cho Group `Developers`**  
```bash
aws iam attach-group-policy --group-name Developers \
    --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
```

📌 **Gán Policy cho Role `LambdaExecutionRole`**  
```bash
aws iam attach-role-policy --role-name LambdaExecutionRole \
    --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
```

✅ **Policy đã được gán thành công!** 🎉  

---

## **5️⃣ Kiểm tra & Xóa IAM Policy**  

📌 **Liệt kê tất cả policies trong tài khoản AWS**  
```bash
aws iam list-policies --scope Local
```

📌 **Xem chi tiết policy `S3ReadOnlyPolicy`**  
```bash
aws iam get-policy --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
```

📌 **Xem nội dung JSON của policy**  
```bash
aws iam get-policy-version --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy --version-id v1
```

📌 **Xóa policy nếu không còn dùng**  
🔸 **Bước 1**: Gỡ policy khỏi tất cả Users, Groups, Roles  
```bash
aws iam detach-user-policy --user-name developer_user --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
aws iam detach-group-policy --group-name Developers --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
aws iam detach-role-policy --role-name LambdaExecutionRole --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
```

🔸 **Bước 2**: Xóa policy  
```bash
aws iam delete-policy --policy-arn arn:aws:iam::123456789012:policy/S3ReadOnlyPolicy
```

✅ **Policy đã bị xóa thành công!** 🚀  

---

## **6️⃣ Tổng kết**  
✔ **IAM Policies giúp kiểm soát quyền truy cập tài nguyên AWS**  
✔ **Tạo Policy bằng AWS Console hoặc AWS CLI**  
✔ **Gán Policy cho User, Group, Role để cấp quyền**  
✔ **Kiểm tra và xóa Policy khi không còn sử dụng**  
