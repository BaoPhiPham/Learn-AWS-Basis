---
title: "Worklog Tuần 12"
date: 2025-11-23
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12:

- Phát triển UI Admin Dashboard.
- Tìm hiểu Security nâng cao (WAF, Shield).

### Các công việc cần triển khai trong tuần này:

| **Ngày** | **Nhiệm vụ**                                                                                  | **Bắt đầu** | **Hoàn thành** | **Tài liệu tham khảo**                                                                                                 |
| -------- | --------------------------------------------------------------------------------------------- | ----------- | -------------- | ---------------------------------------------------------------------------------------------------------------------- |
| 2        | - Code Layout Admin (Sidebar, Header).<br>- Xây dựng các Reusable Components.                 | 24/11/2025  | 25/11/2025     | [React Component Patterns](https://react.dev/learn/passing-props-to-a-component)                                       |
| 3        | - Code màn hình Dashboard Overview.<br>- Code màn hình Quản lý sinh viên (Table, Pagination). | 26/11/2025  | 27/11/2025     | —                                                                                                                      |
| 4        | - Hoàn thiện UI Admin (Responsive).<br>- Hoàn thành giao diện Admin (Mock data).              | 28/11/2025  | 28/11/2025     | —                                                                                                                      |
| 5        | - **EVENT:** Tham gia AWS Cloud Mastery Series #3 – Cloud Security Best Practices.            | 29/11/2025  | 29/11/2025     | [AWS Cloud Mastery Series #3](../../4-eventparticipated/4.5-event5/)                                                   |
| 6        | - Refactor code, tối ưu Performance Frontend.<br>- Chuẩn bị tích hợp API.                     | 30/11/2025  | 30/11/2025     | [React Performance Optimization](https://react.dev/learn/render-and-commit) <br> [Web Vitals](https://web.dev/vitals/) |

### Kết quả đạt được tuần 12:

**1. Phát triển giao diện Admin Dashboard:**

- Xây dựng hoàn chỉnh **Admin Layout** với Sidebar (navigation menu), Header (user profile, notifications).
- Code **Dashboard Overview** hiển thị số liệu tổng quan: Tổng số sinh viên, số bài tập, tỷ lệ hoàn thành, biểu đồ thống kê.
- Phát triển **màn hình Quản lý sinh viên** với Table (hiển thị danh sách), Pagination (phân trang), Search/Filter (tìm kiếm theo tên, lớp), CRUD actions (Thêm/Sửa/Xóa).
- Thiết kế **Responsive**: Giao diện tự động điều chỉnh trên Desktop, Tablet, Mobile.

**2. Kiến trúc Component & Code Quality:**

- Xây dựng **Reusable Components** tái sử dụng được.
- **Refactor code** để tối ưu: Loại bỏ code trùng lặp, tổ chức folder structure rõ ràng (components/, pages/, hooks/, utils/).
- Mock data để test UI trước khi Backend API sẵn sàng.

**3. Kiến thức AWS Security nâng cao:**

- Tham gia **AWS Cloud Mastery Series #3** về Cloud Security Best Practices, học được các dịch vụ bảo mật: **AWS WAF** (Web Application Firewall), **AWS Shield** (DDoS Protection).
- Hiểu cách WAF bảo vệ ứng dụng Web khỏi các cuộc tấn công phổ biến: **SQL Injection, XSS (Cross-Site Scripting), CSRF**.
- Nắm được cách cấu hình WAF Rules để filter malicious requests, rate limiting để chống brute force attacks.
- Áp dụng vào dự án: Lên kế hoạch tích hợp WAF với CloudFront để bảo vệ Frontend, Shield Standard (miễn phí) để chống DDoS cơ bản.

---
