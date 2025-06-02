## EC2 User Data

1. **Bạn có thể bootstrap instance bằng script EC2 User Data**  
   - *Dịch:* Có thể khởi tạo (bootstrap) các phiên bản EC2 bằng một script EC2 User Data.  
   - *Giải thích:* Khi tạo instance, bạn chèn shell script (Linux) hoặc PowerShell/BAT (Windows) vào phần User Data.

2. **Bootstrapping means launching commands when a machine starts**  
   - *Dịch:* Bootstrapping nghĩa là chạy các lệnh ngay khi máy khởi động.  
   - *Giải thích:* Trình thực thi User Data sẽ đọc và chạy các lệnh này trong giai đoạn khởi tạo.

3. **That script is only run once at the instance first start**  
   - *Dịch:* Script này chỉ chạy **một lần** khi instance khởi động lần đầu.  
   - *Giải thích:* Nếu bạn dừng (stop) rồi khởi động lại (start) lại instance, User Data sẽ **không** chạy lại.

4. **EC2 User Data is used to automate boot tasks such as:**  
   - *Dịch:* EC2 User Data dùng để tự động hóa các tác vụ khởi động như:  
     - Installing updates  
       - *Giải thích:* Tự động chạy `yum update`, `apt-get upgrade`…  
     - Installing software  
       - *Giải thích:* Cài đặt web server (Apache/Nginx), database, thư viện…  
     - Downloading common files from the internet  
       - *Giải thích:* Kéo code, tài nguyên tĩnh, bản cấu hình từ S3 hoặc GitHub…  
     - Anything you can think of  
       - *Giải thích:* Bất cứ kịch bản khởi tạo nào bạn cần: cấu hình mạng, mount ổ, thiết lập cron…

5. **The EC2 User Data Script runs with the root user**  
   - *Dịch:* Script EC2 User Data chạy với quyền **root**.  
   - *Giải thích:* Cho phép script thực thi mọi lệnh hệ thống mà không cần thêm bước `sudo`.

---

> **Lưu ý khi sử dụng User Data:**  
> - Kiểm tra kỹ nội dung script trước khi deploy, vì nó chạy tự động với quyền cao nhất.  
> - Dùng `cloud-init` (Linux) hoặc `EC2Launch` (Windows) để có thêm tùy chọn cấu hình nâng cao.  
> - Nếu cần chạy lại, bạn có thể thiết lập lại metadata hoặc dùng custom AMI đã cấu hình sẵn.