### AWS Availability Zones (Vùng khả dụng của AWS)

- **Mỗi khu vực (Region) có nhiều Availability Zones**  
  Mỗi khu vực AWS thường bao gồm từ 3 đến tối đa 6 Availability Zones (AZ). Ví dụ:  
  - **ap-southeast-2a**  
  - **ap-southeast-2b**  
  - **ap-southeast-2c**

- **Mỗi Availability Zone (AZ) là một hoặc nhiều trung tâm dữ liệu riêng biệt**  
  Các trung tâm dữ liệu này được thiết kế với nguồn điện, mạng lưới và kết nối dự phòng, đảm bảo tính ổn định và sẵn sàng cao.

- **Mỗi Availability Zone tách biệt hoàn toàn**  
  Các Availability Zones này được tách biệt khỏi nhau, giúp chúng có thể hoạt động độc lập trong trường hợp xảy ra thiên tai hoặc sự cố nghiêm trọng.

- **Kết nối giữa các Availability Zones với băng thông cao và độ trễ cực thấp**  
  Mạng lưới giữa các Availability Zones được thiết kế với băng thông cao và độ trễ cực thấp, đảm bảo kết nối nhanh chóng và ổn định giữa các AZ.

---

### Giải thích chi tiết:

- **Availability Zones** là những khu vực vật lý độc lập trong một **AWS Region**. Mỗi Availability Zone có ít nhất một trung tâm dữ liệu và có thể chứa nhiều trung tâm dữ liệu hơn.
  
- Các **Availability Zones** này giúp phân tán dữ liệu và ứng dụng, tối ưu hóa khả năng chịu lỗi và tăng tính khả dụng của các dịch vụ trên AWS.

- Mỗi AZ hoạt động độc lập với các AZ khác nhưng được kết nối với nhau qua các kênh mạng lưới tốc độ cao để giảm thiểu độ trễ và đảm bảo hiệu suất khi các dịch vụ được phân bổ giữa các AZ.