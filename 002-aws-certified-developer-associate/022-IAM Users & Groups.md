

## 🔐 IAM: Người dùng và Nhóm (Users & Groups)

### 1. **IAM = Identity and Access Management, Global service**  
🔸 **Dịch:** IAM là viết tắt của “Quản lý danh tính và quyền truy cập”, là một dịch vụ toàn cục (global).  
🔍 **Giải thích:** IAM giúp bạn **quản lý người dùng** và **các quyền truy cập** đến tài nguyên AWS. Là dịch vụ toàn cục, IAM **không phụ thuộc vào vùng (region)** nào – bạn cấu hình ở đâu thì áp dụng toàn hệ thống AWS.

---

### 2. **Root account created by default, shouldn’t be used or shared**  
🔸 **Dịch:** Tài khoản root được tạo mặc định, **không nên sử dụng thường xuyên hoặc chia sẻ với người khác**.  
🔍 **Giải thích:**  
- **Tài khoản root** là tài khoản chủ sở hữu ban đầu của tài khoản AWS, có **quyền tối thượng** (admin toàn quyền).  
- Vì rủi ro bảo mật rất cao (có thể xóa toàn bộ dịch vụ), bạn **chỉ nên dùng root khi thực sự cần**, ví dụ: thiết lập ban đầu.  
- Không nên chia sẻ thông tin đăng nhập root cho người khác.

---

### 3. **Users are people within your organization, and can be grouped**  
🔸 **Dịch:** Người dùng là những cá nhân trong tổ chức của bạn, và có thể được phân nhóm.  
🔍 **Giải thích:**  
- Bạn tạo **IAM Users** để cấp quyền cho từng cá nhân cụ thể trong team (VD: dev, tester, admin).  
- Có thể **gom các user vào group** để quản lý quyền hiệu quả hơn, tránh gán quyền thủ công từng người.

---

### 4. **Groups only contain users, not other groups**  
🔸 **Dịch:** Nhóm chỉ chứa **người dùng (users)**, **không thể chứa nhóm khác (groups)**.  
🔍 **Giải thích:**  
- Mỗi **IAM Group** là tập hợp các users. Bạn **không thể lồng nhóm trong nhóm** như một số hệ thống khác.  
- Điều này đơn giản hóa cấu trúc quyền, nhưng đòi hỏi bạn phải tổ chức user theo cách rõ ràng hơn.

---

### 5. **Users don’t have to belong to a group, and user can belong to multiple groups**  
🔸 **Dịch:** Người dùng **không bắt buộc phải thuộc nhóm nào**, và một người dùng có thể **thuộc nhiều nhóm cùng lúc**.  
🔍 **Giải thích:**  
- Bạn có thể tạo user **độc lập** nếu chỉ cần gán quyền riêng lẻ.  
- Hoặc, bạn có thể cho 1 user vào **nhiều group**, để người đó kế thừa quyền từ nhiều vai trò khác nhau (VD: dev + auditor).

---

📌 **Tóm lại:**
IAM là công cụ quan trọng để **bảo mật và phân quyền hợp lý** trong AWS. Việc tổ chức user & group đúng cách giúp team bạn **quản lý dễ dàng hơn, giảm rủi ro bảo mật**.

Nếu bạn muốn mình minh họa bằng sơ đồ hoặc ví dụ IAM policy cụ thể, mình có thể hỗ trợ thêm!