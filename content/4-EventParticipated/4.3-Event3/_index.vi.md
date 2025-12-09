---
title: "Sự kiện 3"
date: 2025-11-17
weight: 4
chapter: false
pre: "<b> 4.3. </b>"
---

# Bài thu hoạch: AWS Cloud Mastery Series #2 – DevOps on AWS

## Mục tiêu sự kiện

- Hiểu rõ các nguyên tắc cốt lõi của văn hóa DevOps và các chỉ số hiệu suất chính (DORA).
- Làm chủ hệ sinh thái DevOps của AWS để xây dựng pipeline CI/CD hoàn chỉnh (end-to-end).
- So sánh và lựa chọn công cụ Infrastructure as Code (IaC) phù hợp (CloudFormation vs. AWS CDK).
- Khám phá các chiến lược container hóa sử dụng Amazon ECS, EKS và App Runner.
- Triển khai khả năng quan sát (Observability) toàn diện sử dụng CloudWatch và AWS X-Ray.

## Thời gian & Địa điểm

**Thời gian:** 08:30 – 17:00, Thứ Hai, 17 tháng 11  
**Địa điểm:** Tầng 26, Tòa nhà tài chính Bitexco, 2 Đ. Hải Triều, Bến Nghé, Quận 1, TP. Hồ Chí Minh

## Diễn giả

- **Truong Quang Tinh** - DevOps Engineer, TymeX | AWS Community Builder
- **Kha Van** - Cloud Security Engineer | AWS Community Builders
- **Bao Huynh** – AWS Community Builder
- **Thinh Nguyen** – AWS Community Builder
- **Vi Tran** – AWS Community Builder

## Nội dung nổi bật

### Văn hóa DevOps & Các chỉ số đo lường

- **Chuyển dịch văn hóa:** Chuyển từ việc phát triển (Dev) và vận hành (Ops) riêng biệt sang một văn hóa thống nhất với trách nhiệm được chia sẻ.
- **Các chỉ số chính (DORA):** Tập trung vào 4 chỉ số quan trọng để đo lường hiệu suất:
  - Tần suất triển khai (Deployment Frequency - DF)
  - Thời gian hoàn thành thay đổi (Lead Time for Changes - LT)
  - Thời gian trung bình để khôi phục (Mean Time to Restore - MTTR)
  - Tỷ lệ thay đổi thất bại (Change Failure Rate - CFR)

### Dịch vụ AWS DevOps – CI/CD Pipeline

- **Quản lý mã nguồn (Source Control):** Các chiến lược quản lý Git (GitFlow vs. Trunk-based development) sử dụng AWS CodeCommit.
- **Điều phối (Orchestration):** Tự động hóa quy trình phát hành với **AWS CodePipeline**.
- **Chiến lược triển khai (Deployment Strategies):**
  - **Blue/Green:** Giảm thiểu thời gian chết (downtime) và rủi ro bằng cách chạy hai môi trường song song.
  - **Canary:** Triển khai thay đổi cho một nhóm nhỏ người dùng trước.
  - **Rolling:** Cập nhật các instances dần dần theo từng đợt.

### Quản lý hạ tầng bằng mã (IaC)

- **AWS CloudFormation:** Phương pháp khai báo (declarative) sử dụng JSON/YAML template để định nghĩa hạ tầng; sử dụng tính năng phát hiện sai lệch (drift detection) để duy trì tính nhất quán.
- **AWS CDK (Cloud Development Kit):** Phương pháp mệnh lệnh (imperative) cho phép lập trình viên định nghĩa tài nguyên đám mây bằng ngôn ngữ lập trình quen thuộc (TypeScript, Python, Java). Các cấu trúc (constructs) của CDK cho phép tái sử dụng các mẫu hạ tầng.

### Dịch vụ Container & Khả năng quan sát (Observability)

- **Sự tiến hóa của tài nguyên tính toán:** Tiêu chí lựa chọn giữa **Amazon ECS** (kiểm soát chặt chẽ), **Amazon EKS** (chuẩn Kubernetes), và **AWS App Runner** (đơn giản hóa cho lập trình viên).
- **Observability:** Vượt xa việc giám sát đơn thuần bằng cách tích hợp **CloudWatch** (Logs, Metrics, Alarms) với **AWS X-Ray** để truy vết phân tán (distributed tracing), cho phép phân tích nguyên nhân gốc rễ trong microservices.

## Bài học đúc kết

### 1. Tư duy thiết kế

- **Tự động hóa là ưu tiên:** Các quy trình thủ công rất dễ gây lỗi; mọi thứ từ kiểm thử đến cung cấp hạ tầng đều cần được tự động hóa.
- **Bảo mật dịch chuyển sang trái (Shift-Left Security):** Tích hợp kiểm tra bảo mật ngay từ đầu pipeline CI/CD thay vì đợi đến cuối.
- **Đo lường mọi thứ:** Bạn không thể cải thiện những gì bạn không đo lường. DORA metrics là kim chỉ nam cho sự trưởng thành của DevOps.

