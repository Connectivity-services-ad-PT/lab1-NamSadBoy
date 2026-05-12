# Service Boundary của nhóm

## 1. Thông tin nhóm

- Tên nhóm: 7a
- Lớp: CNTT 17-10
- Thành viên: Nguyễn Trọng Nam, Trần Quang Huy, Phạm Hoàng Anh
- Service nhóm phụ trách: Core
- Sản phẩm tổng thể của lớp:

## 2. Actor

Ai tương tác với hệ thống/service?

- Client/Web Application
- API Gateway
- Các service khác trong hệ thống

## 3. System Boundary

Nhóm em xây phần nào?

Phần nhóm kiểm soát:

- Xử lý logic nghiệp vụ cốt lõi của hệ thống
- Quản lý dữ liệu chính (core entities)
- Cung cấp các API cơ bản cho các service khác

Phần nhóm chỉ tích hợp:

- Giao tiếp với các service khác qua API
- Sử dụng shared infrastructure (cache, message queue)

## 4. Service Boundary

Service của nhóm có trách nhiệm gì?

- Quản lý các entity cốt lõi của hệ thống
- Xử lý business logic chính
- Cung cấp API cho các service khác sử dụng
- Đảm bảo tính toàn vẹn dữ liệu

Service KHÔNG làm gì?

- KHÔNG xử lý logic riêng của các service khác
- KHÔNG quản lý dữ liệu không thuộc service này
- KHÔNG gửi trực tiếp response cho end user (thông qua API Gateway)

## 5. Input / Output

### Input

- Request API từ các service khác
- Dữ liệu từ các service khi thực hiện tích hợp
- Yêu cầu từ API Gateway

### Output

- Response API với dữ liệu entity cốt lõi
- Event/Message gửi đến message queue
- Status code và error message

## 6. API dự kiến

| Method | Endpoint | Mục đích |
|---|---|---|
| GET | /health | Kiểm tra service |
| GET | /core/entities | Lấy danh sách entity cốt lõi |
| GET | /core/entities/{id} | Lấy chi tiết entity |
| POST | /core/entities | Tạo mới entity |
| PUT | /core/entities/{id} | Cập nhật entity |
| DELETE | /core/entities/{id} | Xóa entity |

## 7. Phụ thuộc service khác

Service này gọi đến service nào?

- (Tùy thuộc vào architecture, có thể gọi các service phụ trợ)

Service nào gọi đến service này?

- Tất cả các service khác trong hệ thống cần dữ liệu cốt lõi

## 8. Sơ đồ minh họa

Có thể vẽ bằng Mermaid, draw.io, Ludichart hoặc ảnh chụp sơ đồ.

https://drive.google.com/file/d/1o2iXMi9G1Sk014C2BqxBB5cTVBl2WzfI/view?usp=sharing
