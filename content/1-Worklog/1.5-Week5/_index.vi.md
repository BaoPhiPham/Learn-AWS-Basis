---
title: "Worklog Tuần 5"
date: 2025-10-06
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:

* Tìm hiểu cách **giám sát hiệu năng hệ thống** và thu thập log bằng **Amazon CloudWatch**.  
* Khám phá **AWS CloudTrail** để theo dõi hoạt động API và người dùng.  
* Triển khai cơ chế cảnh báo tự động với **Amazon SNS**.  
* Phân tích các **chỉ số hiệu suất** và phản ứng kịp thời với các sự kiện scaling hoặc lỗi hệ thống.  
* Thực hành xây dựng một **giải pháp giám sát toàn diện** cho môi trường AWS.

---

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                                                                                         | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                       |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------- |
| 2    | - Học về **Amazon CloudWatch Metrics**.<br>- **Thực hành:**<br>&emsp;+ Theo dõi CPU, bộ nhớ, network của EC2.<br>&emsp;+ Tạo **Dashboard** để hiển thị các chỉ số quan trọng.<br><br>→ Có cái nhìn trực quan về trạng thái hệ thống.                                                                              | 06/10/2025   | 06/10/2025      | [AWS Study Group](https://000024.awsstudygroup.com/) |
| 3    | - Khám phá **CloudWatch Alarms**.<br>- **Thực hành:**<br>&emsp;+ Tạo alarm cho CPU, Memory, Disk sử dụng thresholds.<br>&emsp;+ Cấu hình hành động khi vượt ngưỡng (ví dụ gửi SNS).<br><br>→ Phản ứng kịp thời với các sự kiện bất thường.                                                                        | 07/10/2025   | 07/10/2025      | [AWS Study Group](https://000025.awsstudygroup.com/) |
| 4    | - Tìm hiểu **AWS CloudTrail**.<br>- **Thực hành:**<br>&emsp;+ Bật CloudTrail để ghi log các API calls.<br>&emsp;+ Kiểm tra các hoạt động người dùng và instance.<br><br>→ Theo dõi toàn bộ hoạt động hệ thống và tuân thủ bảo mật.                                                                                | 08/10/2025   | 08/10/2025      | [AWS Study Group](https://000026.awsstudygroup.com/) |
| 5    | - Khám phá **Amazon SNS** cho cảnh báo.<br>- **Thực hành:**<br>&emsp;+ Tạo topic SNS.<br>&emsp;+ Subscribe email và SMS để nhận thông báo.<br>&emsp;+ Kết nối CloudWatch Alarm với SNS.<br><br>→ Thiết lập cơ chế cảnh báo tự động cho sự kiện hệ thống.                                                          | 09/10/2025   | 09/10/2025      | [AWS Study Group](https://000027.awsstudygroup.com/) |
| 6    | - Tích hợp **CloudWatch, CloudTrail, SNS** thành giải pháp giám sát toàn diện.<br>- **Thực hành:**<br>&emsp;+ Giám sát EC2, RDS, ELB.<br>&emsp;+ Phân tích log và cảnh báo tự động.<br>&emsp;+ Kiểm thử phản ứng với tình huống giả lập (scale, lỗi ứng dụng).<br><br>→ Hoàn thiện hệ thống vận hành và cảnh báo. | 10/10/2025   | 10/10/2025      | [AWS Study Group](https://000028.awsstudygroup.com/) |

---

### Kết quả đạt được trong Tuần 5

#### 1. Amazon CloudWatch
- Giám sát và thu thập **metrics** cho EC2, RDS, ELB.  
- Tạo **Dashboard** trực quan hiển thị các chỉ số quan trọng.  
- Hiểu cơ chế cảnh báo dựa trên **thresholds** và tần suất kiểm tra.  

#### 2. CloudWatch Alarms & SNS
- Thiết lập **CloudWatch Alarm** theo CPU, Memory, Disk.  
- Kết nối với **SNS topic** để gửi cảnh báo email/SMS tự động.  
- Kiểm tra hoạt động cảnh báo khi xảy ra sự kiện bất thường.  

#### 3. AWS CloudTrail
- Bật và cấu hình **CloudTrail** ghi lại toàn bộ hoạt động API.  
- Theo dõi hành vi người dùng và sự kiện hệ thống.  
- Hỗ trợ tuân thủ bảo mật và truy vết sự cố.  

#### 4. Giải pháp giám sát toàn diện
- Tích hợp **CloudWatch, CloudTrail, SNS** thành một hệ thống giám sát hoàn chỉnh.  
- Phân tích log, phản ứng kịp thời với các tình huống scale hoặc lỗi.  
- Nâng cao khả năng vận hành, cảnh báo và quản lý hạ tầng AWS.