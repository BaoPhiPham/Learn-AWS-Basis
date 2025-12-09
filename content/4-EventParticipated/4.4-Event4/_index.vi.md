---
title: "Sự kiện 4"
date: 2025-11-29
weight: 5
chapter: false
pre: "<b> 4.4. </b>"
---

# Bài thu hoạch: AWS Cloud Mastery Series #3 - ​Theo AWS Well-Architected Security Pillar

## Mục tiêu sự kiện

- Hiểu sâu về **Trụ cột Bảo mật (Security Pillar)** trong khung kiến trúc AWS Well-Architected.
- Nắm vững các nguyên tắc cốt lõi: **Đặc quyền tối thiểu (Least Privilege)**, **Zero Trust**, và **Phòng thủ chiều sâu (Defense in Depth)**.
- Học cách triển khai các biện pháp kiểm soát an ninh qua 5 lĩnh vực chính: Quản lý danh tính (IAM), Phát hiện, Bảo vệ hạ tầng, Bảo vệ dữ liệu, và Ứng phó sự cố.
- Nhận diện các mối đe dọa an ninh mạng phổ biến trong môi trường Cloud tại doanh nghiệp Việt Nam.

## Thời gian & Địa điểm

**Thời gian:** 08:30 – 12:00, Thứ Bảy, ngày 29/11/2025  
**Địa điểm:** Tầng 26, Tòa nhà tài chính Bitexco, 2 Đ. Hải Triều, Bến Nghé, Quận 1, TP. Hồ Chí Minh

## Diễn giả

- **Le Vu Xuan An** - Software & Cloud Engineer | AWS Cloud Club Captain HCMUTE
- **Tran Doan Cong Ly** - DevOps Engineer | AWS FCAJ Ambassador | AWS Cloud Club Captain PTIT
- **Danh Hoang Hieu Nghi** – AI Engineer, Renova Cloud | AWS First Cloud AI Journey | AWS Cloud Club Captain HUFLIT
- **Tran Duc Anh** - Cloud Security Engineer Trainee | First Cloud AI Journey | AWS Cloud Club Captain SGU
- **Nguyen Tuan Thinh** - Cloud Engineer Trainee | First Cloud AI Journey
- **Nguyen Do Thanh Dat** - Cloud Engineer Trainee | First Cloud AI Journey
- **Đinh Le Hoang Anh** – Cloud Engineer Trainee | First Cloud AI Journey
- **Kha Van** - Cloud Security Engineer | AWS Community Builders

**Special Guest:**

- **Mendel Grabski** - Cloud Security & Solution Architect | Enabling Secure-by-Design Solutions
- **Truong Quang Tinh** - DevOps Engineer, TymeX | AWS Community Builder

## Nội dung nổi bật

### 1. Nền tảng Bảo mật & Quản lý danh tính (IAM)

- **Nguyên tắc cốt lõi:** Chuyển dịch từ bảo mật chu vi (perimeter) sang mô hình **Zero Trust**, nơi mọi yêu cầu truy cập đều phải được xác thực và cấp quyền.
- **Kiến trúc IAM hiện đại:**
  - Loại bỏ việc sử dụng thông tin xác thực dài hạn (Access Keys) và thay thế bằng **IAM Roles** và **Identity Center (SSO)**.
  - Thực thi **Least Privilege** (Đặc quyền tối thiểu) và sử dụng Access Analyzer để kiểm tra policy.
  - Sử dụng **SCP (Service Control Policies)** để thiết lập ranh giới quyền hạn trong môi trường đa tài khoản (Multi-account).

### 2. Phát hiện & Giám sát liên tục

- **Tầm nhìn tập trung:** Sử dụng **Security Hub** để gom tất cả cảnh báo từ GuardDuty, Inspector và Macie về một nơi.
- **Chiến lược Logging:** Bắt buộc ghi log tại mọi tầng: Network (VPC Flow Logs), API (CloudTrail), và Storage (S3 Logs).
- **Detection-as-Code:** Định nghĩa các quy tắc phát hiện mối đe dọa bằng mã nguồn để đảm bảo tính nhất quán giữa các môi trường.

### 3. Bảo vệ Hạ tầng & Dữ liệu

