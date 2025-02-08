Trong AWS, có hai loại tài khoản người dùng chính là **Root User** và **IAM User**, mỗi loại có vai trò và quyền hạn khác nhau:

---

## 1. **Root User**  
### 🔹 Định nghĩa:  
Root User là tài khoản chủ sở hữu của tài khoản AWS, được tạo ra khi bạn đăng ký AWS lần đầu tiên bằng email chính.

### 🔹 Quyền hạn:  
- Có **toàn quyền truy cập** vào tất cả các dịch vụ và tài nguyên trong tài khoản AWS.
- Không thể bị giới hạn quyền bằng IAM policies.
- Có thể thực hiện các hành động nhạy cảm mà IAM User không thể làm, như:
  - Thay đổi thông tin thanh toán.
  - Đóng tài khoản AWS.
  - Khôi phục quyền truy cập tài khoản.
  - Quản lý **IAM User và quyền hạn IAM**.

### 🔹 Best Practices:  
⚠️ **Không nên sử dụng Root User hàng ngày** do mức độ rủi ro cao nếu bị lộ tài khoản.  
Thay vào đó, bạn nên:
1. **Bật MFA (Multi-Factor Authentication)** để tăng cường bảo mật.
2. **Tạo IAM User** với quyền hạn phù hợp để quản lý tài nguyên thay vì dùng Root User.
3. **Không chia sẻ thông tin đăng nhập Root User** với bất kỳ ai.

---

## 2. **IAM User**  
### 🔹 Định nghĩa:  
IAM (Identity and Access Management) User là tài khoản do Root User hoặc IAM Administrator tạo ra để cấp quyền truy cập AWS theo nguyên tắc **Least Privilege** (ít quyền nhất có thể).

### 🔹 Quyền hạn:  
- Mặc định, IAM User **không có quyền gì** khi mới tạo.
- Quyền của IAM User được kiểm soát bởi **IAM Policies** và **IAM Roles**.
- Có thể cấp quyền cụ thể như:
  - Chỉ truy cập **S3**, **EC2**, **DynamoDB**, v.v.
  - Chỉ có quyền **đọc dữ liệu** nhưng không thể xóa/sửa.
  - Chỉ có quyền quản lý **một số dịch vụ AWS**.

### 🔹 Best Practices:  
1. **Tạo IAM User cho từng cá nhân hoặc dịch vụ cụ thể** thay vì dùng Root User.
2. **Gán quyền tối thiểu cần thiết** bằng IAM Policies.
3. **Sử dụng IAM Groups** để quản lý quyền dễ dàng hơn.
4. **Bật MFA cho IAM User quan trọng**.
5. **Không dùng IAM User có quyền Administrator trừ khi cần thiết**.

---

## 🚀 **So sánh Root User và IAM User**  

| Tiêu chí          | Root User                     | IAM User |
|------------------|--------------------------------|----------------------------------|
| **Tạo khi nào?**  | Khi đăng ký tài khoản AWS     | Được Root User hoặc IAM Admin tạo ra |
| **Mặc định có quyền gì?** | Tất cả quyền trên AWS  | Không có quyền nào (phải cấp quyền) |
| **Có thể bị giới hạn quyền không?** | ❌ Không thể | ✅ Có thể qua IAM Policies |
| **Thực hiện hành động quan trọng?** | ✅ Được (VD: đóng tài khoản, quản lý billing) | ❌ Không được (trừ khi có quyền đặc biệt) |
| **Có nên dùng hàng ngày?** | ❌ Không (rủi ro cao) | ✅ Nên dùng IAM User phù hợp |

---

## 📌 **Khi nào dùng Root User?**  
🔹 Khi cần làm các tác vụ quản trị quan trọng, chẳng hạn như:
- Cấu hình thanh toán, hóa đơn.
- Bật IAM Access Analyzer, AWS Organizations.
- Thiết lập tài khoản AWS ban đầu.

📌 **Còn lại, hãy dùng IAM User với quyền hạn phù hợp để đảm bảo bảo mật và tránh rủi ro!**