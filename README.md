# Thiết kế hệ thống (System Design) — Khóa học mô phỏng tương tác trực quan 📐✨

> **Bản Việt hóa & Lưu trữ độc lập (Self-hosted & Localized Vietnamese Edition)**  
> Giao diện mặc định: **Tiếng Việt** (vẫn có thể chuyển đổi giữa 20 ngôn ngữ khác trong menu).  
> Tác giả gốc: **Dilum Sanjaya** ([@DilumSanjaya](https://x.com/DilumSanjaya) / [dilum.dev](https://dilum.dev/))  
> Website gốc: [designed-to-scale.vercel.app](https://designed-to-scale.vercel.app/)

---

## 💡 Giới thiệu

**Thiết kế hệ thống (System Design)** là khóa học trực quan tương tác 1:1 giúp bạn hiểu sâu cách một hệ thống mở rộng từ **1 máy chủ đơn lẻ lên quy mô hàng triệu người dùng**.

Thay vì những biểu đồ tĩnh hoặc tài liệu chữ khô khan, từng khái niệm ở đây là một **mô hình hình học đẳng cự (isometric animated diagram)** mà bạn có thể trực tiếp bước qua từng phân cảnh:
- Bấm `Space` hoặc nút phát để xem luồng dữ liệu (request, response, ping, push, write) di chuyển thời gian thực.
- Theo dõi các chỉ số biến đổi theo từng bước: độ trễ (latency), thông lượng (throughput), số lượng server khỏe mạnh, tỷ lệ hit cache...
- Điều khiển phóng to/thu nhỏ, xem lại bước trước (`R`), chuyển chế độ sáng/tối (Light/Dark theme).

---

## 📚 Nội dung khóa học (40 bài học trong 9 học phần)

### 01. Nền tảng (Foundations)
- **Vòng đời một request (Request Lifecycle)**: DNS, TCP handshake, TLS, HTTP request/response.
- **Độ trễ & Thông lượng (Latency & Throughput)**: Phân biệt độ trễ mạng, băng thông và giới hạn xử lý.
- **Tính toán ước lượng (Napkin Math)**: Ước lượng tài nguyên CPU, RAM, ổ đĩa cần thiết cho quy mô lớn.

### 02. Mở rộng (Scaling)
- **Mở rộng dọc & ngang (Vertical & Horizontal Scaling)**: Nâng cấp phần cứng vs bổ sung node.
- **Cân bằng tải (Load Balancing)**: Round-robin, least connections, IP hash, health checks.
- **Bộ nhớ đệm (Caching)**: Cache-aside, write-through, write-back, chiến lược trục xuất (eviction: LRU/LFU).
- **Mạng phân phối nội dung (CDN)**: Edge caching, Anycast routing, giảm tải cho máy chủ gốc.
- **Phi trạng thái (Stateless Services)**: Quản lý session bên ngoài để dễ dàng co giãn.

### 03. Dữ liệu & Lưu trữ (Data & Storage)
- **SQL vs NoSQL**: Lựa chọn giữa schema ràng buộc (ACID) và khả năng mở rộng linh hoạt (BASE).
- **Chỉ mục (Indexes)**: B-Tree indexes, chỉ mục ghép (composite), chi phí quét toàn bảng vs tra cứu cây.
- **Động cơ lưu trữ (Storage Engines)**: B-Trees (đọc nhanh) vs LSM Trees (ghi nhanh).
- **Nhân bản (Replication)**: Master-slave, multi-master, đồng bộ (sync) vs bất đồng bộ (async).
- **Phân mảnh (Sharding)**: Range sharding, hash sharding, rebalancing, lookup directory.
- **Băm nhất quán (Consistent Hashing)**: Hash ring, virtual nodes giúp thêm/bớt node mà ít xáo trộn dữ liệu.
- **Định lý CAP (CAP Theorem)**: Cân bằng giữa Tính nhất quán (Consistency), Tính khả dụng (Availability) và Khả năng chịu lỗi phân vùng (Partition Tolerance).

### 04. Giao tiếp (Communication)
- **Giao diện lập trình (APIs)**: So sánh REST, RPC (gRPC), GraphQL, WebSockets.
- **Hàng đợi thông điệp (Queues)**: Xử lý bất đồng bộ, đệm tải đỉnh (burst), worker pool.
- **Mô hình Xuất bản / Đăng ký (Pub/Sub)**: Fan-out event, giải phóng sự phụ thuộc giữa các dịch vụ.
- **Giao tiếp thời gian thực (Real-time)**: Polling, Long-polling, Server-Sent Events (SSE), WebSockets.

### 05. Độ tin cậy (Reliability)
- **Dư thừa & Dự phòng (Redundancy & Failover)**: Active-passive, active-active, heartbeat.
- **Thời gian chờ & Thử lại (Timeouts & Retries)**: Exponential backoff, jitter, ngắt mạch (Circuit Breaker).
- **Giới hạn tốc độ (Rate Limiting)**: Token bucket, leaky bucket, sliding window counter.
- **Khả năng quan sát (Observability)**: Metrics, Structured Logging, Distributed Tracing.

### 06. Kiến trúc (Architecture)
- **Microservices**: Tách rời khối nguyên khối (monolith), bounded context, API Gateway.
- **Khám phá dịch vụ (Service Discovery)**: Client-side vs Server-side discovery, service registry.
- **Giao dịch phân tán (Distributed Transactions)**: Two-Phase Commit (2PC) và Saga pattern (Choreography / Orchestration).

### 07. Bảo mật (Security)
- **Xác thực (Authentication)**: Sessions, JWT, OAuth2, OpenID Connect.
- **Phân quyền (Authorization)**: RBAC (vai trò), ABAC (thuộc tính), ACL.
- **Mã hóa (Encryption)**: Encryption in transit (TLS 1.3), encryption at rest (AES-GCM, KMS).

### 08. Vận hành & Triển khai (Shipping)
- **Kiểm thử phân tán (Testing)**: Unit test, Integration test, Chaos engineering, Load test.
- **CI/CD**: Tự động hóa build, test, lint, đóng gói container.
- **Chiến lược triển khai (Deployments)**: Blue-Green deployment, Canary releases, Rolling updates.

### 09. Thiết kế hệ thống thực tế (Whole Systems)
- **HLD vs LLD**: Cách tiếp cận bản vẽ cấp cao (High-Level) và chi tiết (Low-Level).
- **Tạo ID duy nhất toàn cầu (Unique IDs)**: UUID v4/v7, Twitter Snowflake, database sequence.
- **Lưu trữ tệp tin (File Storage)**: Object storage (S3), chunking, multipart upload, pre-signed URLs.
- **Thiết kế dịch vụ rút gọn URL (URL Shortener - TinyURL)**: Hashing Base62, caching, counter, counter drift.
- **Thiết kế Bảng tin mạng xã hội (News Feed)**: Fan-out on write vs Fan-out on read, hybrid approach.
- **Thiết kế Hệ thống Trò chuyện trực tuyến (Chat App)**: Quản lý kết nối WebSocket, status presence, tin nhắn ngoại tuyến.

---

## 🚀 Hướng dẫn chạy thử cục bộ (Local Run)

Dự án là một ứng dụng web tĩnh hoàn toàn (Pure static SPA) không cần build phức tạp:

```bash
# Sử dụng Python
python -m http.server 8080

# Hoặc sử dụng Node.js (npx)
npx serve .
```

Sau đó mở trình duyệt tại: `http://localhost:8080`

---

## 🌐 Triển khai lên GitHub Pages

Kho lưu trữ đã được tích hợp sẵn file GitHub Actions workflow `.github/workflows/deploy.yml`:
1. Vào repository trên GitHub -> **Settings** -> **Pages**.
2. Tại mục **Build and deployment** > **Source**, chọn **GitHub Actions**.
3. Mỗi khi push code lên nhánh `main`, hệ thống sẽ tự động build và xuất bản ra website GitHub Pages miễn phí.

---

## 📜 Giấy phép & Lời cảm ơn

- Khóa học gốc được tạo bởi tác giả **Dilum Sanjaya** ([designedtoscale.app](https://designedtoscale.app/)).
- Phiên bản này được lưu trữ phục vụ mục đích học tập, nghiên cứu và phổ cập kiến thức kỹ thuật hệ thống cho cộng đồng lập trình viên Việt Nam.
