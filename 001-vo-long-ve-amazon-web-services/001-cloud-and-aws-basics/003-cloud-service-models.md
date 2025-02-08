# **Các Mô Hình Dịch Vụ Cloud Computing & AWS Cloud Service Models** ☁️💻  

Cloud Computing cung cấp nhiều mô hình dịch vụ giúp doanh nghiệp và cá nhân dễ dàng triển khai hệ thống mà không cần đầu tư hạ tầng vật lý. AWS (Amazon Web Services) là một trong những nhà cung cấp Cloud hàng đầu, hỗ trợ đầy đủ các mô hình dịch vụ sau:  

---

## **1️⃣ IaaS (Infrastructure as a Service) - Cơ sở hạ tầng dưới dạng dịch vụ** 🏗️  

### **🔹 Định nghĩa:**  
- IaaS cung cấp **máy chủ ảo, lưu trữ, mạng và bảo mật** dưới dạng dịch vụ, giúp người dùng có thể thuê tài nguyên theo nhu cầu thay vì phải mua và bảo trì phần cứng.  
- Người dùng có toàn quyền kiểm soát hệ thống và tự chịu trách nhiệm quản lý hạ tầng.  

### **🔹 Đặc điểm:**  
✅ Cung cấp **máy chủ ảo (VM), lưu trữ, mạng, firewall, cân bằng tải**.  
✅ Người dùng tự quản lý **hệ điều hành, ứng dụng và dữ liệu**.  
✅ Trả phí theo mức sử dụng (**Pay-as-you-go**).  

### **🔹 Ưu điểm:**  
✅ **Tiết kiệm chi phí đầu tư phần cứng** vì không cần mua máy chủ vật lý.  
✅ **Dễ dàng mở rộng (scale up/down)** khi nhu cầu thay đổi.  
✅ **Toàn quyền kiểm soát hệ thống**, có thể cài đặt và tùy chỉnh theo ý muốn.  

### **🔹 Nhược điểm:**  
❌ Người dùng phải **tự quản lý và bảo trì hệ thống**, đòi hỏi kỹ năng IT.  
❌ **Bảo mật phụ thuộc vào người dùng**, cần tự cài đặt firewall, cập nhật bảo mật.  

### **🔹 Dịch vụ IaaS phổ biến trên AWS:**  
| **Dịch vụ** | **Chức năng** |
|------------|-------------|
| **Amazon EC2** | Cung cấp máy chủ ảo (Virtual Machines) theo nhu cầu. |
| **Amazon S3** | Lưu trữ đối tượng (Object Storage) với độ bền cao. |
| **Amazon EBS** | Lưu trữ block dùng cho EC2. |
| **Amazon VPC** | Tạo mạng ảo riêng (Virtual Private Cloud) để bảo mật hệ thống. |
| **AWS Direct Connect** | Kết nối mạng On-Prem với AWS. |
| **Elastic Load Balancing (ELB)** | Cân bằng tải giữa các máy chủ. |
| **AWS IAM** | Quản lý quyền truy cập và bảo mật hệ thống. |

### **🔹 Ví dụ thực tế:**  
Một startup cần xây dựng website có thể sử dụng:  
- **EC2** để chạy backend.  
- **S3** để lưu trữ dữ liệu.  
- **RDS** để quản lý database.  
- **VPC** để thiết lập mạng riêng và bảo mật hệ thống.  

---

## **2️⃣ PaaS (Platform as a Service) - Nền tảng dưới dạng dịch vụ** 🎛️  

### **🔹 Định nghĩa:**  
- PaaS cung cấp **môi trường phát triển và triển khai ứng dụng** mà không cần lo về hạ tầng.  
- AWS quản lý máy chủ, hệ điều hành, runtime, cập nhật bảo mật, giúp lập trình viên tập trung vào code.  

### **🔹 Đặc điểm:**  
✅ Cung cấp **runtime, framework, hệ điều hành** sẵn sàng sử dụng.  
✅ Hỗ trợ **CI/CD, DevOps**, triển khai ứng dụng nhanh chóng.  
✅ **Không cần quản lý máy chủ, cập nhật OS** – AWS lo hết.  

### **🔹 Ưu điểm:**  
✅ **Tiết kiệm thời gian phát triển**, không phải lo về hạ tầng.  
✅ **Dễ dàng triển khai ứng dụng**, hỗ trợ nhiều ngôn ngữ lập trình.  
✅ **Tích hợp CI/CD**, giúp DevOps hoạt động hiệu quả.  

### **🔹 Nhược điểm:**  
❌ **Ít linh hoạt** hơn IaaS vì không có quyền kiểm soát hệ điều hành.  
❌ **Phụ thuộc vào nhà cung cấp**, khó di chuyển ứng dụng sang nền tảng khác.  

