# Hướng dẫn & Best Practices cho IAM

1. **Không dùng tài khoản Root ngoại trừ khi thiết lập AWS account**  
   - *Giải thích:* Tài khoản Root có toàn quyền trên toàn bộ tài khoản AWS. Chỉ sử dụng cho bước khởi tạo, thanh toán, và khi thực sự cần thiết. Các tác vụ hàng ngày luôn dùng IAM user hoặc role.

2. **Một người dùng thực tế = Một user AWS**  
   - *Giải thích:* Mỗi cá nhân nên có một tài khoản IAM riêng để dễ quản lý, theo dõi hành vi và thu hồi quyền khi cần. Tránh dùng chung user.

3. **Gán người dùng vào nhóm và gán quyền cho nhóm**  
   - *Giải thích:* Thay vì cấp quyền trực tiếp cho từng user, tạo IAM Group (ví dụ: Dev, Ops, QA) rồi gán policy. Giúp quản lý tập trung và nhất quán.

4. **Tạo chính sách mật khẩu mạnh**  
   - *Giải thích:* Đặt độ dài tối thiểu, bắt buộc chữ hoa, chữ thường, số, ký tự đặc biệt. Ngăn chặn mật khẩu dễ đoán.

5. **Sử dụng và thực thi Multi-Factor Authentication (MFA)**  
   - *Giải thích:* Bảo vệ thêm một lớp xác thực, giảm rủi ro khi mật khẩu bị lộ.

6. **Tạo và sử dụng IAM Roles để cấp quyền cho dịch vụ AWS**  
   - *Giải thích:* Dùng Role thay vì Access Key cứng cho EC2, Lambda, CloudFormation... Giúp bảo mật và quản lý quyền thuận tiện hơn.

7. **Dùng Access Keys cho truy cập lập trình (CLI / SDK)**  
   - *Giải thích:* Khi cần tự động hóa, viết script hoặc code, sử dụng cặp Access Key ID + Secret Access Key. Bảo vệ chặt, lưu trữ an toàn.

8. **Kiểm tra và đánh giá quyền bằng IAM Credentials Report & IAM Access Advisor**  
   - *Giải thích:*  
     - *IAM Credentials Report* cho cái nhìn tổng quan về chứng thực (password, key, MFA) ở mức toàn tài khoản.  
     - *IAM Access Advisor* cho biết user/role đã sử dụng dịch vụ nào và khi nào, giúp loại bỏ quyền không cần thiết.

9. **Tuyệt đối không chia sẻ IAM Users & Access Keys**  
   - *Giải thích:* Việc chia sẻ làm mất tính đối ứng giữa người dùng và chứng thực, khó kiểm soát, dễ dẫn đến rò rỉ quyền truy cập.

---

> Tuân thủ các hướng dẫn trên giúp bạn duy trì môi trường AWS an toàn, dễ quản lý và tuân thủ nguyên tắc **Least Privilege**.