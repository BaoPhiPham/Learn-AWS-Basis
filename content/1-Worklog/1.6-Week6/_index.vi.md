---
title: "Worklog Tuần 6"
date: 2025-10-13
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu của Tuần 6:

* Tìm hiểu cách thiết kế và triển khai **kiến trúc serverless** trên AWS.  
* Xây dựng và kiểm thử ứng dụng sử dụng **AWS Lambda**, **API Gateway** và **DynamoDB**.  
* Tự động hóa việc triển khai hạ tầng bằng **AWS CloudFormation**.  
* Khám phá thiết kế **event-driven** (dựa trên sự kiện) và tích hợp giữa các dịch vụ.  
* Áp dụng các phương pháp **giám sát và logging** cho môi trường serverless.  

---

### Các công việc cần triển khai trong tuần này:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                       |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------- |
| 2    | - Tìm hiểu khái niệm và lợi ích của **Serverless Computing**.<br>- So sánh khi nào nên dùng **Lambda** thay vì **EC2**.<br>- **Thực hành:**<br>&emsp;+ Tạo một **Lambda function** đơn giản bằng Python.<br>&emsp;+ Kiểm thử function qua AWS Console và CLI.<br><br>→ Hiểu cơ chế hoạt động cơ bản của serverless.                                       | 13/10/2025   | 13/10/2025      | [AWS Study Group](https://000031.awsstudygroup.com/) |
| 3    | - Học cách xây dựng API bằng **Amazon API Gateway**.<br>- **Thực hành:**<br>&emsp;+ Tạo endpoint REST API kết nối với Lambda.<br>&emsp;+ Triển khai API theo từng stage và kiểm tra truy cập công khai.<br><br>→ Hiểu cách API tích hợp với Lambda.                                                                                                       | 14/10/2025   | 14/10/2025      | [AWS Study Group](https://000032.awsstudygroup.com/) |
| 4    | - Làm việc với **Amazon DynamoDB** để lưu trữ dữ liệu serverless.<br>- **Thực hành:**<br>&emsp;+ Tạo bảng DynamoDB, định nghĩa khóa phân vùng và khóa sắp xếp.<br>&emsp;+ Kết nối Lambda để thực hiện các thao tác CRUD.<br>&emsp;+ Kiểm thử việc truy xuất và cập nhật dữ liệu qua API Gateway.<br><br>→ Nắm vững kiến trúc serverless dựa trên dữ liệu. | 15/10/2025   | 15/10/2025      | [AWS Study Group](https://000033.awsstudygroup.com/) |
| 5    | - Tìm hiểu **AWS CloudFormation** để quản lý hạ tầng dưới dạng mã (IaC).<br>- **Thực hành:**<br>&emsp;+ Viết file YAML để triển khai Lambda, API Gateway và DynamoDB.<br>&emsp;+ Tự động tạo và xóa stack bằng CloudFormation.<br><br>→ Biết cách tự động triển khai hệ thống serverless bằng mã nguồn.                                                   | 16/10/2025   | 16/10/2025      | [AWS Study Group](https://000034.awsstudygroup.com/) |
| 6    | - Cấu hình giám sát và tự động hóa cho hệ thống serverless.<br>- **Thực hành:**<br>&emsp;+ Dùng **CloudWatch Logs** để xem log thực thi Lambda.<br>&emsp;+ Thiết lập **CloudWatch Alarms** để cảnh báo lỗi hoặc giới hạn.<br>&emsp;+ Tạo quy tắc tự động bằng **EventBridge**.<br><br>→ Nâng cao khả năng giám sát và tự động phản ứng trong hệ thống.    | 17/10/2025   | 17/10/2025      | [AWS Study Group](https://000035.awsstudygroup.com/) |

---

### Kết quả đạt được trong Tuần 6

#### 1. Kiến thức cơ bản về Serverless
- Hiểu rõ lợi ích của kiến trúc serverless (không cần quản lý server, tự động mở rộng, trả phí theo mức sử dụng).  
- Tạo và kiểm thử **Lambda function** được kích hoạt thủ công và bằng sự kiện API.  

#### 2. Tích hợp với API Gateway
- Xây dựng **REST API** bằng **API Gateway** kết nối với **Lambda**.  
- Triển khai nhiều stage (dev, prod) và kiểm thử truy cập công khai thành công.  

#### 3. Kết nối với DynamoDB
- Thiết kế bảng **DynamoDB** với cấu trúc khóa hiệu quả cho truy xuất nhanh.  
- Tích hợp Lambda để thực hiện **CRUD operations** trực tiếp.  
- Hoàn thiện quy trình **API → Lambda → DynamoDB** đầy đủ.  

#### 4. Hạ tầng dưới dạng mã (IaC)
- Tự động triển khai kiến trúc serverless bằng **CloudFormation**.  
- Quản lý vòng đời stack (tạo, cập nhật, xóa) một cách linh hoạt và tái sử dụng.  

#### 5. Giám sát và Tự động hóa
- Cấu hình **CloudWatch Logs** và **CloudWatch Alarms** để phát hiện sự cố.  
- Sử dụng **EventBridge** để tự động phản ứng khi có sự kiện từ Lambda.  
- Tăng cường khả năng quan sát, độ tin cậy và tính tự động của hệ thống serverless.  