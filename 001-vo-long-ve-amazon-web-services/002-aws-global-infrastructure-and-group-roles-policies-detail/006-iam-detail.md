# **AWS IAM (Identity and Access Management) Chi Tiết**  

## **1️⃣ AWS IAM là gì?**  
**AWS IAM (Identity and Access Management)** là một dịch vụ giúp bạn quản lý quyền truy cập vào tài nguyên AWS một cách an toàn. Với IAM, bạn có thể:  
✅ **Tạo và quản lý** người dùng, nhóm và vai trò (**users, groups, roles**)  
✅ **Kiểm soát quyền truy cập** bằng cách sử dụng **policies** (chính sách bảo mật)  
✅ **Bảo mật tài khoản AWS** bằng xác thực đa yếu tố (MFA)  
✅ **Trao quyền truy cập tạm thời** bằng AWS STS (Security Token Service)  
✅ **Quản lý khóa truy cập** cho AWS CLI, SDK và API  

IAM rất quan trọng vì nó giúp bạn đảm bảo **chỉ những người hoặc dịch vụ có quyền mới có thể truy cập tài nguyên AWS**.  

---

## **2️⃣ Các thành phần chính của AWS IAM**  

### **1. IAM Users (Người dùng IAM)**
- IAM User là một danh tính trong AWS đại diện cho một người hoặc ứng dụng.  
- Mỗi IAM User có thể có **username, password**, và **Access Key** để truy cập AWS bằng CLI hoặc API.  
- Mặc định, IAM User **không có quyền truy cập**, trừ khi được gán **permissions**.  

📌 **Ví dụ tạo user mới trên AWS CLI:**  
```bash
aws iam create-user --user-name user_demo
```

---

### **2. IAM Groups (Nhóm IAM)**
- IAM Groups giúp **tổ chức và quản lý** nhiều IAM Users cùng một lúc.  
- Bạn có thể gán **chính sách bảo mật (policies)** cho IAM Groups để áp dụng quyền cho tất cả thành viên trong nhóm.  
- **Ví dụ:**  
  - Nhóm **Developers** có quyền truy cập EC2 và S3.  
  - Nhóm **Admins** có quyền quản lý toàn bộ AWS.  

📌 **Ví dụ tạo group mới trên AWS CLI:**  
```bash
aws iam create-group --group-name DevTeam
```

---

### **3. IAM Roles (Vai trò IAM)**
- IAM Roles là danh tính có quyền truy cập nhưng **không thuộc về một người cụ thể**.  
- **Dùng để cấp quyền tạm thời** cho:
  ✅ **AWS Services** (ví dụ: EC2 có quyền truy cập S3).  
  ✅ **Ứng dụng bên ngoài** (ví dụ: AWS Lambda gọi DynamoDB).  
  ✅ **Tài khoản AWS khác** (Cross-Account Access).  

📌 **Ví dụ tạo role cho EC2 có quyền đọc từ S3:**  
```bash
aws iam create-role --role-name S3ReadOnlyRole \
    --assume-role-policy-document file://trust-policy.json
```

---

### **4. IAM Policies (Chính sách IAM)**
- IAM Policies là **bộ quy tắc xác định quyền** của IAM Users, Groups hoặc Roles.  
- Policies được viết bằng **JSON**, bao gồm:  
  ✅ **Effect**: "Allow" (cho phép) hoặc "Deny" (từ chối).  
  ✅ **Action**: Hành động có thể thực hiện (ví dụ: `s3:ListBucket`).  
  ✅ **Resource**: Tài nguyên AWS nào được phép thao tác.  

📌 **Ví dụ policy cho phép đọc S3:**  
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::my-bucket"
    }
  ]
}
```

📌 **Gán policy cho một user bằng AWS CLI:**  
```bash
aws iam attach-user-policy --user-name user_demo \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

### **5. IAM MFA (Xác thực đa yếu tố)**
- **Multi-Factor Authentication (MFA)** giúp tăng cường bảo mật bằng cách yêu cầu **một mã xác thực thứ hai** ngoài mật khẩu.  
- AWS hỗ trợ **MFA ảo (ứng dụng như Google Authenticator)** và **MFA vật lý (YubiKey, U2F Security Keys, v.v.).**  

📌 **Bật MFA cho IAM User:**  
1. Truy cập **AWS IAM Console**  
2. Chọn user → **Security credentials** → **Assign MFA**  
3. Quét mã QR bằng Google Authenticator  
4. Nhập mã OTP để xác nhận  

---

## **3️⃣ Các loại quyền truy cập trong AWS IAM**  

| Loại quyền truy cập | Mô tả |
|--------------------|--------|
| **Console Access** | Truy cập AWS bằng giao diện web (AWS Console). |
| **Programmatic Access** | Truy cập AWS bằng CLI, SDK hoặc API bằng Access Key. |
| **Temporary Access** | Dùng IAM Roles hoặc AWS STS để cấp quyền tạm thời. |

---

## **4️⃣ Best Practices (Thực hành tốt nhất với AWS IAM)**  

✅ **Nguyên tắc “Least Privilege”**: Chỉ cấp quyền tối thiểu cần thiết.  
✅ **Bật MFA**: Bắt buộc MFA cho tài khoản root và IAM Users quan trọng.  
✅ **Dùng IAM Roles thay vì IAM Users**: Hạn chế việc tạo Access Keys cố định.  
✅ **Xóa hoặc xoá quyền tài khoản root**: Không dùng tài khoản root trừ trường hợp cần thiết.  
✅ **Ghi log hoạt động IAM bằng AWS CloudTrail**: Giúp theo dõi và kiểm tra các thay đổi IAM.  

---

## **5️⃣ Tổng kết**
✔ **IAM Users**: Đại diện cho cá nhân hoặc ứng dụng, cần được cấp quyền.  
✔ **IAM Groups**: Nhóm người dùng có chung quyền hạn.  
✔ **IAM Roles**: Cấp quyền tạm thời cho AWS Services hoặc tài khoản khác.  
✔ **IAM Policies**: Quy định ai được làm gì trên tài nguyên AWS.  
✔ **IAM MFA**: Tăng cường bảo mật với xác thực 2 lớp.  