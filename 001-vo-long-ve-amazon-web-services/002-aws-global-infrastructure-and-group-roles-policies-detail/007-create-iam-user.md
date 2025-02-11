# **Hướng Dẫn Chi Tiết Tạo IAM User Trên AWS** 🚀  

IAM User là tài khoản người dùng trong AWS, được sử dụng để quản lý quyền truy cập vào tài nguyên AWS. Dưới đây là hướng dẫn chi tiết để tạo IAM User theo từng bước cụ thể.  

---

## **1️⃣ Tạo IAM User bằng AWS Console** (Giao diện Web)  
### 🔹 **Bước 1: Truy cập AWS IAM Console**  
- Đăng nhập AWS Console tại 👉 [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)  
- Trong menu bên trái, chọn **Users** → Nhấn **Add users**  

### 🔹 **Bước 2: Nhập thông tin User**  
- **User name**: Nhập tên user (ví dụ: `developer_user`).  
- **Chọn loại quyền truy cập**:  
  ✅ **AWS Management Console access** (truy cập giao diện web)  
  ✅ **Access key - Programmatic access** (truy cập qua AWS CLI, SDK, API)  

📌 **Nếu chọn AWS Management Console access:**  
- **Chọn phương thức tạo mật khẩu**:  
  ✅ **Tự động tạo mật khẩu** (Auto-generated password)  
  ✅ **Tự đặt mật khẩu** (Custom password)  
- Bật tùy chọn **User must create a new password at next sign-in** để yêu cầu đổi mật khẩu lần đầu đăng nhập.  

### 🔹 **Bước 3: Gán quyền cho User**  
Có 3 cách để cấp quyền cho IAM User:  
1. **Thêm vào group có sẵn** (ví dụ: nhóm `Developers`)  
2. **Gán policy trực tiếp** (ví dụ: `AmazonS3ReadOnlyAccess`)  
3. **Copy quyền từ User khác**  

📌 **Ví dụ: Gán quyền đọc S3**  
- Tìm kiếm `AmazonS3ReadOnlyAccess` → Chọn **Attach**  

### 🔹 **Bước 4: Xác nhận & tạo User**  
- Kiểm tra lại thông tin → Nhấn **Create user**  
- Lưu lại **Access Key ID** và **Secret Access Key** (nếu có).  
- Nếu user có AWS Console access, gửi đường link đăng nhập cho họ.  

📌 **Link đăng nhập IAM**:  
```
https://<AWS-Account-ID>.signin.aws.amazon.com/console
```

✅ **Hoàn tất! IAM User đã được tạo thành công.** 🎉  

---

## **2️⃣ Tạo IAM User bằng AWS CLI** (Dòng lệnh)  
Bạn có thể tạo IAM User nhanh chóng bằng **AWS CLI**.  

### 🔹 **Bước 1: Tạo User**
📌 Tạo User có tên `developer_user`:  
```bash
aws iam create-user --user-name developer_user
```
📌 Kết quả mong đợi:  
```json
{
    "User": {
        "Path": "/",
        "UserName": "developer_user",
        "UserId": "AIDEXAMPLEUSER",
        "Arn": "arn:aws:iam::123456789012:user/developer_user",
        "CreateDate": "2025-02-11T12:00:00Z"
    }
}
```

### 🔹 **Bước 2: Cấp quyền cho User**  
📌 Gán quyền **đọc S3** cho User bằng policy `AmazonS3ReadOnlyAccess`:  
```bash
aws iam attach-user-policy --user-name developer_user \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

### 🔹 **Bước 3: Tạo Access Key cho User**  
📌 Tạo Access Key để user có thể dùng AWS CLI hoặc API:  
```bash
aws iam create-access-key --user-name developer_user
```
📌 Kết quả mong đợi:  
```json
{
    "AccessKey": {
        "UserName": "developer_user",
        "AccessKeyId": "AKIAXXXXXX",
        "Status": "Active",
        "SecretAccessKey": "abcd1234efgh5678ijkl9012mnop3456qrstuv78",
        "CreateDate": "2025-02-11T12:05:00Z"
    }
}
```
🚨 **Lưu ý:** **SecretAccessKey chỉ hiển thị một lần**. Hãy lưu lại an toàn!  

### 🔹 **Bước 4: Kiểm tra danh sách IAM Users**  
📌 Xem danh sách tất cả IAM Users:  
```bash
aws iam list-users
```
📌 Kết quả mong đợi:  
```json
{
    "Users": [
        {
            "UserName": "developer_user",
            "UserId": "AIDEXAMPLEUSER",
            "Arn": "arn:aws:iam::123456789012:user/developer_user",
            "CreateDate": "2025-02-11T12:00:00Z"
        }
    ]
}
```

✅ **IAM User đã được tạo thành công bằng AWS CLI!** 🎉  

---

## **3️⃣ Cấu hình IAM User trên AWS CLI**  
Sau khi tạo IAM User và có **Access Key**, bạn có thể cấu hình AWS CLI để sử dụng user này.  

📌 **Chạy lệnh cấu hình AWS CLI:**  
```bash
aws configure
```
📌 Nhập thông tin:  
```
AWS Access Key ID [None]: AKIAXXXXXX
AWS Secret Access Key [None]: abcd1234efgh5678ijkl9012mnop3456qrstuv78
Default region name [None]: us-east-1
Default output format [None]: json
```
📌 **Kiểm tra user đang sử dụng:**  
```bash
aws sts get-caller-identity
```
📌 Kết quả mong đợi:  
```json
{
    "UserId": "AIDEXAMPLEUSER",
    "Account": "123456789012",
    "Arn": "arn:aws:iam::123456789012:user/developer_user"
}
```

✅ **AWS CLI đã được cấu hình với IAM User mới!** 🎉  

---

## **4️⃣ Xóa IAM User (nếu cần)**  
Nếu bạn muốn xóa một IAM User, hãy làm như sau:  

📌 **Bước 1: Xóa Access Key của User**  
```bash
aws iam delete-access-key --user-name developer_user --access-key-id AKIAXXXXXX
```

📌 **Bước 2: Xóa User khỏi Group (nếu có)**  
```bash
aws iam remove-user-from-group --user-name developer_user --group-name DevTeam
```

📌 **Bước 3: Xóa tất cả policies gán trực tiếp cho User**  
```bash
aws iam detach-user-policy --user-name developer_user --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

📌 **Bước 4: Xóa IAM User**  
```bash
aws iam delete-user --user-name developer_user
```
✅ **User đã bị xóa thành công.** 🚀  

---

## **5️⃣ Tổng kết**  
✔ **Tạo IAM User** qua AWS Console hoặc AWS CLI  
✔ **Gán quyền** thông qua Policies  
✔ **Tạo Access Key** để dùng AWS CLI / API  
✔ **Cấu hình AWS CLI** để sử dụng IAM User  
✔ **Xóa IAM User** khi không còn cần thiết  
