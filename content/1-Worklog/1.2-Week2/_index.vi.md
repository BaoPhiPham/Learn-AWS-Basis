---
title: "Worklog Tuần 2"
date: 2025-09-15
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Nâng cao hiểu biết về **Amazon EC2** và dịch vụ lưu trữ liên quan (**Amazon EBS**).  
* Học cách lưu trữ và truy xuất dữ liệu an toàn bằng **Amazon S3**.  
* Triển khai và kết nối cơ sở dữ liệu thông qua **Amazon RDS**.  
* Tích hợp ứng dụng chạy trên EC2 với **S3** và **RDS** để hình thành hệ thống backend hoàn chỉnh.  
* Thực hành giám sát và tối ưu chi phí cho tài nguyên tính toán và lưu trữ.  

---

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc                                                                                                                                                                                                                                                                                                                                                                                                              | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                       |
| ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------- |
| 2    | - Tìm hiểu **Amazon Elastic Block Store (EBS)** và các loại volume.<br>- **Thực hành:**<br>&emsp;+ Tạo và gắn **EBS Volume** vào một EC2 instance hiện có.<br>&emsp;+ Định dạng và mount volume trên **Linux** và **Windows**.<br>&emsp;+ Tạo **snapshot** và khôi phục volume để kiểm thử sao lưu.<br><br>→ Hiểu quy trình tạo, quản lý và phục hồi EBS.                                                              | 15/09/2025   | 15/09/2025      | [AWS Study Group](https://000009.awsstudygroup.com/) |
| 3    | - Khám phá **Amazon S3** như dịch vụ lưu trữ đối tượng (object storage).<br>- Hiểu cấu trúc bucket, object, versioning và lifecycle management.<br>- **Thực hành:**<br>&emsp;+ Tạo **S3 Bucket** và tải lên nhiều loại file.<br>&emsp;+ Kích hoạt **Versioning** và **Lifecycle Policy**.<br>&emsp;+ Cấu hình **Bucket Policy** và **ACLs** để kiểm soát truy cập.<br><br>→ Làm chủ quy trình quản lý dữ liệu trên S3. | 16/09/2025   | 16/09/2025      | [AWS Study Group](https://000010.awsstudygroup.com/) |
| 4    | - Kết nối ứng dụng trên EC2 với **Amazon S3**.<br>- **Thực hành:**<br>&emsp;+ Viết script (Python/Node.js) trên EC2 để upload và download dữ liệu từ S3.<br>&emsp;+ Sử dụng **IAM Role** thay vì Access Key để xác thực.<br>&emsp;+ Kiểm tra hoạt động bằng **AWS CLI** và **SDK**.<br><br>→ Thực hành tích hợp EC2 ↔ S3 an toàn qua IAM Role.                                                                         | 17/09/2025   | 17/09/2025      | [AWS Study Group](https://000011.awsstudygroup.com/) |
| 5    | - Tìm hiểu cơ bản về **Amazon RDS**: loại cơ sở dữ liệu, Multi-AZ, sao lưu tự động.<br>- **Thực hành:**<br>&emsp;+ Khởi tạo **RDS MySQL Instance**.<br>&emsp;+ Kết nối từ EC2 đến RDS thông qua private subnet trong cùng VPC.<br>&emsp;+ Tạo, truy vấn và quản lý database mẫu.<br><br>→ Hiểu cơ chế vận hành và bảo mật của RDS.                                                                                     | 18/09/2025   | 18/09/2025      | [AWS Study Group](https://000012.awsstudygroup.com/) |
| 6    | - Rà soát và tối ưu tài nguyên compute & storage.<br>- **Thực hành:**<br>&emsp;+ Theo dõi chỉ số EC2 và RDS bằng **Amazon CloudWatch**.<br>&emsp;+ Phân tích mức sử dụng S3 và EBS bằng **AWS Cost Explorer**.<br>&emsp;+ Áp dụng **Lifecycle Policy** để tự động dọn dẹp dữ liệu không dùng.<br><br>→ Nâng cao kỹ năng giám sát và tối ưu chi phí hệ thống.                                                           | 19/09/2025   | 19/09/2025      | [AWS Study Group](https://000013.awsstudygroup.com/) |

---

### Kết quả đạt được trong tuần 2

#### 1. Dịch vụ tính toán và lưu trữ (Compute & Storage)
- Tạo và gắn thành công **EBS Volume** vào EC2 trên cả Linux và Windows.  
- Thực hành **snapshot** và khôi phục dữ liệu để kiểm thử khả năng sao lưu.  
- Hiểu rõ vòng đời volume và mô hình chi phí của EBS.  

#### 2. Lưu trữ đối tượng (Amazon S3)
- Tạo và quản lý nhiều **S3 Bucket** với các thiết lập **Versioning** và **Lifecycle Policy**.  
- Áp dụng **Bucket Policy** và **ACLs** để đảm bảo kiểm soát truy cập và bảo mật dữ liệu.  
- Hiểu cách tổ chức dữ liệu và tối ưu chi phí lưu trữ theo từng tầng.  

#### 3. Cơ sở dữ liệu đám mây (Amazon RDS)
- Khởi tạo và cấu hình thành công **RDS MySQL Instance** trong subnet riêng tư.  
- Kết nối ứng dụng trên EC2 với RDS thông qua mạng nội bộ (VPC).  
- Thực hành quản trị cơ bản: tạo bảng, truy vấn, và snapshot dữ liệu.  

#### 4. Tích hợp ứng dụng
- Viết và chạy thành công script **upload/download giữa EC2 và S3** sử dụng **IAM Role** thay cho Access Key.  
- Xây dựng và kiểm thử luồng dữ liệu hoàn chỉnh **EC2 → S3 → RDS**, hình thành hệ thống backend cơ bản.  

#### 5. Giám sát và tối ưu chi phí
- Theo dõi hiệu năng EC2, RDS qua **Amazon CloudWatch** và phân tích chi phí bằng **Cost Explorer**.  
- Phát hiện tài nguyên không sử dụng và tối ưu cấu hình EBS/S3.  
- Cải thiện khả năng nhận diện và kiểm soát chi phí cho tầng tính toán và lưu trữ.  
