---
title: "Worklog Tuần 9"
date: 2025-11-02
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

- Phân tích nghiệp vụ.
- Viết Proposal dự án.

### Các công việc cần triển khai trong tuần này:

| **Ngày** | **Nhiệm vụ**                                                                                                                                                   | **Bắt đầu** | **Hoàn thành** | **Tài liệu tham khảo**                            |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | -------------- | ------------------------------------------------- |
| 2        | - Phân tích User Story (Admin, Student).<br>- Xác định tính năng Core: CRUD sinh viên, Chat, Ranking.<br>- Lập danh sách Use Cases chi tiết.                   | 03/11/2025  | 03/11/2025     | —                                                 |
| 3        | - Viết Proposal: Tuyên bố vấn đề & Giải pháp.<br>- Tính toán chi phí dự kiến bằng **AWS Pricing Calculator**.<br>- Phân tích lợi ích của kiến trúc Serverless. | 04/11/2025  | 04/11/2025     | [AWS Pricing Calculator](https://calculator.aws/) |
| 4        | - Vẽ Flowchart nghiệp vụ (Luồng đăng nhập, luồng nộp bài).<br>- Thiết kế ERD cho DynamoDB Schema.<br>- Xác định API endpoints cần thiết.                       | 05/11/2025  | 05/11/2025     | —                                                 |
| 5        | - Review Proposal cùng nhóm.<br>- Chốt Tech Stack: DynamoDB, Lambda, S3, Cognito, SES...<br>- Phân công nhiệm vụ cho từng thành viên.                          | 06/11/2025  | 06/11/2025     | —                                                 |
| 6        | - Hoàn thiện tài liệu Proposal.                                                                                                                                | 07/11/2025  | 07/11/2025     | —                                                 |

### Kết quả đạt được tuần 9:

**1. Hoàn thành tài liệu Proposal:**

- Tài liệu Proposal đầy đủ 3 phần chính: Problem Statement (vấn đề cần giải quyết), Solution Architecture (kiến trúc giải pháp), Cost Estimation (dự toán chi phí).
- Chi phí vận hành hệ thống được tính toán chi tiết bằng AWS Pricing Calculator, chứng minh Serverless tiết kiệm hơn so với Server truyền thống.
- Đề xuất công nghệ: DynamoDB (Database), Lambda (Backend Logic), API Gateway (RESTful API), Cognito (Authentication), S3 (Frontend Storage).

**2. Phân tích hệ thống chi tiết:**

- **Use Cases & User Stories:** Liệt kê đầy đủ các tình huống sử dụng cho 3 vai trò Admin, Lecturer và Student.
- **Flowchart nghiệp vụ:** Vẽ sơ đồ luồng cho 2 nghiệp vụ chính (Luồng đăng nhập với Cognito, Luồng nộp bài tập và chấm điểm).
- **Database Schema:** Thiết kế ERD cho DynamoDB theo Single Table Design pattern phù hợp với NoSQL.
- **API Endpoints:** Xác định danh sách API cần thiết cho Frontend gọi Backend.

---
