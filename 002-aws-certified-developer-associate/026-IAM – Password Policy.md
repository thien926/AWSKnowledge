### **Tiêu đề: IAM – Password Policy**
**Chính sách Mật khẩu IAM**

---

### **1. Strong passwords = higher security for your account**
- **Dịch:** Mật khẩu mạnh = bảo mật cao hơn cho tài khoản của bạn
- **Giải thích:** Sử dụng mật khẩu phức tạp, khó đoán sẽ giúp bảo vệ tài khoản khỏi bị truy cập trái phép.

---

### **2. In AWS, you can setup a password policy:**
- **Dịch:** Trong AWS, bạn có thể thiết lập một chính sách mật khẩu:
- **Giải thích:** AWS cho phép bạn tạo các quy định về mật khẩu nhằm tăng tính bảo mật cho hệ thống.

---

#### **- Set a minimum password length**
- **Dịch:** Đặt độ dài tối thiểu cho mật khẩu
- **Giải thích:** Bắt buộc người dùng phải tạo mật khẩu có độ dài tối thiểu, ví dụ: ít nhất 8 ký tự.

---

#### **- Require specific character types:**
  - **including uppercase letters**
    - **Dịch:** Bao gồm ký tự viết hoa (A-Z)
    - **Giải thích:** Yêu cầu mật khẩu phải chứa ít nhất một chữ cái viết hoa.
  - **lowercase letters**
    - **Dịch:** Chữ cái viết thường (a-z)
    - **Giải thích:** Mật khẩu cần có ít nhất một chữ cái thường.
  - **numbers**
    - **Dịch:** Số (0-9)
    - **Giải thích:** Mật khẩu cần chứa ít nhất một chữ số.
  - **non-alphanumeric characters**
    - **Dịch:** Ký tự đặc biệt (không phải chữ cái hay số, ví dụ: !, @, #, $)
    - **Giải thích:** Tăng độ mạnh của mật khẩu bằng cách yêu cầu có ít nhất một ký tự đặc biệt.

---

#### **- Allow all IAM users to change their own passwords**
- **Dịch:** Cho phép tất cả người dùng IAM thay đổi mật khẩu của riêng họ
- **Giải thích:** Người dùng có thể tự đặt lại mật khẩu khi cần thiết, giúp bảo vệ tài khoản khi nghi ngờ bị lộ mật khẩu.

---

#### **- Require users to change their password after some time (password expiration)**
- **Dịch:** Yêu cầu người dùng đổi mật khẩu sau một khoảng thời gian (hết hạn mật khẩu)
- **Giải thích:** Mỗi tài khoản phải thay đổi mật khẩu sau một thời gian nhất định (ví dụ: mỗi 90 ngày), giúp giảm nguy cơ bị lộ lâu dài.

---

#### **- Prevent password re-use**
- **Dịch:** Ngăn chặn việc dùng lại mật khẩu cũ
- **Giải thích:** Không cho phép người dùng lặp lại mật khẩu cũ khi đặt lại mật khẩu, giúp hạn chế các lỗ hổng bảo mật do thói quen sử dụng lại mật khẩu.

---

### **Tóm tắt:**
Chính sách mật khẩu của IAM trên AWS giúp tăng cường bảo mật bằng cách kiểm soát độ mạnh, tần suất đổi, thành phần và tính duy nhất của mật khẩu người dùng.