- **An ninh mạng:** Áp dụng **Defense in Depth** với phân đoạn VPC (Private/Public subnets), Security Groups và WAF/Shield tại các điểm biên (edge).
- **Mã hóa:**
  - **Lưu trữ (At-rest):** Sử dụng KMS với cơ chế tự động xoay vòng khóa (key rotation) cho EBS, RDS, S3.
  - **Truyền tải (In-transit):** Bắt buộc sử dụng TLS 1.2+ cho mọi luồng dữ liệu.
- **Quản lý bí mật:** Thay thế thông tin đăng nhập (hardcoded credentials) trong code bằng **AWS Secrets Manager** hoặc **Parameter Store**.

### 4. Tự động hóa Ứng phó sự cố (Incident Response - IR)

- **Vòng đời IR:** Chuẩn bị → Phát hiện & Phân tích → Khoanh vùng, Xử lý & Khôi phục → Hoạt động sau sự cố.
- **Playbooks:** Quy trình mẫu xử lý các tình huống thực tế: lộ IAM key, S3 bucket bị public, phát hiện malware trên EC2.
- **Tự động hóa:** Sử dụng **Lambda** và **Step Functions** để tự động khắc phục (ví dụ: tự động thu hồi quyền của user bị xâm nhập).

## Bài học đúc kết

### Tư duy Bảo mật

- **Bảo mật là trách nhiệm của mọi người:** Không chỉ riêng đội Security, lập trình viên phải thực hành "Security by Design" ngay từ khi viết dòng code đầu tiên.
- **Tư duy "Assume Breach":** Luôn thiết kế hệ thống với giả định rằng một thành phần có thể bị xâm nhập, từ đó giới hạn "phạm vi ảnh hưởng" (blast radius).

### Kiến trúc Kỹ thuật

- **Identity là "bức tường lửa" mới:** Trong môi trường Cloud-native, việc quản lý IAM quan trọng hơn cả firewall mạng.
- **Hạ tầng bất biến (Immutable Infrastructure):** Hạn chế vá lỗi trực tiếp trên server; thay vào đó hãy thay thế bằng các server mới đã được vá lỗi để tránh malware ẩn mình.

### Ứng dụng vào công việc

- **Refactor IAM:** Rà soát ngay các IAM policy của dự án nhóm. Loại bỏ các quyền `*:*` dư thừa và thay thế hardcoded Access Keys bằng IAM Roles cho EC2/Lambda.
- **Bảo vệ Secrets:** Di chuyển các thông tin nhạy cảm (DB password, API Key) từ file `.env` lên **AWS Systems Manager Parameter Store**.
- **Kích hoạt GuardDuty:** Bật GuardDuty trên tài khoản dự án (tận dụng Free Tier) để phát hiện các hành vi bất thường như đào coin trái phép.
- **Mã hóa mặc định:** Bật Server-Side Encryption (SSE-S3) cho tất cả S3 bucket trong dự án Quản lý sinh viên.

## Trải nghiệm tham dự

Buổi workshop tập trung cao độ vào tính thực chiến của bảo mật đám mây. Khác với các buổi giới thiệu chung, sự kiện này cung cấp các **mô hình hành động cụ thể**:

- **Học tập tương tác:** Phần demo về Validate IAM Policy giúp em thấy rõ việc cấu hình sai quyền hạn dễ dàng xảy ra như thế nào.
- **Tính thực tế cao:** Việc thảo luận về "Top threats tại Việt Nam" làm nội dung trở nên rất gần gũi, nhấn mạnh sự cần thiết phải bảo vệ chống lại việc lộ lọt thông tin xác thực.
- **Tự động hóa:** Chứng kiến một Playbook IR được kích hoạt bởi EventBridge và xử lý bởi Lambda đã thay đổi hoàn toàn cách nhìn của em về việc vận hành bảo mật ở quy mô lớn.

## Hình ảnh sự kiện

![All members participated](/images/4-EventParticipated/Event5_1.jpg)
![Identity & Access Management](/images/4-EventParticipated/Event5_2.jpg)
![The Badging Journey](/images/4-EventParticipated/Event5_3.jpg)
![Multi Layer Security against Attack Vectors](/images/4-EventParticipated/Event5_4.jpg)
![Special Guest](/images/4-EventParticipated/Event5_5.jpg)

> Sự kiện này đã thay đổi tư duy của em từ "xây dựng nhanh" sang "xây dựng an toàn". Em đã có một lộ trình rõ ràng để gia cố bảo mật cho ứng dụng trước khi đưa vào môi trường production.
