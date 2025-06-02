### Tổng quan
**IAM Policies** (Chính sách IAM) là những tài liệu quy định những quyền gì được cấp cho ai, trên tài nguyên nào trong hệ thống AWS.

---

### Cấu trúc chính

#### 1. **Version**
- *Dịch*: Phiên bản ngôn ngữ chính sách, luôn luôn là "2012-10-17"
- *Giải thích*: Giúp AWS hiểu đúng cú pháp của policy bạn đang dùng. Giá trị này cố định, hầu hết các policy hiện nay đều phải có phần này.

---

#### 2. **Id**
- *Dịch*: Một định danh cho chính sách (không bắt buộc)
- *Giải thích*: Dùng để gán mã ID riêng cho policy, giúp quản lý hoặc tra cứu thuận tiện hơn. Có thể bỏ qua phần này.

---

#### 3. **Statement**
- *Dịch*: Một hoặc nhiều mô tả quyền cụ thể (bắt buộc)
- *Giải thích*: Đây là "trái tim" của policy, là một hoặc nhiều đoạn mô tả về những quyền gì được cấp và cho ai.

---

### Trong từng Statement gồm các thành phần:

#### 3.1. **Sid**
- *Dịch*: Định danh cho từng câu lệnh (không bắt buộc)
- *Giải thích*: Giúp phân biệt hoặc chú thích từng statement nếu có nhiều statement trong một policy.

---

#### 3.2. **Effect**
- *Dịch*: Quyết định câu lệnh này cho phép (Allow) hay từ chối (Deny) quyền truy cập
- *Giải thích*:  
  - `Allow`: Cho phép thực hiện hành động.  
  - `Deny`: Từ chối quyền truy cập, luôn được ưu tiên cao nhất trong AWS.

---

#### 3.3. **Principal**
- *Dịch*: Đối tượng tài khoản/người dùng/role mà policy này áp dụng (chủ yếu dùng trong resource-based policy)
- *Giải thích*: Chỉ định ai sẽ nhận quy định này, như một user, role hoặc tài khoản AWS khác.

---

#### 3.4. **Action**
- *Dịch*: Danh sách hành động mà chính sách cho phép hoặc từ chối
- *Giải thích*: Các thao tác như `s3:GetObject`, `ec2:StartInstances`,… chính sách quy định được phép với các action nào.

---

#### 3.5. **Resource**
- *Dịch*: Danh sách tài nguyên mà các hành động trên được áp dụng
- *Giải thích*: Quy định phạm vi tác động của policy lên những tài nguyên cụ thể nào (ví dụ như ARN của một bucket S3).

---

#### 3.6. **Condition**
- *Dịch*: Các điều kiện bổ sung để xác định khi nào policy có hiệu lực (không bắt buộc)
- *Giải thích*: Dùng để thêm ràng buộc, ví dụ như chỉ cho phép hành động nếu truy cập từ một địa chỉ IP nhất định hoặc một khoảng thời gian nhất định.

---

## Tóm tắt cấu trúc mẫu

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowListBucket",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::example-bucket",
      "Condition": {
        "IpAddress": {"aws:SourceIp": "192.0.2.0/24"}
      }
    }
  ]
}
```

---

> **Tóm lại:**  
> Một policy IAM được cấu thành từ các phần: `Version` (phiên bản), `Id` (ID, tùy chọn), `Statement` (danh sách câu lệnh quyền), mỗi `Statement` lại có thể có các thành phần như `Sid`, `Effect`, `Principal`, `Action`, `Resource`, `Condition`.  
> Phần quan trọng nhất là các `Statement` quyết định quyền gì được cấp cho ai, trên tài nguyên nào, với điều kiện gì.
