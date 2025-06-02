# Tóm tắt phần IAM

- **Users**: ánh xạ tới người dùng thật, có mật khẩu để đăng nhập AWS Management Console  
- **Groups**: chỉ chứa các user, giúp gán quyền tập thể  
- **Policies**: tài liệu JSON mô tả các quyền (permission) cho user hoặc group  
- **Roles**: dùng cho EC2 instances hoặc các dịch vụ AWS, cho phép cấp quyền tạm thời  
- **Security**: bao gồm MFA và chính sách mật khẩu (Password Policy) để tăng cường bảo mật  
- **AWS CLI**: quản lý dịch vụ AWS thông qua dòng lệnh  
- **AWS SDK**: quản lý dịch vụ AWS thông qua ngôn ngữ lập trình  
- **Access Keys**: dùng để xác thực khi truy cập AWS qua CLI hoặc SDK  
- **Audit**: sử dụng IAM Credential Reports và IAM Access Advisor để rà soát và tối ưu quyền truy cập