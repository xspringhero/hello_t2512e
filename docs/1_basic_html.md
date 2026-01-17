# HƯỚNG DẪN CƠ BẢN VỀ CÁC THẺ HTML TRONG LẬP TRÌNH WEB

HTML (HyperText Markup Language) là ngôn ngữ đánh dấu tiêu chuẩn để tạo nên cấu trúc của một trang web. Tài liệu này cung cấp cái nhìn tổng quan về các thẻ (tags) cơ bản và cách sử dụng chúng trong thực tế.

---

### 1. Cấu trúc một tài liệu HTML tiêu chuẩn

Mọi tệp HTML đều bắt đầu bằng một cấu trúc khung để trình duyệt có thể nhận diện và hiển thị chính xác.

```html
<!DOCTYPE html> <!-- Khai báo loại tài liệu là HTML5 -->
<html lang="vi"> <!-- Ngôn ngữ chính của trang web -->
<head>
    <meta charset="UTF-8"> <!-- Định dạng mã hóa ký tự (hỗ trợ tiếng Việt) -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tiêu đề trang web</title> <!-- Hiển thị trên tab trình duyệt -->
</head>
<body>
    <!-- Nội dung hiển thị của trang web sẽ nằm ở đây -->
</body>
</html>
```

---

### 2. Các thẻ định dạng văn bản

Văn bản là thành phần cốt lõi của website. HTML cung cấp các thẻ để phân cấp nội dung từ tiêu đề đến đoạn văn.

*   **Thẻ tiêu đề (Headings):** Có 6 cấp độ từ `<h1>` đến `<h6>`. `<h1>` là quan trọng nhất và thường dùng cho tiêu đề chính.
*   **Thẻ đoạn văn (`<p>`):** Dùng để nhóm các dòng văn bản lại với nhau.
*   **Thẻ xuống dòng (`<br>`) và Thẻ đường kẻ ngang (`<hr>`).**

```html
<h1>Đây là tiêu đề cấp 1</h1>
<h2>Đây là tiêu đề cấp 2</h2>
<p>Đây là một đoạn văn bản mô tả nội dung. HTML tự động tạo khoảng cách giữa các đoạn văn.</p>
<hr> <!-- Tạo một đường kẻ ngang ngăn cách nội dung -->
<p>Dòng thứ nhất.<br>Dòng thứ hai (đã xuống dòng).</p>
```

---

### 3. Thẻ liên kết (Links) và Hình ảnh (Images)

Khả năng kết nối giữa các trang và hiển thị đa phương tiện là đặc điểm quan trọng của web.

*   **Thẻ liên kết (`<a>`):** Sử dụng thuộc tính `href` để chỉ định đích đến.
*   **Thẻ hình ảnh (`<img>`):** Là thẻ tự đóng, sử dụng thuộc tính `src` (nguồn ảnh) và `alt` (văn bản thay thế).

```html
<!-- Liên kết đến trang web khác -->
<a href="https://www.google.com" target="_blank">Truy cập Google (mở trong tab mới)</a>

<!-- Hiển thị hình ảnh -->
<img src="path/to/image.jpg" alt="Mô tả hình ảnh cho trình đọc màn hình" width="300">
```

---

### 4. Thẻ Danh sách (Lists)

Dùng để liệt kê thông tin theo dạng có thứ tự hoặc không có thứ tự.

*   **Danh sách không thứ tự (`<ul>`):** Hiển thị với các dấu chấm đầu dòng.
*   **Danh sách có thứ tự (`<ol>`):** Hiển thị với các con số hoặc ký tự.
*   **Phần tử danh sách (`<li>`):** Nằm bên trong thẻ `<ul>` hoặc `<ol>`.

```html
<ul>
    <li>Phần tử 1</li>
    <li>Phần tử 2</li>
</ul>

<ol>
    <li>Bước 1: Cài đặt</li>
    <li>Bước 2: Thực thi</li>
</ol>
```

---

### 5. Thẻ Khối (Containers)

Đây là các thẻ quan trọng nhất để xây dựng bố cục khi kết hợp với CSS.

*   **`<div>`:** Một khối (block-level) dùng để nhóm các thành phần lại với nhau.
*   **`<span>`:** Một phần tử nội dòng (inline) dùng để định dạng một phần nhỏ văn bản.

```html
<div style="background-color: #f0f0f0;">
    <h2>Tiêu đề trong Div</h2>
    <p>Văn bản có một từ <span style="color: red;">quan trọng</span> được tô màu.</p>
</div>
```

---

### 6. Thẻ HTML5 mang tính ngữ nghĩa (Semantic Tags)

Sử dụng các thẻ này giúp công cụ tìm kiếm (SEO) và các thiết bị hỗ trợ hiểu rõ cấu trúc trang web hơn là chỉ dùng thẻ `<div>`.

*   `<header>`: Phần đầu trang (logo, menu).
*   `<nav>`: Chứa các liên kết điều hướng.
*   `<main>`: Nội dung chính của trang.
*   `<section>`: Một phần nội dung cụ thể.
*   `<article>`: Một bài viết độc lập.
*   `<footer>`: Phần chân trang.

```html
<header>
    <nav>
        <ul>
            <li><a href="#">Trang chủ</a></li>
            <li><a href="#">Giới thiệu</a></li>
        </ul>
    </nav>
</header>
```

---

### 7. Thẻ Biểu mẫu (Forms)

Dùng để thu thập dữ liệu từ người dùng.

```html
<form action="/submit-data" method="POST">
    <!-- Nhãn cho ô nhập liệu -->
    <label for="username">Tên đăng nhập:</label><br>
    <input type="text" id="username" name="username" placeholder="Nhập tên..."><br><br>

    <label for="password">Mật khẩu:</label><br>
    <input type="password" id="password" name="password"><br><br>

    <!-- Nút nhấn -->
    <button type="submit">Gửi thông tin</button>
</form>
```

---

### 8. Một số lưu ý quan trọng

1.  **Cặp thẻ đóng/mở:** Hầu hết các thẻ đều có cặp mở `<tag>` và đóng `</tag>`. Một số thẻ đặc biệt tự đóng như `<img>`, `<br>`, `<hr>`, `<input>`.
2.  **Thuộc tính (Attributes):** Luôn nằm trong thẻ mở, ví dụ: `<a href="...">`.
3.  **Lồng ghép thẻ:** Phải đảm bảo quy tắc "vào sau ra trước". Thẻ nào mở sau cùng thì phải đóng đầu tiên.
    *   *Đúng:* `<p><strong>Văn bản</strong></p>`
    *   *Sai:* `<p><strong>Văn bản</p></strong>`
4.  **Comment trong HTML:** Sử dụng cú pháp `<!-- Nội dung ghi chú -->` để giải thích mã nguồn mà không hiển thị trên trình duyệt.