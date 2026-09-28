# BÀI TẬP LẬP TRÌNH WEB

## Người thực hiện
Họ tên: Đinh Văn Trường
MSSV: K235480106074

## 1. Môi trường sử dụng
- Windows
- WSL 2
- Ubuntu
- Docker Engine
- Docker Compose

## 2. Các dịch vụ Docker
- Nginx
- Node-RED
- MariaDB
- phpMyAdmin
- Cloudflared

## 3. Hai website qua Nginx
Website 1:
http://site1.localhost:8080

Website 2:
http://site2.localhost:8080

Nginx sử dụng server_name để phân biệt hai website.

## 4. Node-RED API
API:
GET /api/students

Kết quả mẫu:
{
  "ok": 1,
  "msg": "thành công",
  "dssv": [
    {
      "name": "Dinh Van Truong",
      "money": 123
    },
    {
      "name": "David",
      "money": 456
    }
  ]
}

Flow:
HTTP IN -> FUNCTION -> HTTP RESPONSE

## 5. Website gọi API
Website 1 sử dụng JavaScript fetch('/api/students') để gọi API.

Nginx proxy đường dẫn /api/ sang Node-RED.

Luồng:
Browser -> Nginx -> Node-RED -> JSON

## 6. MariaDB và phpMyAdmin
Database: webdb

phpMyAdmin:
http://localhost:8081

## 7. Cloudflared
Cloudflared tạo tunnel từ Internet vào Nginx.

Luồng:
Internet -> Cloudflared -> Nginx -> Website / Node-RED API

URL trycloudflare.com là URL tạm và có thể thay đổi.

## 8. Cách chạy project
Khởi động:
docker compose up -d

Kiểm tra:
docker compose ps

Dừng:
docker compose down

## 9. Cấu trúc project
web-homework/
- docker-compose.yml
- README.md
- .gitignore
- nginx/default.conf
- nodered/
- website1/index.html
- website2/index.html

## 10. Kết quả
- WSL 2 và Ubuntu hoạt động.
- Docker và Docker Compose hoạt động.
- Nginx chạy 2 website.
- Node-RED cung cấp API.
- Website 1 dùng JavaScript gọi API.
- MariaDB và phpMyAdmin hoạt động.
- Cloudflared public website ra Internet.