### **🔹 Dịch vụ PaaS phổ biến trên AWS:**  
| **Dịch vụ** | **Chức năng** |
|------------|-------------|
| **AWS Elastic Beanstalk** | Triển khai và quản lý ứng dụng web mà không cần lo về hạ tầng. |
| **AWS Lambda** | Chạy code **Serverless** mà không cần quản lý máy chủ. |
| **Amazon RDS** | Cơ sở dữ liệu quan hệ (MySQL, PostgreSQL, SQL Server, etc.). |
| **AWS Fargate** | Chạy container mà không cần quản lý server. |
| **AWS API Gateway** | Quản lý API, kết nối với Lambda hoặc EC2. |
| **AWS Step Functions** | Xây dựng workflow tự động hóa các tiến trình. |

### **🔹 Ví dụ thực tế:**  
Một nhóm phát triển muốn triển khai nhanh ứng dụng web có thể sử dụng:  
- **Elastic Beanstalk** để host ứng dụng.  
- **Lambda** để chạy function backend.  
- **RDS** để lưu trữ dữ liệu.  

---

## **3️⃣ SaaS (Software as a Service) - Phần mềm dưới dạng dịch vụ** 📲  

### **🔹 Định nghĩa:**  
- SaaS cung cấp **phần mềm hoàn chỉnh chạy trên Cloud**, người dùng chỉ cần truy cập qua trình duyệt mà không cần cài đặt hay bảo trì.  
- Nhà cung cấp chịu trách nhiệm vận hành, cập nhật và bảo trì hệ thống.  

### **🔹 Đặc điểm:**  
✅ Người dùng **không cần quản lý hạ tầng, bảo trì phần mềm**.  
✅ Truy cập dễ dàng từ **bất kỳ đâu có Internet**.  
✅ Nhà cung cấp đảm bảo **bảo mật, cập nhật, sao lưu dữ liệu**.  

### **🔹 Ưu điểm:**  
✅ **Không cần cài đặt, bảo trì**, nhà cung cấp lo toàn bộ.  
✅ **Dễ sử dụng, truy cập nhanh**, hỗ trợ làm việc nhóm từ xa.  
✅ **Tính linh hoạt cao**, có thể dùng trên nhiều thiết bị.  

### **🔹 Nhược điểm:**  
❌ **Phụ thuộc vào nhà cung cấp**, nếu dịch vụ ngừng hoạt động, người dùng bị ảnh hưởng.  
❌ **Bảo mật dữ liệu cần xem xét**, do thông tin được lưu trên Cloud.  

### **🔹 Dịch vụ SaaS phổ biến trên AWS:**  
| **Dịch vụ** | **Chức năng** |
|------------|-------------|
| **Amazon WorkMail** | Dịch vụ email doanh nghiệp giống như Gmail. |
| **Amazon Chime** | Họp video trực tuyến (tương tự Zoom, Microsoft Teams). |
| **Amazon QuickSight** | Trực quan hóa dữ liệu, tạo báo cáo thông minh (BI). |
| **AWS Cognito** | Quản lý đăng nhập và xác thực người dùng. |
| **AWS Security Hub** | Dịch vụ bảo mật và quản lý tuân thủ. |

### **🔹 Ví dụ thực tế:**  
Một công ty có thể dùng:  
- **Amazon WorkMail** để quản lý email nội bộ.  
- **AWS Cognito** để xác thực người dùng.  

---

## **4️⃣ Hybrid Cloud trên AWS** 🌍🔗  
Hybrid Cloud kết hợp giữa **hệ thống On-Prem và Cloud**, giúp doanh nghiệp linh hoạt trong việc triển khai dịch vụ.  

### **🔹 Dịch vụ Hybrid Cloud của AWS:**  
| **Dịch vụ** | **Chức năng** |  
|------------|-------------|  
| **AWS Outposts** | Đưa phần cứng AWS về trung tâm dữ liệu doanh nghiệp. |  
| **AWS Direct Connect** | Kết nối mạng nội bộ với AWS. |  
| **AWS Storage Gateway** | Đồng bộ dữ liệu giữa On-Prem và AWS. |  

---

## **So sánh IaaS, PaaS, SaaS** 🆚  
| **Tiêu chí**  | **IaaS** | **PaaS** | **SaaS** |
|--------------|---------|---------|---------|
| **Quản lý hạ tầng** | Người dùng tự quản lý | Nhà cung cấp lo hạ tầng, người dùng lo ứng dụng | Hoàn toàn do nhà cung cấp quản lý |
| **Đối tượng sử dụng** | DevOps, quản trị viên hệ thống | Lập trình viên, nhà phát triển ứng dụng | Người dùng cuối |
| **Độ linh hoạt** | Cao (toàn quyền kiểm soát) | Trung bình (chỉ kiểm soát ứng dụng) | Thấp (chỉ sử dụng phần mềm có sẵn) |
| **Tính bảo trì** | Người dùng tự lo bảo trì hệ thống | Nhà cung cấp lo về hệ điều hành, runtime | Nhà cung cấp lo toàn bộ |
| **Ví dụ** | AWS EC2, Google Compute Engine | AWS Elastic Beanstalk, Google App Engine | Gmail, Dropbox, Zoom |