# IAM Security Tools  
**Các công cụ bảo mật IAM**

1. **IAM Credentials Report (cấp độ tài khoản)**
   - *Dịch:* Báo cáo thông tin chứng thực IAM  
   - *Mô tả:* Một báo cáo liệt kê tất cả người dùng trong tài khoản AWS của bạn và trạng thái của các chứng thực khác nhau của họ, ví dụ:
     - Mật khẩu: thời điểm cuối cùng sử dụng
     - Access Keys: đang hoạt động hay không
     - MFA: đã kích hoạt hay chưa  
   - *Công dụng:*  
     - Giúp quản trị viên rà soát, theo dõi và xoá hoặc thay thế các chứng thực cũ/không an toàn.  
     - Đảm bảo tuân thủ chính sách bảo mật (ví dụ: xoá key không dùng > 90 ngày).

2. **IAM Access Advisor (cấp độ người dùng)**
   - *Dịch:* Công cụ Tư vấn Truy cập IAM  
   - *Mô tả:*  
     - Hiển thị các quyền (permission) mà bạn đã cấp cho một user hoặc role.  
     - Cho biết thời điểm cuối cùng user/role sử dụng từng dịch vụ AWS.  
   - *Công dụng:*  
     - Xác định các quyền không còn cần thiết (unused permissions).  
     - Tối ưu chính sách theo nguyên tắc **Least Privilege** (ít quyền nhất).  
     - Cập nhật hoặc thu hồi policy cho phù hợp, giảm bề mặt tấn công.

---

> **Tóm tắt:**  
> - *IAM Credentials Report* hỗ trợ xem tổng quan chứng thực ở mức tài khoản.  
> - *IAM Access Advisor* tập trung vào cách người dùng/role đã sử dụng quyền.  
> - Kết hợp hai công cụ giúp duy trì môi trường AWS an toàn, tuân thủ best practices.