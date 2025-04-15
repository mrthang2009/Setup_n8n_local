# Hướng dẫn cài đặt và sử dụng n8n

n8n là một nền tảng tự động hóa workflow mạnh mẽ giúp bạn kết nối các dịch vụ và ứng dụng khác nhau. Hướng dẫn này sẽ giúp bạn cài đặt và chạy n8n trên máy tính cá nhân.

## Mục lục

- [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)
- [Cài đặt NVM (Node Version Manager)](#cài-đặt-nvm-node-version-manager)
- [Cài đặt Node.js](#cài-đặt-nodejs)
- [Cài đặt n8n](#cài-đặt-n8n)
- [Chạy n8n](#chạy-n8n)
- [Khắc phục lỗi thường gặp](#khắc-phục-lỗi-thường-gặp)
- [Sử dụng n8n cơ bản](#sử-dụng-n8n-cơ-bản)
- [Chạy n8n như một dịch vụ](#chạy-n8n-như-một-dịch-vụ)

## Yêu cầu hệ thống

- Hệ điều hành: Windows, macOS, hoặc Linux
- RAM: tối thiểu 2GB (khuyến nghị 4GB trở lên)
- Ổ cứng: tối thiểu 1GB dung lượng trống

## Cài đặt NVM (Node Version Manager)

NVM cho phép bạn dễ dàng cài đặt và quản lý nhiều phiên bản Node.js.

### Windows

1. Tải NVM cho Windows từ: https://github.com/coreybutler/nvm-windows/releases
2. Tải file `nvm-setup.exe`
3. Chạy file cài đặt và làm theo hướng dẫn
4. Mở Command Prompt (CMD) để kiểm tra cài đặt:
   ```
   nvm version
   ```

### macOS/Linux

1. Mở Terminal
2. Chạy lệnh sau:
   ```
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
   ```
3. Đóng và mở lại Terminal
4. Kiểm tra cài đặt:
   ```
   nvm --version
   ```

## Cài đặt Node.js

n8n hoạt động tốt nhất với Node.js phiên bản 18.x hoặc 20.x.

1. Mở Command Prompt (Windows) hoặc Terminal (macOS/Linux)
2. Cài đặt Node.js phiên bản 18.19.0 (khuyến nghị):
   ```
   nvm install 18.19.0
   ```
3. Sử dụng phiên bản vừa cài đặt:
   ```
   nvm use 18.19.0
   ```
4. Đặt làm phiên bản mặc định:
   ```
   nvm alias default 18.19.0
   ```
5. Kiểm tra Node.js đã cài đặt thành công:
   ```
   node -v
   ```
   Kết quả sẽ hiển thị: `v18.19.0`
6. Kiểm tra npm:
   ```
   npm -v
   ```

## Cài đặt n8n

1. Mở Command Prompt hoặc Terminal
2. Cài đặt n8n toàn cục:
   ```
   npm install n8n -g
   ```
3. Đợi quá trình cài đặt hoàn tất (có thể mất vài phút)

## Chạy n8n

1. Mở Command Prompt hoặc Terminal
2. Chạy lệnh:
   ```
   n8n start
   ```
3. Đợi n8n khởi động (bạn sẽ thấy thông báo khởi động thành công)
4. Mở trình duyệt web và truy cập: http://localhost:5678

## Khắc phục lỗi thường gặp

### 'nvm' không được nhận diện

- Đảm bảo bạn đã cài đặt NVM đúng cách
- Khởi động lại máy tính và thử lại
- Kiểm tra biến môi trường PATH có chứa đường dẫn đến NVM không

### 'node' hoặc 'npm' không được nhận diện

- Chạy lại lệnh `nvm use 18.19.0`
- Kiểm tra xem đã cài đặt Node.js chưa bằng `nvm list`
- Nếu chưa cài đặt, chạy `nvm install 18.19.0`

### Lỗi khi cài đặt n8n

- Thử cài đặt với quyền quản trị:
  - Windows: Chạy CMD với quyền Administrator
  - macOS/Linux: Thêm `sudo` ở đầu lệnh (ví dụ: `sudo npm install n8n -g`)

### n8n không thể khởi động

- Kiểm tra xem cổng 5678 đã được sử dụng chưa
- Chạy n8n với cổng khác: `n8n start --port=5679`
- Kiểm tra xem phiên bản Node.js có hợp lệ không (18.x hoặc 20.x)

## Sử dụng n8n cơ bản

1. Truy cập giao diện web n8n: http://localhost:5678
2. Tạo tài khoản quản trị khi được yêu cầu
3. Tạo workflow mới:
   - Nhấn nút "+ New" hoặc "Create New Workflow"
   - Đặt tên cho workflow
4. Thêm node vào workflow:
   - Nhấn nút "+" trong khu vực canvas
   - Tìm kiếm và chọn node bạn muốn sử dụng
5. Cấu hình node:
   - Nhấp vào node để mở cài đặt
   - Điền các thông tin cần thiết
6. Kết nối các node:
   - Kéo từ điểm kết nối (nút tròn) của node này đến node khác
7. Lưu workflow:
   - Nhấn nút "Save" ở góc trên phải
8. Chạy workflow:
   - Nhấn "Execute Workflow" để chạy thử

## Chạy n8n như một dịch vụ

Nếu bạn muốn n8n chạy liên tục, ngay cả khi đóng terminal, bạn có thể sử dụng PM2:

### Cài đặt PM2

```
npm install pm2 -g
```

### Khởi động n8n với PM2

```
pm2 start n8n
```

### Thiết lập khởi động cùng hệ thống

```
pm2 startup
```

Sau đó chạy lệnh được hiển thị (nếu có)

### Lưu cấu hình

```
pm2 save
```

### Kiểm tra trạng thái

```
pm2 status
```

### Dừng n8n

```
pm2 stop n8n
```

---

## Lưu ý quan trọng

- Dữ liệu của n8n được lưu trong thư mục `.n8n` trong thư mục người dùng của bạn
- Đường dẫn trên Windows: `C:\Users\<username>\.n8n`
- Đường dẫn trên macOS/Linux: `~/.n8n`
- Nên sao lưu thư mục này để tránh mất dữ liệu

---

Việc cài đặt n8n đã hoàn tất! Bây giờ bạn có thể bắt đầu tạo các workflow tự động để nâng cao hiệu quả công việc của mình.
