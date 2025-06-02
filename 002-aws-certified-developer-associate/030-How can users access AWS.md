# Làm thế nào người dùng có thể truy cập AWS?

1. **Có ba cách để truy cập AWS:**
   - **AWS Management Console**  
     - Dịch: Bảng điều khiển quản lý AWS (bảo vệ bằng mật khẩu + MFA)  
     - Giải thích: Giao diện web trực quan, người dùng đăng nhập bằng tài khoản IAM/Root, nhập mật khẩu và mã MFA nếu được yêu cầu.  
   - **AWS Command Line Interface (CLI)**  
     - Dịch: Giao diện dòng lệnh AWS (bảo vệ bằng Access Keys)  
     - Giải thích: Công cụ dòng lệnh cho phép thực thi lệnh AWS, xác thực qua Access Key ID và Secret Access Key.  
   - **AWS Software Development Kit (SDK)**  
     - Dịch: Bộ SDK phát triển cho AWS (dùng trong code, bảo vệ bằng Access Keys)  
     - Giải thích: Thư viện lập trình hỗ trợ nhiều ngôn ngữ, cho phép gọi API AWS kèm Access Keys để xác thực.

2. **Access Keys được tạo ra thông qua AWS Console**  
   - Dịch: Access Keys được sinh ra qua Bảng điều khiển AWS  
   - Giải thích: Quản trị viên hoặc người dùng IAM tự phát sinh cặp Access Key ID + Secret Access Key từ trang IAM trong Console.

3. **Users manage their own access keys**  
   - Dịch: Người dùng tự quản lý Access Keys của họ  
   - Giải thích: Mỗi người dùng chịu trách nhiệm lưu trữ, xoá hoặc tái tạo Access Key khi cần thiết.

4. **Access Keys are secret, just like a password. Don’t share them**  
   - Dịch: Access Keys là bí mật, giống như mật khẩu. Đừng chia sẻ chúng.  
   - Giải thích: Nếu lộ Access Key, kẻ tấn công có thể dùng chúng để truy cập và thao tác tài nguyên AWS thay bạn.

5. **Access Key ID ~= username**  
   - Dịch: Access Key ID ~ giống tên người dùng  
   - Giải thích: Access Key ID có dạng chuỗi công khai, dùng để nhận diện “ai” đang gọi API.

6. **Secret Access Key ~= password**  
   - Dịch: Secret Access Key ~ giống mật khẩu  
   - Giải thích: Secret Access Key là phần bí mật dùng để ký yêu cầu, bắt buộc bảo mật tương tự mật khẩu.

---

**Tóm tắt:**  
- Giao diện Console phù hợp khi cần thao tác thủ công, có MFA bảo vệ.  
- CLI/SDK tiện tự động hoá, chạy script, dùng Access Keys để xác thực.  
- Tuyệt đối giữ kín Access Keys, chỉ cấp phát cho cá nhân, và xoá ngay khi không sử dụng.