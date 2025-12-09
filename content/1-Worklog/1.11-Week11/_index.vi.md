---
title: "Worklog Tuần 11"
date: 2025-11-16
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

- Setup Project Frontend.
- Tích hợp Authentication (Cognito).
- Tham gia sự kiện DevOps.

### Các công việc cần triển khai trong tuần này:

| **Ngày** | **Nhiệm vụ**                                                                                                                   | **Bắt đầu** | **Hoàn thành** | **Tài liệu tham khảo**                                                                                          |
| -------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------- | -------------- | --------------------------------------------------------------------------------------------------------------- |
| 2        | - **EVENT:** Tham gia AWS Cloud Mastery Series #2 – DevOps on AWS.<br>- Tìm hiểu CI/CD (CodePipeline).                         | 18/11/2025  | 18/11/2025     | [AWS Cloud Mastery Series #2](../../4-eventparticipated/4.4-event4/)                                            |
| 3        | - Thiết kế Database Schema (DynamoDB JSON).<br>- Gửi thiết kế cho Backend team.                                                | 19/11/2025  | 19/11/2025     | [DynamoDB Best Practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html) |
| 4        | - Khởi tạo Project React + TypeScript (Vite).<br>- Config Tailwind, ESLint, Git repo.                                          | 20/11/2025  | 20/11/2025     | [Vite Guide](https://vitejs.dev/guide/) <br> [TypeScript Handbook](https://www.typescriptlang.org/docs/)        |
| 5        | - Code UI Login Page.<br>- Validate form với React Hook Form + Zod.                                                            | 21/11/2025  | 21/11/2025     | [React Hook Form](https://react-hook-form.com/get-started) <br> [Zod Validation](https://zod.dev/)              |
| 6        | - Cấu hình **Amazon Cognito** (User Pool).<br>- Tích hợp thư viện Amplify Auth.<br>- Nối API Login thành công (Lấy JWT Token). | 22/11/2025  | 22/11/2025     | [Amplify Authentication](https://docs.amplify.aws/react/build-a-backend/auth/)                                  |

### Kết quả đạt được tuần 11:

**1. Kiến thức DevOps trên AWS:**

- Tham gia **AWS Cloud Mastery Series #2** về DevOps on AWS, nắm được các dịch vụ CI/CD: **CodePipeline, CodeBuild, CodeDeploy**.
- Hiểu quy trình tự động hóa triển khai (Continuous Integration/Continuous Deployment) giúp tăng tốc phát triển và giảm lỗi.
- Áp dụng kiến thức vào dự án: Lên kế hoạch setup CI/CD pipeline để tự động deploy Frontend lên S3 + CloudFront.

**2. Khởi tạo và cấu hình Frontend Project:**

- Setup project **React + TypeScript** với **Vite** (build tool nhanh hơn Create React App).
- Cấu hình **Tailwind CSS** cho styling và **ESLint** cho code quality.
- Tạo Git repository và thiết lập branch strategy (main, develop, feature branches).

**3. Phát triển tính năng Authentication:**

- Code hoàn thiện **Login Page UI** với form validation sử dụng **React Hook Form** (performance tốt) và **Zod** (type-safe validation).
- Cấu hình **Amazon Cognito User Pool** để quản lý người dùng: Tạo User Pool, thiết lập password policy, email verification.
- Tích hợp **AWS Amplify Auth** library vào React app.
- **Kết nối thành công API Login**: Người dùng nhập email/password → Cognito xác thực → Trả về JWT Token → Lưu token vào localStorage để authenticate các API call tiếp theo.

**4. Kỹ năng Security:**

- Hiểu rõ luồng Authentication flow: Frontend (React) ↔ Cognito (Identity Provider) ↔ Backend (Lambda + API Gateway với Cognito Authorizer).
- Áp dụng **Secure Architectures** vào thực tế: Sử dụng Cognito làm Identity Management thay vì tự code authentication (bảo mật hơn, tuân thủ best practices).
- Nắm được cách làm việc với JWT Token và cách bảo vệ sensitive data trên Frontend.

---
