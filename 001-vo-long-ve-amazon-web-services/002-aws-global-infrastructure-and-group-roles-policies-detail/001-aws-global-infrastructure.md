**AWS Global Infrastructure** là hệ thống hạ tầng toàn cầu của Amazon Web Services (AWS), được thiết kế để cung cấp dịch vụ đám mây có độ sẵn sàng cao, hiệu suất tốt và bảo mật cao trên toàn thế giới. AWS Global Infrastructure bao gồm các thành phần chính sau:  

### **1. AWS Regions (Khu vực AWS)**
- **Region** là một khu vực địa lý độc lập, nơi AWS đặt các trung tâm dữ liệu của mình.
- Mỗi Region có ít nhất hai hoặc nhiều **Availability Zones** (AZs).
- Các Region được đặt tại nhiều nơi trên thế giới, giúp người dùng chọn nơi gần nhất với khách hàng của họ để giảm độ trễ.
- Một số Region phổ biến: `us-east-1` (Bắc Virginia), `eu-west-1` (Ireland), `ap-southeast-1` (Singapore).

### **2. Availability Zones (AZs - Vùng sẵn sàng)**
- Mỗi Region có nhiều AZs, mỗi AZ là một trung tâm dữ liệu riêng biệt nhưng được kết nối với nhau bằng mạng tốc độ cao.
- Mỗi AZ có nguồn điện, hệ thống làm mát, và bảo mật riêng để đảm bảo tính sẵn sàng cao.
- Khi triển khai ứng dụng trên AWS, bạn có thể đặt tài nguyên trong nhiều AZ để tăng khả năng chịu lỗi.

### **3. Edge Locations (Điểm biên)**
- Là các trung tâm dữ liệu được tối ưu hóa để phân phối nội dung nhanh hơn, chủ yếu phục vụ cho Amazon CloudFront (CDN) và AWS Global Accelerator.
- Edge Locations giúp cải thiện tốc độ tải dữ liệu và giảm độ trễ cho người dùng cuối.

### **4. Local Zones**
- Là các trung tâm dữ liệu gần với người dùng cuối hơn, giúp giảm độ trễ cho các ứng dụng yêu cầu xử lý thời gian thực như gaming, AR/VR.

### **5. AWS Wavelength**
- Được thiết kế để tích hợp với mạng 5G, cho phép các ứng dụng có độ trễ cực thấp hoạt động ngay tại các mạng viễn thông.

### **6. AWS Outposts**
- Một dịch vụ giúp bạn chạy AWS trên phần cứng tại chỗ (on-premises), phù hợp cho các doanh nghiệp cần tuân thủ quy định về dữ liệu.

### **Lợi ích của AWS Global Infrastructure**
✅ Độ sẵn sàng cao, hỗ trợ failover giữa các AZ và Region.  
✅ Giảm độ trễ với hệ thống phân phối rộng khắp.  
✅ Bảo mật cao với nhiều lớp bảo vệ vật lý và mạng.  
✅ Khả năng mở rộng linh hoạt tùy theo nhu cầu sử dụng.  

Bạn đang quan tâm đến dịch vụ cụ thể nào trong AWS Global Infrastructure không? 🚀