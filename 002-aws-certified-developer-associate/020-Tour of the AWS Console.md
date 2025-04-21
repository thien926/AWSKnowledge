
### 🧭 **Khám phá AWS Management Console (Tour of the AWS Console)**

#### 🌐 **AWS có các Dịch vụ Toàn Cầu (Global Services):**

| Dịch vụ | Mô tả ngắn |
|--------|-------------|
| **Identity and Access Management (IAM)** | Quản lý người dùng, nhóm và quyền truy cập tài nguyên AWS. |
| **Route 53** | Dịch vụ DNS (hệ thống phân giải tên miền) mạnh mẽ, hỗ trợ cân bằng tải và định tuyến theo vị trí địa lý. |
| **CloudFront** | Mạng phân phối nội dung (CDN) giúp phân phối nhanh các nội dung tĩnh và động đến người dùng toàn cầu. |
| **WAF (Web Application Firewall)** | Tường lửa ứng dụng web bảo vệ trước các cuộc tấn công phổ biến như SQL injection, XSS,… |

➡️ **Lưu ý:** Những dịch vụ này **hoạt động trên toàn cầu**, không bị giới hạn theo từng vùng (Region).

---

#### 📍 **Hầu hết các dịch vụ AWS là theo vùng (Region-scoped):**

| Dịch vụ | Mô hình | Mô tả |
|--------|---------|--------|
| **Amazon EC2** | IaaS (Infrastructure as a Service) | Cung cấp máy chủ ảo có thể cấu hình tùy ý. |
| **Elastic Beanstalk** | PaaS (Platform as a Service) | Triển khai ứng dụng tự động với môi trường được quản lý. |
| **Lambda** | FaaS (Function as a Service) | Chạy code không cần quản lý máy chủ, theo sự kiện. |
| **Rekognition** | SaaS (Software as a Service) | Dịch vụ phân tích hình ảnh và video, nhận diện khuôn mặt, đối tượng,… |

➡️ **Lưu ý:** Các dịch vụ này được **triển khai và quản lý theo từng Vùng địa lý (Region)**. Người dùng cần chọn Region phù hợp để sử dụng dịch vụ.

---

#### 🌍 **Tra cứu bảng dịch vụ theo vùng:**

🔗 [Region Table – Danh sách dịch vụ theo vùng AWS](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services)