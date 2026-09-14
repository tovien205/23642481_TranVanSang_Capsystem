# Tài liệu Tích hợp API - CAB System (MVP)

Tài liệu này ánh xạ các Yêu cầu Chức năng (Functional Requirements) sang các API Endpoints tương ứng của hệ thống.

## 1. Đặt Xe & Điều Phối (Booking & Dispatch)
| File | Endpoint | Method | Mô tả (Chức năng) |
| :--- | :--- | :---: | :--- |
| `fr01_booking.yaml` | `/api/v1/bookings` | **POST** | Tạo chuyến đi mới (FR-MATCH-01) |
| `fr02_dispatch.yaml` | `/api/v1/dispatch/match` | **POST** | Thuật toán quét và gán tài xế gần nhất (FR-MATCH-02, 03) |
| `fr02_dispatch.yaml` | `/api/v1/dispatch/respond` | **PUT** | Tài xế chấp nhận/từ chối chuyến đi (FR-MATCH-04) |

## 2. Quản lý Chuyến đi & Tracking (Trip Lifecycle)
| File | Endpoint | Method | Mô tả (Chức năng) |
| :--- | :--- | :---: | :--- |
| `fr03_tracking.yaml` | `/api/v1/tracking/{tripId}` | **GET** | Lấy tọa độ GPS realtime của tài xế (FR-TRIP-02) |
| `fr04_trip_lifecycle.yaml`| `/api/v1/trips/{tripId}/status` | **PATCH**| Cập nhật tiến độ: *Đang đến, Đã đón, Hoàn thành* (FR-TRIP-01) |

## 3. Tính Cước & Thanh Toán (Pricing & Payment)
| File | Endpoint | Method | Mô tả (Chức năng) |
| :--- | :--- | :---: | :--- |
| `fr05_pricing.yaml` | `/api/v1/pricing/estimate` | **POST** | Tính giá cước dự kiến trước khi đặt (FR-PAY-01) |
| `fr06_payment.yaml` | `/api/v1/payments` | **POST** | Xử lý thanh toán điện tử / Xác nhận tiền mặt (FR-PAY-02, 03) |

## 4. Đánh Giá (Rating)
| File | Endpoint | Method | Mô tả (Chức năng) |
| :--- | :--- | :---: | :--- |
| `fr07_notification.yaml`| `/api/v1/trips/{tripId}/rating` | **POST** | Khách hàng đánh giá chuyến đi (FR-RATING-01) |
