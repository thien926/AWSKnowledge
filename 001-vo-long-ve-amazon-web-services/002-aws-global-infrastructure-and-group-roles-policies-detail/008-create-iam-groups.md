# **Hướng Dẫn Chi Tiết Tạo IAM Groups Trên AWS** 🚀  

IAM Groups giúp quản lý nhiều IAM Users cùng một lúc bằng cách gán quyền chung cho cả nhóm thay vì từng user riêng lẻ. Điều này giúp quản lý quyền truy cập dễ dàng và bảo mật hơn.  

---

## **1️⃣ Tạo IAM Group bằng AWS Console (Giao diện Web)**  

### 🔹 **Bước 1: Truy cập AWS IAM Console**  
- Đăng nhập AWS Console tại 👉 [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)  
- Ở menu bên trái, chọn **User groups** → Nhấn **Create group**  

### 🔹 **Bước 2: Nhập tên nhóm**  
- **Group name**: Nhập tên nhóm (ví dụ: `Developers`)  
- Nhấn **Next**  

### 🔹 **Bước 3: Gán quyền cho Group**  
Bạn có thể **gán policy** (chính sách bảo mật) để cấp quyền truy cập cho nhóm.  
📌 **Ví dụ cấp quyền cho nhóm `Developers`:**  
- **AmazonS3FullAccess** → Quyền quản lý toàn bộ S3  
- **AmazonEC2ReadOnlyAccess** → Quyền đọc thông tin EC2  

🔹 **Tìm kiếm và chọn policies phù hợp** → Nhấn **Next**  

### 🔹 **Bước 4: Xác nhận & tạo nhóm**  
- Kiểm tra lại thông tin → Nhấn **Create group**  

✅ **Nhóm IAM Group đã được tạo thành công!** 🎉  

---

## **2️⃣ Thêm User vào IAM Group**  
### 🔹 **Bước 1: Vào IAM Console**  
- Vào **User groups** → Chọn nhóm vừa tạo (ví dụ: `Developers`)  
- Chọn **Add users**  

### 🔹 **Bước 2: Chọn User cần thêm**  
- Tick vào các User muốn thêm vào nhóm  
- Nhấn **Add users**  

✅ **User đã được thêm vào IAM Group và có quyền của nhóm!** 🚀  

---

## **3️⃣ Tạo IAM Group bằng AWS CLI** (Dòng lệnh)  

### 🔹 **Bước 1: Tạo Group**  
📌 Lệnh tạo nhóm **Developers**  
```bash
aws iam create-group --group-name Developers
```
📌 Kết quả mong đợi:  
```json
{
    "Group": {
        "Path": "/",
        "GroupName": "Developers",
        "GroupId": "AIDGROUPEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:group/Developers",
        "CreateDate": "2025-02-11T12:00:00Z"
    }
}
```

---

### 🔹 **Bước 2: Gán quyền cho Group**  
📌 Gán quyền quản lý S3 cho nhóm `Developers`  
```bash
aws iam attach-group-policy --group-name Developers \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

📌 Gán quyền đọc EC2 cho nhóm `Developers`  
```bash
aws iam attach-group-policy --group-name Developers \
    --policy-arn arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess
```

📌 **Kiểm tra danh sách policies đã gán cho Group**  
```bash
aws iam list-attached-group-policies --group-name Developers
```
📌 Kết quả mong đợi:  
```json
{
    "AttachedPolicies": [
        {
            "PolicyName": "AmazonS3FullAccess",
            "PolicyArn": "arn:aws:iam::aws:policy/AmazonS3FullAccess"
        },
        {
            "PolicyName": "AmazonEC2ReadOnlyAccess",
            "PolicyArn": "arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess"
        }
    ]
}
```

---

### 🔹 **Bước 3: Thêm User vào Group**  
📌 Thêm User `developer_user` vào nhóm `Developers`  
```bash
aws iam add-user-to-group --user-name developer_user --group-name Developers
```

📌 **Kiểm tra danh sách User trong nhóm**  
```bash
aws iam get-group --group-name Developers
```
📌 Kết quả mong đợi:  
```json
{
    "Group": {
        "Path": "/",
        "GroupName": "Developers",
        "GroupId": "AIDGROUPEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:group/Developers",
        "CreateDate": "2025-02-11T12:00:00Z"
    },
    "Users": [
        {
            "Path": "/",
            "UserName": "developer_user",
            "UserId": "AIDEXAMPLEUSER",
            "Arn": "arn:aws:iam::123456789012:user/developer_user",
            "CreateDate": "2025-02-11T12:05:00Z"
        }
    ]
}
```

✅ **User đã được thêm vào IAM Group!** 🎉  

---

## **4️⃣ Xóa IAM Group (nếu cần)**  

### 🔹 **Bước 1: Xóa User khỏi Group**  
📌 Xóa User `developer_user` khỏi nhóm `Developers`:  
```bash
aws iam remove-user-from-group --user-name developer_user --group-name Developers
```

### 🔹 **Bước 2: Xóa Policies khỏi Group**  
📌 Xóa quyền `AmazonS3FullAccess`:  
```bash
aws iam detach-group-policy --group-name Developers \
    --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

📌 Xóa quyền `AmazonEC2ReadOnlyAccess`:  
```bash
aws iam detach-group-policy --group-name Developers \
    --policy-arn arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess
```

### 🔹 **Bước 3: Xóa Group**  
📌 Xóa nhóm `Developers`:  
```bash
aws iam delete-group --group-name Developers
```

✅ **Nhóm IAM Group đã bị xóa thành công!** 🚀  

---

## **5️⃣ Tổng kết**  
✔ **IAM Groups giúp quản lý quyền tập trung** cho nhiều Users  
✔ **Tạo Group bằng AWS Console hoặc AWS CLI**  
✔ **Gán quyền bằng Policies**  
✔ **Thêm hoặc xóa Users khỏi Group**  
✔ **Xóa Group khi không còn sử dụng**  
