---
title: "Worklog Tuần 13"
date: 2025-12-01
weight: 13
chapter: false
pre: " <b> 1.13. </b> "
---

### Mục tiêu tuần 13:

- Tích hợp Backend (API Gateway).
- Implement Realtime Chat (AppSync).

### Các công việc cần triển khai trong tuần này:

| **Ngày** | **Nhiệm vụ**                                                                                                                                                                                                                | **Bắt đầu** | **Hoàn thành** | **Tài liệu tham khảo**                                                                                                                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2        | - Kết nối API Gateway (REST).<br>- Xử lý lỗi CORS.                                                                                                                                                                          | 02/12/2025  | 02/12/2025     | [CORS in API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html) <br> [Axios Documentation](https://axios-http.com/docs/intro)                                                   |
| 3        | - Tích hợp CRUD Sinh viên:<br>&emsp;+ Create (Thêm sinh viên mới)<br>&emsp;+ Read (Lấy danh sách/chi tiết)<br>&emsp;+ Update (Cập nhật thông tin)<br>&emsp;+ Delete (Xóa sinh viên)<br>- Xử lý state loading/error trên UI. | 03/12/2025  | 03/12/2025     | [React Query](https://tanstack.com/query/latest) <br> [Error Handling Best Practices](https://kentcdodds.com/blog/use-react-error-boundary-to-handle-errors-in-react)                                                |
| 4        | - **Trọng tâm:** Tích hợp **AWS AppSync**.<br>- Cấu hình GraphQL Client.<br>- Viết Query/Mutation cho Chat:<br>&emsp;+ Query: Lấy lịch sử chat<br>&emsp;+ Mutation: Gửi tin nhắn                                            | 04/12/2025  | 04/12/2025     | [Amplify GraphQL](https://docs.amplify.aws/react/build-a-backend/graphqlapi/) <br> [AWS AppSync](https://docs.aws.amazon.com/appsync/latest/devguide/what-is-appsync.html)                                           |
| 5        | - Xử lý GraphQL Subscription (Realtime).<br>- Test chat giữa 2 user thành công:<br>&emsp;+ User A gửi tin nhắn<br>&emsp;+ User B nhận realtime ngay lập tức                                                                 | 05/12/2025  | 05/12/2025     | [GraphQL Subscriptions](https://docs.amplify.aws/react/build-a-backend/graphqlapi/subscribe-data/) <br> [WebSocket Connections](https://docs.aws.amazon.com/appsync/latest/devguide/real-time-websocket-client.html) |
| 6        | - Refactor code Frontend.<br>- Optimize Performance (lazy loading, memoization).<br>- Viết documentation cho code.                                                                                                          | 06/12/2025  | 06/12/2025     | [React Performance](https://react.dev/learn/render-and-commit) <br> [Code Documentation](https://jsdoc.app/)                                                                                                         |

### Kết quả đạt được tuần 13:

**1. Kết nối API thành công:**

- Kết nối được Frontend với API Gateway do Backend team làm.
- Xử lý được lỗi CORS bằng cách làm việc với Backend team.
- Xây dựng API service với Axios, tự động thêm JWT Token vào header.
- Làm được loading spinner và error notification khi call API.

**2. Hoàn thành giao diện CRUD Sinh viên:**

- Làm form thêm/sửa sinh viên với validation.
- Hiển thị danh sách sinh viên với bảng có phân trang và tìm kiếm.
- Làm được xóa sinh viên với modal xác nhận.
- Dùng React Query để quản lý data và tự động refresh sau khi thay đổi.

**3. Tích hợp được Realtime Chat:**

- Setup GraphQL Client để kết nối với AppSync.
- Viết Query để lấy tin nhắn cũ và Mutation để gửi tin nhắn mới.
- Làm được Subscription để nhận tin nhắn realtime qua WebSocket.
- Test thành công: 2 user nhắn tin cho nhau, tin nhắn hiện ngay không cần reload trang.
- Đây là phần khó nhất vì phải hiểu GraphQL và WebSocket.

**4. Học được:**

- Cách tích hợp Frontend với REST API và GraphQL API.
- Phân biệt được khi nào dùng REST (CRUD) và khi nào dùng GraphQL (Realtime).
- Dùng DevTools để debug API calls.
- Làm việc nhóm với Backend team để xử lý vấn đề CORS và test End-to-End.

---
