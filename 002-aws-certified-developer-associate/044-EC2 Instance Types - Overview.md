# EC2 Instance Types – Tổng quan

- **Bạn có thể sử dụng nhiều loại EC2 instances được tối ưu cho các kịch bản khác nhau**  
  (ví dụ: tính toán chung, tính toán hiệu năng cao, bộ nhớ lớn, máy học, lưu trữ…)  
  Tham khảo chi tiết tại: https://aws.amazon.com/ec2/instance-types/

- **AWS có quy tắc đặt tên chung cho các instance: `<class><generation>.<size>`**  
  Ví dụ: **m5.2xlarge**

  1. **m**: Instance class  
     - `m` = General Purpose (tính toán chung)  
     - Các class khác:  
       - `t` (Burstable General Purpose)  
       - `c` (Compute Optimized)  
       - `r` (Memory Optimized)  
       - `p`, `g`, `f` (Accelerated Computing – GPU/FPGA)  
       - `i`, `d` (Storage Optimized)  
       - `hpc` (HPC Optimized)  
  2. **5**: Generation (thế hệ thứ 5)  
     - Số càng lớn, hiệu năng và tính năng càng mới, càng được AWS cải tiến.  
  3. **2xlarge**: Kích cỡ trong class  
     - Quy định số CPU vCPU, RAM… Ví dụ `2xlarge` thường có nhiều vCPU/RAM hơn `large` hay `xlarge`.

> **Ví dụ một số family phổ biến**  
> - General Purpose: `t3.micro`, `m5.large`  
> - Compute Optimized: `c5.xlarge`  
> - Memory Optimized: `r5.2xlarge`  
> - Accelerated Computing: `p3.8xlarge`, `g4dn.xlarge`  
> - Storage Optimized: `i3.large`, `d2.4xlarge`

---

> **Lưu ý:**  
> Lựa chọn instance type phù hợp giúp tối ưu chi phí và hiệu năng cho ứng dụng của bạn. Vui lòng kiểm tra kỹ thông số (CPU, RAM, I/O, mạng) trên trang chính thức trước khi triển khai.