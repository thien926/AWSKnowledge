## **Hướng dẫn kết nối AWS CLI từng bước cụ thể**  

AWS CLI (Command Line Interface) cho phép bạn tương tác với các dịch vụ AWS thông qua dòng lệnh. Dưới đây là hướng dẫn chi tiết để cài đặt và cấu hình AWS CLI trên máy tính của bạn.  

---

## **1️⃣ Bước 1: Cài đặt AWS CLI**  

### 🔹 **Windows**  
1. **Tải AWS CLI** từ trang chính thức:  
   👉 [AWS CLI Installer for Windows](https://awscli.amazonaws.com/AWSCLIV2.msi)  
2. **Chạy file `.msi`** vừa tải về và làm theo hướng dẫn cài đặt.  
3. **Kiểm tra AWS CLI đã cài đặt chưa** bằng cách mở `Command Prompt (cmd)` và chạy lệnh:  
   ```bash
   aws --version
   ```
   **Kết quả mong đợi:**  
   ```
   aws-cli/2.x.x Python/3.x.x Windows/x86_64
   ```

### 🔹 **macOS**  
1. **Cài đặt bằng Homebrew:**  
   ```bash
   brew install awscli
   ```
2. **Kiểm tra phiên bản AWS CLI:**  
   ```bash
   aws --version
   ```

### 🔹 **Linux (Ubuntu/Debian)**  
1. **Tải AWS CLI về:**  
   ```bash
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   ```
2. **Giải nén và cài đặt:**  
   ```bash
   unzip awscliv2.zip
   sudo ./aws/install
   ```
3. **Kiểm tra AWS CLI:**  
   ```bash
   aws --version
   ```

---

## **2️⃣ Bước 2: Tạo Access Key & Secret Key trên AWS**  
Bạn cần có **Access Key** và **Secret Key** để kết nối AWS CLI với tài khoản AWS.  

1. **Truy cập AWS Console** 👉 [AWS IAM Console](https://console.aws.amazon.com/iam/)  
2. Chọn **Users** → Chọn user của bạn  
3. Chọn tab **Security credentials**  
4. Nhấn **Create access key**  
5. Lưu lại **Access Key ID** và **Secret Access Key** (chỉ hiển thị 1 lần).  

---

## **3️⃣ Bước 3: Cấu hình AWS CLI**  
Sau khi có Access Key và Secret Key, bạn cần thiết lập cấu hình AWS CLI.  

1. Mở Terminal (`cmd`, `PowerShell`, `bash`, `zsh`)  
2. Chạy lệnh:  
   ```bash
   aws configure
   ```
3. Nhập thông tin:  
   ```
   AWS Access Key ID [None]: <Access Key ID>
   AWS Secret Access Key [None]: <Secret Access Key>
   Default region name [None]: us-east-1 (hoặc region bạn muốn dùng)
   Default output format [None]: json (hoặc text, table)
   ```
4. Kiểm tra kết nối:  
   ```bash
   aws s3 ls
   ```  
   Nếu hiển thị danh sách S3 Buckets thì bạn đã kết nối thành công! 🚀  

---

## **4️⃣ Bước 4: Kiểm tra danh sách tài khoản và Region**  
✅ **Kiểm tra thông tin tài khoản AWS đang sử dụng:**  
```bash
aws sts get-caller-identity
```
📌 **Kết quả mong đợi:**  
```json
{
    "UserId": "ABCDEFGHIJKL",
    "Account": "123456789012",
    "Arn": "arn:aws:iam::123456789012:user/my-user"
}
```

✅ **Kiểm tra Region đã cấu hình:**  
```bash
aws configure get region
```

✅ **Xem danh sách Region có sẵn:**  
```bash
aws ec2 describe-regions --output table
```

---

## **5️⃣ Một số lệnh AWS CLI phổ biến**  

### 🔹 **Làm việc với S3**  
✅ **Liệt kê tất cả các S3 Buckets:**  
```bash
aws s3 ls
```
✅ **Tạo S3 Bucket mới:**  
```bash
aws s3 mb s3://my-new-bucket
```
✅ **Tải file lên S3:**  
```bash
aws s3 cp myfile.txt s3://my-new-bucket/
```

### 🔹 **Làm việc với EC2**  
✅ **Liệt kê tất cả các instances đang chạy:**  
```bash
aws ec2 describe-instances
```
✅ **Khởi động một instance mới:**  
```bash
aws ec2 run-instances --image-id ami-12345678 --count 1 --instance-type t2.micro --key-name MyKeyPair
```

---

## **🔥 Tổng kết**  
✔ **Bước 1**: Cài đặt AWS CLI  
✔ **Bước 2**: Lấy Access Key và Secret Key từ AWS  
✔ **Bước 3**: Cấu hình AWS CLI bằng lệnh `aws configure`  
✔ **Bước 4**: Kiểm tra kết nối bằng `aws sts get-caller-identity`  
✔ **Bước 5**: Bắt đầu sử dụng AWS CLI với các lệnh cơ bản  
