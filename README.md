# 🥿 PVB Shop — Website Bán Giày Trực Tuyến

<p align="center">
  <img src="https://img.shields.io/badge/Laravel-8.x-FF2D20?style=flat-square&logo=laravel&logoColor=white"/>
  <img src="https://img.shields.io/badge/PHP-8.0+-777BB4?style=flat-square&logo=php&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat-square&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Tailwind_CSS-2.x-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
</p>

> Website thương mại điện tử bán giày trực tuyến, xây dựng bằng **Laravel 8** theo mô hình MVC. Hỗ trợ đầy đủ luồng mua hàng cho khách hàng và bảng điều khiển quản trị cho Admin.

---

## 📋 Mục lục

- [Tính năng](#-tính-năng)
- [Tech Stack](#-tech-stack)
- [Yêu cầu hệ thống](#-yêu-cầu-hệ-thống)
- [Cài đặt](#-cài-đặt)
- [Cấu hình](#-cấu-hình)
- [Tài khoản mặc định](#-tài-khoản-mặc-định)
- [Cấu trúc thư mục](#-cấu-trúc-thư-mục)
- [Cơ sở dữ liệu](#-cơ-sở-dữ-liệu)
- [Screenshots](#-screenshots)
- [Tác giả](#-tác-giả)

---

## ✨ Tính năng

### 👤 Khách hàng
| Tính năng | Mô tả |
|-----------|-------|
| Trang chủ | Banner slider, sản phẩm nổi bật, thương hiệu nổi tiếng |
| Cửa hàng | Duyệt & lọc sản phẩm theo loại giày, thương hiệu, giá |
| Chi tiết sản phẩm | Xem 4 ảnh, mô tả chi tiết, đánh giá từ khách hàng |
| Giỏ hàng | Thêm / xoá / cập nhật số lượng sản phẩm (session-based) |
| Thanh toán | Nhập thông tin giao nhận, chọn COD hoặc chuyển khoản |
| Tài khoản | Xem và chỉnh sửa thông tin cá nhân |
| Đánh giá | Gửi đánh giá sao và bình luận cho sản phẩm đã mua |

### 🔧 Quản trị viên (Admin)
| Tính năng | Mô tả |
|-----------|-------|
| Dashboard | Thống kê doanh thu tháng/năm, số lượng giày, khách hàng |
| Quản lý Giày | CRUD sản phẩm với upload tối đa 4 ảnh, DataTables |
| Quản lý Loại giày | Thêm / sửa / xoá loại giày (Thể thao, Sandal, Sneaker, Boots) |
| Quản lý Thương hiệu | Quản lý 8 thương hiệu (Nike, Adidas, Converse…) |
| Quản lý Khuyến mãi | Tạo chương trình giảm giá theo % |
| Xét duyệt Đơn hàng | Xem chi tiết hoá đơn JSON, xử lý đơn hàng |
| Quản lý Tài khoản | Thêm / sửa / xoá tài khoản người dùng |
| Quản lý Phân quyền | 3 cấp: Quản trị viên · Người dùng · Nhân viên |

---

## 🛠 Tech Stack

| Thành phần | Công nghệ |
|------------|-----------|
| **Backend** | PHP 8.0+, Laravel 8.x |
| **Auth** | Laravel Jetstream + Fortify |
| **Frontend** | Blade Templates, Tailwind CSS 2.x, Livewire |
| **Admin UI** | SB Admin 2 (Bootstrap 4) |
| **Database** | MySQL 5.7 / 8.0, Eloquent ORM |
| **Build tool** | NPM + Laravel Mix (Webpack) |
| **Package manager** | Composer 2.x |

---

## ⚙️ Yêu cầu hệ thống

- **PHP** >= 8.0 (extensions: BCMath, Ctype, Fileinfo, JSON, Mbstring, OpenSSL, PDO, Tokenizer, XML)
- **Composer** >= 2.0
- **Node.js** >= 14.x & **NPM** >= 6.x
- **MySQL** >= 5.7
- **Web server**: Apache 2.4 / Nginx (hoặc dùng `php artisan serve` khi phát triển)

---

## 🚀 Cài đặt

### 1. Clone repository

```bash
git clone https://github.com/<your-username>/laravel-shoes-shop.git
cd laravel-shoes-shop
```

### 2. Cài đặt dependencies PHP

```bash
composer install
```

### 3. Cài đặt dependencies JavaScript

```bash
npm install
npm run dev
```

### 4. Tạo file môi trường

```bash
cp .env.example .env
php artisan key:generate
```

### 5. Cấu hình database trong `.env`

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=pvb_shop
DB_USERNAME=root
DB_PASSWORD=
```

### 6. Chạy migration và seeder

```bash
# Tạo bảng
php artisan migrate

# Nhập dữ liệu mẫu (24 sản phẩm, 8 thương hiệu, 5 khuyến mãi...)
php artisan db:seed
```

### 7. Tạo symbolic link cho storage

```bash
php artisan storage:link
```

### 8. Khởi động server

```bash
php artisan serve
```

Truy cập: **http://127.0.0.1:8000**

---

## 🔧 Cấu hình

### Import database trực tiếp (tuỳ chọn)

Nếu muốn dùng file SQL có sẵn thay vì chạy seeder:

```bash
mysql -u root -p pvb_shop < ilyoushoesshop.sql
```

### Cấu hình Mail (cho chức năng quên mật khẩu)

```env
MAIL_MAILER=smtp
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=your@gmail.com
MAIL_PASSWORD=your_app_password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=your@gmail.com
MAIL_FROM_NAME="PVB Shop"
```

---

## 🔑 Tài khoản mặc định

Sau khi chạy seeder, hệ thống có sẵn các tài khoản sau:

| Tên đăng nhập | Mật khẩu | Vai trò |
|---------------|----------|---------|
| `admin` | `admin` | Quản trị viên (id_phan_quyen = 1) |
| `bang` | `123456789` | Người dùng |
| `bang2` | `123456789` | Người dùng |

> **Lưu ý:** Đăng nhập bằng **Tên đăng nhập** (không phải email). Tài khoản có `id_phan_quyen = 1` sẽ được chuyển tự động đến trang Admin.

---

## 📁 Cấu trúc thư mục

```
laravel-shoes-shop/
├── app/
│   ├── Http/
│   │   ├── Controllers/        # Controllers cho từng module
│   │   └── Middleware/         # Auth & role middleware
│   ├── Models/
│   │   ├── Giay.php            # Model sản phẩm giày
│   │   ├── DonHang.php         # Model đơn hàng
│   │   ├── KhuyenMai.php       # Model khuyến mãi
│   │   ├── LoaiGiay.php        # Model loại giày
│   │   ├── ThuongHieu.php      # Model thương hiệu
│   │   ├── DanhGia.php         # Model đánh giá
│   │   ├── PhanQuyen.php       # Model phân quyền
│   │   └── User.php            # Model người dùng
│   └── Providers/
├── database/
│   ├── migrations/             # Định nghĩa cấu trúc bảng
│   └── seeders/                # Dữ liệu mẫu
│       ├── GiaySeeder.php      # 24 sản phẩm giày
│       ├── ThuongHieuSeeder.php
│       ├── LoaiGiaySeeder.php
│       ├── KhuyenMaiSeeder.php
│       ├── PhanQuyenSeeder.php
│       └── TaiKhoanSeeder.php
├── public/
│   ├── images1/               # Ảnh giao diện (banner, logo)
│   ├── images2/               # Ảnh sản phẩm giày
│   └── css/ js/               # Assets đã build
├── resources/
│   └── views/
│       ├── admin/             # Giao diện Admin (SB Admin 2)
│       └── app/               # Giao diện khách hàng
├── routes/
│   └── web.php                # Định nghĩa toàn bộ routes
├── ilyoushoesshop.sql         # Database dump
└── .env.example
```

---

## 🗄 Cơ sở dữ liệu

Hệ thống sử dụng **12 bảng**, trong đó 8 bảng nghiệp vụ chính:

```
users           — Tài khoản người dùng
phan_quyen      — Vai trò phân quyền (Admin / User / Staff)
giay            — Sản phẩm giày (24 sản phẩm mẫu)
loai_giay       — Loại giày: Thể thao, Sandal, Sneaker, Boots
thuong_hieu     — Thương hiệu: Nike, Adidas, Converse, Gucci...
khuyen_mai      — Chương trình khuyến mãi
don_hang        — Đơn hàng (hoá đơn lưu dạng JSON)
danh_gia        — Đánh giá sản phẩm
```

---

## 📸 Screenshots

| Trang chủ | Trang thanh toán |
|-----------|-----------------|
| ![Home](public/images1/banner0.jpg) | *(Xem demo)* |

| Admin Dashboard | Trang tài khoản |
|-----------------|-----------------|
| *(Xem demo)* | *(Xem demo)* |

---

## 👤 Tác giả

**Phan Văn Bằng**

- 📧 Email: [pvbang@gmail.com](mailto:pvbang@gmail.com)
- 🎓 Trường: Đại học Công nghệ Thông tin và Truyền thông
- 📅 Năm: 2026

---

## 📄 License

Dự án được phát triển cho mục đích học tập — Tiểu luận môn **Công nghệ Phần mềm**.

Mã nguồn được phân phối theo giấy phép [MIT](LICENSE).

---

<p align="center">Made with ❤️ using Laravel 8</p>