### 2. Kiến trúc kỹ thuật

- **Hạ tầng bất biến (Immutable Infrastructure):** Máy chủ không bao giờ được sửa đổi sau khi triển khai; chúng sẽ được thay thế hoàn toàn bằng máy chủ mới.
- **Điều phối Pipeline:** Một pipeline mạnh mẽ phải bao gồm các bước build, unit test, integration test và các cổng phê duyệt (approval gates) trước khi lên production.
- **Khả năng truy vết (Traceability):** Trong hệ thống phân tán, việc tương quan giữa logs và traces (thông qua X-Ray) là bắt buộc để debug.

### 3. Chiến lược hiện đại hóa

- **Lựa chọn quy mô phù hợp (Right-sizing):** Sử dụng **App Runner** cho các web app đơn giản để giảm chi phí vận hành, và dành **EKS** cho các hệ thống microservices phức tạp cần điều phối cao.
- **Áp dụng IaC:** Chuyển từ việc thao tác tay trên console sang định nghĩa hạ tầng bằng code để đảm bảo khả năng tái tạo và phục hồi sau thảm họa.

## Ứng dụng vào công việc

- **Áp dụng Trunk-based Development:** Tinh gọn quy trình Git trong dự án nhóm để giảm xung đột khi merge code và tăng tốc độ tích hợp.
- **Triển khai CI/CD:** Xây dựng pipeline sử dụng **AWS CodePipeline** để tự động deploy backend quản lý sinh viên ngay khi push code lên nhánh chính.
- **Chuyển đổi sang IaC:** Refactor lại các thiết lập thủ công hiện tại của DynamoDB và Lambda functions thành các script **AWS CDK** để dễ bảo trì hơn.
- **Tăng cường giám sát:** Thiết lập **CloudWatch Alarms** cho các lỗi API nghiêm trọng (mã lỗi 5xx) để chủ động phát hiện sự cố trước buổi demo.

## Trải nghiệm tham dự

Tham dự buổi workshop **“DevOps on AWS”** là cầu nối quan trọng giúp em lấp đầy khoảng cách giữa việc viết code (Dev) và vận hành hệ thống (Ops). Sự kiện đã cung cấp một lộ trình rõ ràng để xây dựng các hệ thống tin cậy và có khả năng mở rộng. Những trải nghiệm chính bao gồm:

- **Học hỏi từ người thực chiến:** Các diễn giả là những AWS Community Builders tích cực, chia sẻ những "bài học xương máu" và các cạm bẫy thực tế trong DevOps chứ không chỉ là lý thuyết sách vở. Em đã hiểu rõ hơn về **Mô hình Trách nhiệm Chia sẻ** trong bối cảnh DevOps.
- **Tiếp cận kỹ thuật thực tế:**
  - Tham gia **live CI/CD walkthrough**, chứng kiến code thô được chuyển đổi thành ứng dụng hoàn chỉnh thông qua pipeline tự động chỉ trong vài phút.
  - Trải nghiệm sức mạnh của **AWS CDK** khi triển khai VPC và ECS cluster với số dòng code ít hơn đáng kể so với CloudFormation template thuần túy.
  - Trực quan hóa việc truy vết phân tán với **AWS X-Ray**, hiểu cách xác định điểm nghẽn (bottlenecks) trong microservices.
- **Kết nối và thảo luận:** Thảo luận về sự đánh đổi giữa **GitFlow** và **Trunk-based** development cho các nhóm nhỏ và nhận được hướng dẫn về lộ trình chứng chỉ **AWS Certified DevOps Engineer – Professional**.

### Bài học rút ra

- **IaC là không thể thương lượng:** Đối với bất kỳ dự án dài hạn nào, hạ tầng bắt buộc phải là code.
- **Observability là sống còn:** Xây dựng hệ thống chỉ là một nửa chặng đường; biết được hệ thống có "khỏe" hay không là nửa còn lại.
- **Văn hóa hơn công cụ:** Các công cụ như Jenkins hay CodePipeline sẽ vô dụng nếu thiếu văn hóa hợp tác và cải tiến liên tục.

## Hình ảnh sự kiện

![Warm-up with speaker Tinh Truong](/images/4-EventParticipated/Event4_1.jpg)
![Infrastructure as Code (IaC)](/images/4-EventParticipated/Event4_2.jpg)

> Tổng kết lại, sự kiện không chỉ cung cấp kỹ năng kỹ thuật về các công cụ AWS mà còn rèn luyện tư duy DevOps chuyên nghiệp, chuẩn bị cho em khả năng xây dựng các hệ thống chuẩn production một cách hiệu quả.
