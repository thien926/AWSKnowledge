

## 🛡️ IAM: Phân quyền (Permissions)

### 1. **Users or Groups can be assigned JSON documents called policies**  
🔸 **Dịch:** Người dùng (Users) hoặc Nhóm (Groups) có thể được gán các **tài liệu định dạng JSON** gọi là **chính sách (policies)**.  
🔍 **Giải thích:**  
- Trong AWS, quyền truy cập được quy định bằng **Policy**, là một **tệp JSON** mô tả những gì user/group **được phép hoặc không được phép** làm.  
- Bạn có thể gán policy **trực tiếp cho user** hoặc thông qua **group**.

🧩 **Ví dụ policy đơn giản (JSON):**
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
✅ Cho phép liệt kê nội dung của bucket `my-bucket`.

---

### 2. **These policies define the permissions of the users**  
🔸 **Dịch:** Các chính sách này sẽ **xác định quyền truy cập** của người dùng.  
🔍 **Giải thích:**  
- Mỗi policy sẽ quy định:  
  - **Thao tác nào được phép?** (`Action`)  
  - **Tài nguyên nào?** (`Resource`)  
  - **Cho phép hay từ chối?** (`Effect`)  
- Dựa vào đó, IAM sẽ **kiểm soát chính xác những gì user có thể làm**, ví dụ: đọc file S3, truy cập EC2, hay cấu hình VPC.

---

### 3. **In AWS you apply the least privilege principle: don’t give more permissions than a user needs**  
🔸 **Dịch:** Trong AWS, bạn nên áp dụng nguyên tắc **“ít quyền nhất có thể”** – **chỉ cấp đúng quyền mà người dùng cần, không hơn**.  
🔍 **Giải thích:**  
- Đây là một **nguyên tắc bảo mật rất quan trọng**:  
  - Tránh cấp quyền "admin" cho tất cả.  
  - Càng nhiều quyền => rủi ro bị khai thác càng cao.  
- Bạn nên tạo các policy **tùy chỉnh, chi tiết, và giới hạn** theo vai trò thực tế của từng người.

📌 **Ví dụ:**
- Developer chỉ cần quyền `lambda:InvokeFunction`, không cần `lambda:DeleteFunction`.
- Auditor chỉ cần quyền `read-only`, không cần `write`.

---

## 📎 Tóm lại:
| Thành phần | Ý nghĩa |
|------------|--------|
| **Policy (JSON)** | Định nghĩa quyền của user/group |
| **User / Group** | Đối tượng được gán quyền |
| **Least Privilege** | Nguyên tắc bảo mật: chỉ cấp quyền cần thiết |

👉 Việc hiểu rõ và áp dụng đúng policy sẽ giúp bạn **bảo vệ hệ thống AWS khỏi các truy cập trái phép** và dễ dàng kiểm soát hoạt động nội bộ hơn.

Cần mình ví dụ thêm về các loại policy hay cách debug khi bị từ chối truy cập (`AccessDenied`)? Mình hỗ trợ được luôn nhé!