# Bài 3 - Database per Service

Hai Spring Boot service chạy độc lập và sử dụng hai database PostgreSQL riêng biệt:

- `user-service`: port `8081`, kết nối `user_db`, đọc bảng `users`.
- `inventory-service`: port `8082`, kết nối `inventory_db`, đọc bảng `products`.

## Chạy ứng dụng

Mở hai terminal tại thư mục gốc của bài tập:

```powershell
cd user-service
.\mvnw.cmd spring-boot:run
```

```powershell
cd inventory-service
.\mvnw.cmd spring-boot:run
```

PostgreSQL phải đang chạy tại `localhost:5432`. Trước khi chạy, cấu hình mật khẩu của từng database trong terminal tương ứng:

```powershell
$env:USER_DB_PASSWORD="<mật khẩu user_db>"
```

```powershell
$env:INVENTORY_DB_PASSWORD="<mật khẩu inventory_db>"
```

Mật khẩu chỉ được lưu trong biến môi trường cục bộ và không được commit vào Git.

## Kiểm tra API

```text
GET http://localhost:8081/api/v1/users
GET http://localhost:8082/api/v1/products
```

Hai API trả về toàn bộ bản ghi từ bảng tương ứng trong database riêng của service.
