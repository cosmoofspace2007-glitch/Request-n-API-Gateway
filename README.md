# Bài 2 - Định tuyến Request đến API Gateway

## Mục tiêu

Cấu hình Nginx sử dụng Path-based Routing để phục vụ
Frontend và Backend trên cùng một domain và port 80.

## Cấu hình định tuyến

- Request bắt đầu bằng /api/ được chuyển tới API Gateway tại localhost:8080.
- Các request còn lại được chuyển tới Frontend tại localhost:3000.

## Luồng hoạt động

/api/* → Nginx :80 → API Gateway :8080

/* → Nginx :80 → React :3000

## Header

Nginx truyền các header:

- Host
- X-Real-IP
- X-Forwarded-For
- X-Forwarded-Proto

## X-Forwarded-For

X-Forwarded-For được sử dụng để truyền IP của client
tới Backend thông qua Nginx.

Nếu không truyền X-Forwarded-For, Backend có thể chỉ
nhìn thấy IP của Nginx, ví dụ 127.0.0.1, thay vì IP
thực của client.
