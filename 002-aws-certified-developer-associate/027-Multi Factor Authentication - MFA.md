### **Tiêu đề: Multi Factor Authentication – MFA**
**Xác thực đa yếu tố – MFA**

---

### **1. Users have access to your account and can possibly change configurations or delete resources in your AWS account**
- **Dịch:** Người dùng có thể truy cập vào tài khoản của bạn và có khả năng thay đổi cấu hình hoặc xóa tài nguyên trong tài khoản AWS của bạn.
- **Giải thích:** Nếu ai đó truy cập được vào tài khoản thì có thể gây thiệt hại lớn như thay đổi hệ thống, xóa dữ liệu, gây mất an toàn.

---

### **2. You want to protect your Root Accounts and IAM users**
- **Dịch:** Bạn muốn bảo vệ tài khoản Root và người dùng IAM của mình.
- **Giải thích:** Tài khoản Root và người dùng IAM là những tài khoản quản trị quan trọng, cần bảo vệ tối đa để tránh bị xâm nhập.

---

### **3. MFA = password you know + security device you own**
- **Dịch:** MFA = mật khẩu bạn biết + thiết bị bảo mật bạn sở hữu.
- **Giải thích:**  
  - Yếu tố 1: *Một thông tin chỉ bạn biết* (ví dụ: mật khẩu).
  - Yếu tố 2: *Một thiết bị bạn sở hữu* (ví dụ: điện thoại hoặc token sinh mã OTP).
  - Khi kết hợp cả hai, sẽ tăng độ an toàn cho việc đăng nhập.

---

### **4. Minh họa quy trình:**
```
Alice (người dùng)
      |
      +----> Nhập Password 
      +----> Nhập mã MFA (từ thiết bị bảo mật)
      |
   => Đăng nhập thành công
```
- **Dịch:** Muốn đăng nhập, cần vừa mật khẩu vừa mã xác thực từ thiết bị bảo mật (như điện thoại hoặc key token).

---

### **5. Main benefit of MFA: if a password is stolen or hacked, the account is not compromised**
- **Dịch:** Lợi ích chính của MFA: nếu mật khẩu bị đánh cắp hoặc hack thì tài khoản vẫn không bị xâm phạm.
- **Giải thích:** Dù hacker biết mật khẩu, họ vẫn không đăng nhập được nếu không có thiết bị bảo mật (mã OTP/MFA của bạn).

---

### **Tóm tắt:**
**MFA bảo vệ tài khoản của bạn bằng cách yêu cầu nhiều yếu tố xác thực, giúp giảm thiểu rủi ro bị tấn công khi mật khẩu bị lộ.**