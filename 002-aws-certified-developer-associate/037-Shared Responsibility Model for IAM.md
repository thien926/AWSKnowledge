# Mô hình Chia sẻ Trách nhiệm cho IAM

## 1. AWS chịu trách nhiệm về:
- **Infrastructure (global network security)**  
  *Cơ sở hạ tầng (bảo mật mạng toàn cầu)*  
  AWS đảm bảo datacenter, mạng lưới toàn cầu, phần cứng, và nền tảng hạ tầng được bảo vệ, giám sát liên tục.  
- **Configuration and vulnerability analysis**  
  *Cấu hình và phân tích lỗ hổng*  
  AWS thực hiện kiểm tra bảo mật, quét lỗ hổng và cập nhật bản vá cho hệ thống quản lý tài nguyên IAM.  
- **Compliance validation**  
  *Xác nhận tuân thủ*  
  AWS chịu trách nhiệm đảm bảo hạ tầng đáp ứng các tiêu chuẩn, quy định (ISO, SOC, GDPR, v.v.).

---

## 2. Bạn (You) chịu trách nhiệm về:
- **Users, Groups, Roles, Policies management and monitoring**  
  *Quản lý và giám sát Users, Groups, Roles, Policies*  
  Tạo, cập nhật, gán quyền cho user/group/role, theo dõi hoạt động đăng nhập và sử dụng quyền.  
- **Enable MFA on all accounts**  
  *Kích hoạt MFA cho tất cả tài khoản*  
  Áp dụng xác thực đa yếu tố để tăng cường bảo mật cho mọi user và tài khoản Root.  
- **Rotate all your keys often**  
  *Thường xuyên xoay vòng mọi Access Keys*  
  Thay mới Access Key ID & Secret Access Key định kỳ để giảm thiểu rủi ro nếu key bị lộ.  
- **Use IAM tools to apply appropriate permissions**  
  *Sử dụng công cụ IAM để áp dụng quyền thích hợp*  
  Dùng IAM Policies, Access Advisor, Credentials Report để gán quyền theo nguyên tắc Least Privilege.  
- **Analyze access patterns & review permissions**  
  *Phân tích mẫu truy cập & rà soát quyền*  
  Kiểm tra xem user/role sử dụng dịch vụ nào, khi nào; từ đó điều chỉnh, thu hồi quyền không cần thiết.  

---

> **Tổng kết:**  
> - AWS đảm bảo an toàn hạ tầng và tuân thủ tiêu chuẩn.  
> - Bạn chịu trách nhiệm quản lý người dùng, quyền truy cập, thiết lập và duy trì bảo mật IAM.  
> Mô hình này giúp phân chia rõ ràng ai làm gì, đảm bảo an toàn tổng thể cho môi trường AWS.