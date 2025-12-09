---
title: "Worklog Tuần 1"
date: 2025-09-08
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Hiểu và triển khai các chiến lược **quản lý chi phí** bằng **AWS Budgets**.  
* Nắm vững các khái niệm cốt lõi của **AWS Identity and Access Management (IAM)**, bao gồm người dùng (Users), nhóm (Groups) và vai trò (Roles).  
* Xây dựng hạ tầng mạng đám mây **bảo mật và độc lập** bằng **Amazon VPC** kết hợp với **Site-to-Site VPN**.  
* Khởi tạo, cấu hình và quản lý máy chủ ảo bằng **Amazon EC2**.  
* Cấp quyền truy cập dịch vụ AWS cho ứng dụng chạy trên EC2 một cách an toàn thông qua **IAM Roles**.  

---

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                       |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------- |
| 2    | - Tìm hiểu cách theo dõi và kiểm soát chi phí AWS bằng **AWS Budgets**.<br>- Phân biệt các loại ngân sách khác nhau.<br>- **Thực hành:**<br>&emsp;+ Tạo **Cost Budget** để theo dõi tổng chi tiêu.<br>&emsp;+ Tạo **Usage Budget** để giám sát mức sử dụng dịch vụ cụ thể.<br>&emsp;+ Khám phá **Reservation & Savings Plans Budgets** để theo dõi cam kết sử dụng.                                            | 08/09/2025   | 08/09/2025      | [AWS Study Group](https://000007.awsstudygroup.com/) |
| 3    | - Tìm hiểu các khái niệm cơ bản của IAM: Users, Groups, Policies, Roles.<br>- Tuân thủ các nguyên tắc bảo mật cho tài khoản root.<br>- **Thực hành:**<br>&emsp;+ Tạo **Admin Group** với quyền AdministratorAccess.<br>&emsp;+ Tạo **IAM User** mới và thêm vào nhóm Admin.<br>&emsp;+ Tìm hiểu cách tạo và sử dụng **IAM Role**.<br>&emsp;+ Thực hành tính năng **Switch Role**.                              | 09/09/2025   | 09/09/2025      | [AWS Study Group](https://000002.awsstudygroup.com/) |
| 4    | - Học cách xây dựng mạng riêng ảo với **Amazon VPC**.<br>- Hiểu các thành phần của VPC: subnet, route table, internet gateway.<br>- **Thực hành:**<br>&emsp;+ Tạo VPC với subnet công khai và riêng tư.<br>&emsp;+ Cấu hình **Security Groups** làm tường lửa trạng thái.<br>&emsp;+ Khởi tạo EC2 trong VPC.<br>&emsp;+ Thiết lập kết nối **Site-to-Site VPN**.                                                | 10/09/2025   | 10/09/2025      | [AWS Study Group](https://000003.awsstudygroup.com/) |
| 5    | - Làm quen với các khái niệm cốt lõi của **Amazon EC2**.<br>- Triển khai ứng dụng trên nhiều hệ điều hành khác nhau.<br>- **Thực hành:**<br>&emsp;+ Khởi tạo **Windows Server 2022** và kết nối qua RDP.<br>&emsp;+ Khởi tạo **Amazon Linux 2** và kết nối qua SSH.<br>&emsp;+ Triển khai ứng dụng quản lý người dùng trên cả hai hệ thống.<br>&emsp;+ Áp dụng chiến lược **giám sát và quản lý chi phí EC2**. | 11/09/2025   | 11/09/2025      | [AWS Study Group](https://000004.awsstudygroup.com/) |
| 6    | - Hiểu lý do tại sao việc nhúng trực tiếp Access Key vào ứng dụng là rủi ro bảo mật.<br>- Tìm hiểu cách sử dụng **IAM Roles for EC2** để cấp quyền truy cập an toàn.<br>- **Thực hành:**<br>&emsp;+ Chuẩn bị S3 bucket và EC2 instance.<br>&emsp;+ Tạo **IAM Role** với quyền truy cập S3.<br>&emsp;+ Gắn Role vào EC2 instance.<br>&emsp;+ Kiểm tra ứng dụng có thể truy cập S3 mà không cần Access Key.      | 12/09/2025   | 12/09/2025      | [AWS Study Group](https://000048.awsstudygroup.com/) |

---

### Kết quả đạt được trong tuần 1

#### Quản lý chi phí (Cost Management)
- Tạo và cấu hình thành công **AWS Budgets** để theo dõi chi phí và mức sử dụng.  
- Thực hành thiết lập nhiều loại ngân sách khác nhau: **Cost Budget**, **Usage Budget**, **Reservation Budget**, và **Savings Plans Budget**.  

#### Quản lý danh tính và truy cập (IAM)
- Thành thạo việc tạo **người dùng (User)** và **nhóm (Group)** để quản lý quyền truy cập.  
- Áp dụng nguyên tắc **Least Privilege** thông qua việc tạo nhóm và người dùng quản trị riêng biệt.  
- Hiểu và thực hành việc tạo **IAM Role** để phân quyền an toàn; sử dụng tính năng **Switch Role**.  

#### Hạ tầng mạng (VPC & VPN)
- Xây dựng hoàn chỉnh một **Amazon VPC** tùy chỉnh với subnet, internet gateway và route table.  
- Cấu hình **Security Groups** làm tường lửa cho các EC2 instance.  
- Thiết lập thành công **Site-to-Site VPN**, mô phỏng môi trường hybrid cloud.  

#### Điện toán đám mây (Amazon EC2)
- Khởi tạo và quản lý thành công các instance **Windows Server** và **Amazon Linux 2**.  
- Thực hành kết nối, quản trị cơ bản và triển khai ứng dụng quản lý người dùng.  
- Áp dụng chiến lược **quản lý chi phí và sử dụng EC2** hiệu quả.  

#### Tích hợp ứng dụng an toàn
- Hiểu rõ rủi ro bảo mật khi dùng Access Key tĩnh trong ứng dụng.  
- Tạo thành công **IAM Role for EC2** để cấp quyền truy cập tạm thời, an toàn đến các dịch vụ khác (như S3).  
- Kiểm chứng rằng ứng dụng trên EC2 có thể truy cập tài nguyên S3 mà không cần thông tin xác thực cứng.  