---
title: "Worklog Tuần 3"
date: 2025-09-22
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

* Học cách thiết kế **hạ tầng có tính sẵn sàng cao và khả năng mở rộng linh hoạt** trên AWS.  
* Triển khai **Elastic Load Balancing (ELB)** và **Auto Scaling Groups (ASG)** để tự động phân phối lưu lượng và mở rộng máy chủ.  
* Cấu hình **Amazon Route 53** cho quản lý tên miền và định tuyến DNS.  
* Tăng độ tin cậy của hệ thống thông qua **sao lưu dữ liệu** và **giám sát**.  
* Thực hành phân tích các chỉ số hiệu năng và phản ứng với sự kiện mở rộng.  

---

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                                                                                                                                                                                             | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                       |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------- |
| 2    | - Tìm hiểu khái niệm về **Elastic Load Balancing (ELB)**.<br>- Hiểu các loại Load Balancer: Application, Network, và Gateway.<br>- **Thực hành:**<br>&emsp;+ Triển khai hai EC2 instance ở hai Availability Zone khác nhau.<br>&emsp;+ Tạo **Application Load Balancer (ALB)** và cấu hình Target Groups.<br>&emsp;+ Kiểm tra khả năng phân phối tải qua ứng dụng web.<br><br>→ Thành thạo quản lý lưu lượng với ELB. | 22/09/2025   | 22/09/2025      | [AWS Study Group](https://000014.awsstudygroup.com/) |
| 3    | - Học về **Auto Scaling Groups (ASG)** và các chính sách mở rộng.<br>- **Thực hành:**<br>&emsp;+ Tạo **Launch Template** cho cấu hình EC2.<br>&emsp;+ Cấu hình **ASG** với số lượng instance tối thiểu và tối đa.<br>&emsp;+ Kiểm tra chính sách **scale-out** và **scale-in** dựa trên chỉ số CPU.<br><br>→ Triển khai mở rộng động dựa theo tải công việc.                                                          | 23/09/2025   | 23/09/2025      | [AWS Study Group](https://000015.awsstudygroup.com/) |
| 4    | - Khám phá **Amazon Route 53** và các chính sách định tuyến DNS.<br>- **Thực hành:**<br>&emsp;+ Đăng ký tên miền hoặc tạo Hosted Zone.<br>&emsp;+ Cấu hình bản ghi **A/AAAA** và **CNAME**.<br>&emsp;+ Kết nối **Route 53** với DNS của Load Balancer.<br><br>→ Hiểu cách định tuyến tên miền và xử lý failover.                                                                                                      | 24/09/2025   | 24/09/2025      | [AWS Study Group](https://000016.awsstudygroup.com/) |
| 5    | - Học về **sao lưu và phục hồi (backup & recovery)** trên AWS.<br>- **Thực hành:**<br>&emsp;+ Tạo **EBS snapshot** và **RDS automated backup**.<br>&emsp;+ Lưu trữ backup trong **Amazon S3** bằng **Lifecycle Policies**.<br>&emsp;+ Kiểm tra phục hồi dữ liệu từ snapshot.<br><br>→ Đảm bảo tính bền vững hệ thống qua chiến lược sao lưu tự động.                                                                  | 25/09/2025   | 25/09/2025      | [AWS Study Group](https://000017.awsstudygroup.com/) |
| 6    | - Nâng cao khả năng quan sát với **Amazon CloudWatch** và **AWS CloudTrail**.<br>- **Thực hành:**<br>&emsp;+ Tạo **CloudWatch Alarms** theo dõi CPU, bộ nhớ và mạng.<br>&emsp;+ Theo dõi **ASG scaling events** và **ELB request metrics**.<br>&emsp;+ Sử dụng **CloudTrail** để ghi lại hoạt động người dùng và API calls.<br><br>→ Xây dựng giải pháp giám sát và audit hoàn chỉnh.                                 | 26/09/2025   | 26/09/2025      | [AWS Study Group](https://000018.awsstudygroup.com/) |

---

### Kết quả đạt được trong tuần 3

#### 1. Elastic Load Balancing (ELB)
- Triển khai và cấu hình thành công **Application Load Balancer** để phân phối lưu lượng giữa nhiều EC2 instance.  
- Kiểm tra thành công cơ chế **load balancing và failover** thông qua bài test hiệu năng.  
- Hiểu rõ sự khác biệt giữa **Application**, **Network**, và **Gateway Load Balancer**.  

#### 2. Auto Scaling Groups (ASG)
- Tạo và kiểm thử thành công **Auto Scaling Group** bằng **Launch Template**.  
- Áp dụng **target tracking** và **step scaling policies** dựa trên CPU utilization.  
- Xác minh cơ chế tự động mở rộng và thay thế instance khi gặp lỗi.  

#### 3. Amazon Route 53
- Cấu hình định tuyến DNS cho ứng dụng web thông qua **Route 53 Hosted Zones**.  
- Liên kết bản ghi **Route 53** với **Load Balancer DNS name** để truy cập qua domain.  
- Hiểu các loại **routing policies** như Simple, Weighted, và Failover.  

#### 4. Sao lưu và phục hồi
- Tạo và kiểm tra **EBS snapshots** và **RDS automated backups**.  
- Quản lý **lưu trữ backup trên S3** với **Lifecycle Management**.  
- Phục hồi tài nguyên thành công từ snapshot để đảm bảo khả năng khôi phục thảm họa.  

#### 5. Giám sát và quan sát hệ thống
- Cấu hình **CloudWatch Alarms** để phát hiện bất thường về hiệu năng.  
- Theo dõi **sự kiện mở rộng ASG**, **chỉ số ELB requests**, và **hiệu năng RDS**.  
- Ghi nhận hoạt động API và hành động người dùng qua **CloudTrail**, cải thiện khả năng giám sát và tuân thủ bảo mật.  
