---
title: "Worklog Tuần 4"
date: 2025-09-29
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Học cách triển khai, quản lý và bảo mật **cơ sở dữ liệu quan hệ (RDS)** trên AWS.  
* Hiểu rõ các khái niệm cốt lõi của **Amazon S3** về lưu trữ đối tượng và quản lý vòng đời dữ liệu.  
* Khám phá **Amazon EFS** để triển khai hệ thống lưu trữ chia sẻ giữa nhiều EC2 instance.  
* Thực hiện các chiến lược **sao lưu, phiên bản hóa (versioning)** và **mã hóa dữ liệu** để đảm bảo tính bền vững và tuân thủ bảo mật.  
* Tăng cường kiểm soát truy cập thông qua **IAM Policies**, **Bucket Policies** và **xác thực cơ sở dữ liệu (Database Authentication)**.

---

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                       |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------- |
| 2    | - Tìm hiểu khái niệm **Amazon RDS**: DB Instance, Multi-AZ, Read Replica.<br>- **Thực hành:**<br>&emsp;+ Khởi tạo một **RDS MySQL instance**.<br>&emsp;+ Cấu hình **Parameter Group** và **Security Group**.<br>&emsp;+ Kết nối qua EC2 và kiểm thử thao tác CRUD cơ bản.<br><br>→ Làm quen với việc triển khai và vận hành cơ sở dữ liệu trên AWS.                             | 29/09/2025   | 29/09/2025      | [AWS Study Group](https://000019.awsstudygroup.com/) |
| 3    | - Khám phá dịch vụ **Amazon S3**.<br>- Hiểu về **Storage Classes** và **Lifecycle Policies**.<br>- **Thực hành:**<br>&emsp;+ Tạo **S3 bucket** có bật **Versioning**.<br>&emsp;+ Thực hiện thao tác upload, download và xóa đối tượng.<br>&emsp;+ Thiết lập **Lifecycle Rule** để lưu trữ dữ liệu cũ sang **Glacier**.<br><br>→ Quản lý dữ liệu hiệu quả và tối ưu chi phí.     | 30/09/2025   | 30/09/2025      | [AWS Study Group](https://000020.awsstudygroup.com/) |
| 4    | - Tìm hiểu dịch vụ **Amazon EFS** (Elastic File System).<br>- **Thực hành:**<br>&emsp;+ Tạo hệ thống tệp EFS mới.<br>&emsp;+ Mount EFS vào hai EC2 instance.<br>&emsp;+ Kiểm tra khả năng truy cập đồng thời và đồng bộ hóa dữ liệu.<br><br>→ Hiểu rõ cách vận hành hệ thống lưu trữ chia sẻ trong môi trường phân tán.                                                         | 01/10/2025   | 01/10/2025      | [AWS Study Group](https://000021.awsstudygroup.com/) |
| 5    | - Nâng cao chiến lược **bảo vệ và sao lưu dữ liệu**.<br>- **Thực hành:**<br>&emsp;+ Bật **Automated Backup** và thiết lập **Snapshot Scheduling** cho RDS.<br>&emsp;+ Kích hoạt **S3 Versioning** và **Cross-Region Replication (CRR)**.<br>&emsp;+ Mã hóa dữ liệu ở trạng thái nghỉ bằng **AWS KMS**.<br><br>→ Đảm bảo an toàn dữ liệu và khả năng khôi phục khi xảy ra sự cố. | 02/10/2025   | 02/10/2025      | [AWS Study Group](https://000022.awsstudygroup.com/) |
| 6    | - Tăng cường kiểm soát truy cập và bảo mật.<br>- **Thực hành:**<br>&emsp;+ Thiết lập **IAM Policy** và **Bucket Policy** theo nguyên tắc least privilege.<br>&emsp;+ Áp dụng **IAM Database Authentication** cho RDS.<br>&emsp;+ Theo dõi nhật ký truy cập qua **CloudTrail**.<br><br>→ Cải thiện khả năng quản trị, tuân thủ và bảo mật dữ liệu.                               | 03/10/2025   | 03/10/2025      | [AWS Study Group](https://000023.awsstudygroup.com/) |

---

### Kết quả đạt được trong tuần 4

#### 1. Amazon RDS
- Khởi tạo và cấu hình thành công **MySQL RDS Instance** với chế độ **Multi-AZ**.  
- Thực hiện thao tác đọc/ghi dữ liệu và kiểm thử kết nối qua EC2.  
- Hiểu và ứng dụng được **Automated Backup**, **Snapshot** và **Parameter Group**.  

#### 2. Amazon S3
- Tạo **S3 Bucket** có bật **Versioning** và cấu hình **Lifecycle Management**.  
- Thực hành thao tác **upload, delete, restore** và lưu trữ lạnh trên **Glacier**.  
- Tối ưu chi phí bằng cách lựa chọn lớp lưu trữ phù hợp (Standard, IA, Glacier).  

#### 3. Amazon EFS
- Thiết lập và mount thành công **EFS File System** cho nhiều EC2 instance.  
- Kiểm tra khả năng chia sẻ dữ liệu và đảm bảo tính đồng bộ.  
- So sánh ưu/nhược điểm giữa **EFS**, **EBS** và **S3** cho từng loại workload.  

#### 4. Sao lưu & bảo mật dữ liệu
- Triển khai **RDS Automated Backup** và **Snapshot Scheduling** thành công.  
- Áp dụng **KMS Encryption** và **Cross-Region Replication (CRR)** trên S3.  
- Tuân thủ các nguyên tắc trong **AWS Well-Architected Security Pillar**.  

#### 5. Kiểm soát truy cập & giám sát
- Thiết kế **IAM Policy** và **Bucket Policy** theo nguyên tắc phân quyền tối thiểu.  
- Thực hiện xác thực người dùng qua **IAM Database Authentication**.  
- Giám sát hoạt động truy cập qua **AWS CloudTrail** nhằm đảm bảo tính minh bạch và bảo mật hệ thống.  
