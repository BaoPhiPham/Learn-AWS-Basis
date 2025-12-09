---
title: "Sự kiện 2"
date: 2025-11-15
weight: 3
chapter: false
pre: "<b> 4.2. </b>"
---

# Bài thu hoạch: AWS Cloud Mastery Series #1 - ​AI/ML/GenAI on AWS

## Mục tiêu sự kiện

- Có cái nhìn toàn cảnh về thị trường AI/ML tại Việt Nam và hệ sinh thái dịch vụ của AWS.
- Hiểu rõ vòng đời phát triển Machine Learning toàn diện (End-to-end) sử dụng **Amazon SageMaker**.
- Khám phá năng lực của Generative AI với **Amazon Bedrock**, tập trung vào các Mô hình nền tảng (Foundation Models), RAG và Agents.
- Học các kỹ thuật Prompt Engineering thực tế để xây dựng ứng dụng tích hợp AI mà không cần kiến thức chuyên sâu về khoa học dữ liệu.

## Thời gian & Địa điểm

**Thời gian:** 08:30 – 12:00, Thứ Bảy, 18/11/2025  
**Địa điểm:** Tầng 26, Tòa nhà tài chính Bitexco, 2 Đ. Hải Triều, Bến Nghé, Quận 1, TP. Hồ Chí Minh

## Diễn giả

- **Đinh Le Hoang Anh** – Cloud Engineer Trainee, First Cloud AI Journey
- **Lam Tuan Kiet** – Sr. DevOps Engineer, FPT Software
- **Danh Hoang Hieu Nghi** – AI Engineer, Renova Cloud

## Nội dung nổi bật

### 1. Tổng quan về AWS AI/ML Services (SageMaker)

- **Nền tảng toàn diện:** Amazon SageMaker không chỉ dùng để training mà bao phủ toàn bộ vòng đời từ chuẩn bị dữ liệu (Data labeling), huấn luyện, tinh chỉnh đến triển khai và giám sát.
- **Tích hợp MLOps:** Tầm quan trọng của việc kết hợp quy trình ML với tư duy DevOps (CI/CD cho ML) để đảm bảo mô hình được triển khai ổn định và có khả năng mở rộng.
- **Live Demo:** Hướng dẫn trực quan trên **SageMaker Studio**, từ khâu gán nhãn dữ liệu đến khi expose ra một endpoint API.

### 2. Generative AI với Amazon Bedrock

- **Serverless GenAI:** Bedrock cho phép truy cập các mô hình ngôn ngữ lớn (Claude 3, Llama 3, Titan) thông qua API duy nhất mà không cần quản lý hạ tầng máy chủ.
- **Lựa chọn mô hình:** Hướng dẫn chọn model phù hợp dựa trên chi phí, độ trễ và khả năng suy luận (ví dụ: dùng Claude cho tác vụ phức tạp, Titan cho tác vụ tóm tắt đơn giản).
- **RAG (Retrieval-Augmented Generation):** Kiến trúc kết nối LLM với dữ liệu riêng của doanh nghiệp (Knowledge Base) để giảm thiểu ảo giác (hallucinations) và cung cấp câu trả lời chính xác theo ngữ cảnh.

### 3. Các tính năng GenAI nâng cao

- **Kỹ thuật Prompt Engineering:** Áp dụng tư duy chuỗi (Chain-of-Thought) và học từ vài mẫu (Few-shot learning) để điều hướng câu trả lời của AI.
- **Bedrock Agents:** Xây dựng quy trình làm việc đa bước, nơi AI có thể thực thi các API để thực hiện tác vụ (ví dụ: đặt lịch họp, tra cứu DB).
- **Guardrails:** Thiết lập các bộ lọc an toàn để ngăn chặn việc tạo ra nội dung độc hại hoặc không phù hợp.

## Bài học đúc kết (Key Takeaways)

### Tư duy thiết kế (Design Mindset)

- **Bình dân hóa AI (Democratization):** Không cần phải là Tiến sĩ Toán học mới làm được AI. Với các dịch vụ như Bedrock, kỹ sư phần mềm có thể tích hợp tính năng thông minh qua API.
- **Ngữ cảnh là vua (Context is King):** Một mô hình thông minh chung chung không giá trị bằng mô hình hiểu rõ dữ liệu doanh nghiệp. RAG là cầu nối giữa trí tuệ nhân tạo và giá trị thực tế.

### Kiến trúc kỹ thuật

- **Managed Services vs Self-hosted:** Với hầu hết các bài toán ứng dụng, sử dụng dịch vụ quản lý (Bedrock) tối ưu hơn về chi phí và bảo mật so với việc tự host model trên EC2.
- **An toàn là trên hết:** Ứng dụng AI bắt buộc phải có các lớp bảo vệ (Guardrails) kiểm soát đầu vào/đầu ra trước khi đến tay người dùng cuối.

### Ứng dụng vào công việc (Applying to Work)

- **Nghiên cứu kiến trúc RAG:** Tìm hiểu sâu hơn về cách hoạt động của RAG (Retrieval-Augmented Generation) để hiểu nguyên lý đằng sau các tính năng tìm kiếm tài liệu thông minh.
- **Nắm vững nguyên tắc bảo mật:** Ghi nhớ các quy tắc an toàn dữ liệu (như không gửi thông tin nhạy cảm lên public model) để áp dụng cho các dự án trong tương lai.
- **Bảo mật dữ liệu:** Đảm bảo dữ liệu sinh viên sử dụng cho RAG được mã hóa (KMS) và không bị sử dụng để train lại các public model.

## Trải nghiệm tham dự

Buổi workshop đã thành công trong việc giải mã thế giới phức tạp của AI/ML.

- **Góc nhìn đa chiều:** Sự kết hợp giữa góc nhìn vận hành (DevOps từ FPT) và góc nhìn mô hình (AI Engineer từ Renova).
- **Tính thực tiễn:** Phần Live Demo xây dựng Chatbot GenAI rất giá trị, chứng minh rằng việc tạo ra một sản phẩm AI (MVP) hiện nay chỉ mất vài giờ thay vì vài tháng.
- **Kết nối:** Hoạt động networking giúp em hiểu rõ hơn về nhu cầu thị trường đối với các lập trình viên có kỹ năng tích hợp AI (AI-literate developers).

## Hình ảnh sự kiện

![Setup](/images/4-EventParticipated/Event3_1.jpg)  
![Demo from speaker Dinh Le Hoang Anh](/images/4-EventParticipated/Event3_2.jpg)  
![Amazon Bedrock Agent Core](/images/4-EventParticipated/Event3_3.jpg)  
![Top 10 highest score in kahoot!](/images/4-EventParticipated/Event3_4.jpg)

> Sự kiện này là cầu nối quan trọng giữa phát triển phần mềm truyền thống và AI hiện đại. Nó khẳng định rằng tích hợp GenAI là bước đi tất yếu để nâng cao trải nghiệm người dùng trong các dự án em đang thực hiện.
