# TÀI LIỆU HƯỚNG DẪN CƠ BẢN VỀ CSS (CASCADING STYLE SHEETS)

CSS (Cascading Style Sheets) là ngôn ngữ dùng để định dạng và trình bày giao diện cho các tài liệu viết bằng HTML. Nếu HTML đóng vai trò xây dựng khung sườn và nội dung, thì CSS giúp tùy chỉnh màu sắc, phông chữ và bố cục để trang web trở nên chuyên nghiệp hơn.

---

### 1. Cấu trúc của một quy tắc CSS

Mỗi quy tắc CSS bao gồm hai phần chính: **Bộ chọn (Selector)** và **Khối khai báo (Declaration Block)**.

```css
/* Selector { Property: Value; } */

p {
  color: red;        /* Thuộc tính: Giá trị */
  font-size: 16px;   /* Thuộc tính: Giá trị */
}
```

*   **Selector (Bộ chọn):** Chỉ định phần tử HTML muốn định dạng (ví dụ: thẻ `<p>`, thẻ `<h1>`).
*   **Property (Thuộc tính):** Đặc điểm muốn thay đổi (ví dụ: màu sắc, kích thước chữ).
*   **Value (Giá trị):** Thông số cụ thể áp dụng cho thuộc tính.

---

### 2. Các cách chèn CSS vào trang HTML

Có 3 phương pháp chính để áp dụng CSS vào một tài liệu HTML:

#### 2.1. CSS ngoài (External CSS) - Phương pháp tối ưu nhất
Toàn bộ mã CSS được viết trong một tệp riêng có đuôi `.css`. Sau đó, tệp này được liên kết vào tệp HTML thông qua thẻ `<link>` đặt trong phần `<head>`.

```html
<!-- Trong tệp index.html -->
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

#### 2.2. CSS trong (Internal CSS)
Mã CSS được viết trực tiếp bên trong thẻ `<style>`, nằm trong phần `<head>` của trang HTML. Thích hợp khi chỉ muốn định dạng riêng cho một trang duy nhất.

```html
<head>
    <style>
        body {
            background-color: lightgray;
        }
    </style>
</head>
```

#### 2.3. CSS trực tiếp (Inline CSS)
Viết trực tiếp vào thuộc tính `style` của từng thẻ HTML. Cách này chỉ nên dùng cho những chỉnh sửa nhỏ, tức thời vì khó quản lý.

```html
<h1 style="color: blue; text-align: center;">Đây là tiêu đề</h1>
```

---

### 3. Các bộ chọn (Selectors) cơ bản

Để CSS tác động chính xác vào phần tử mong muốn, cần sử dụng các bộ chọn sau:

*   **Chọn theo tên thẻ:** Tác động đến tất cả các thẻ cùng loại.
    *   Ví dụ: `h2 { color: green; }` (Tất cả thẻ h2 sẽ có màu xanh).
*   **Chọn theo Class (Lớp):** Dùng dấu chấm `.` trước tên class. Một class có thể dùng cho nhiều thẻ khác nhau.
    *   Ví dụ: `.text-highlight { color: orange; }`
*   **Chọn theo ID:** Dùng dấu thăng `#` trước tên ID. Mỗi ID là duy nhất và chỉ dùng cho một phần tử trên trang.
    *   Ví dụ: `#main-title { font-size: 30px; }`

---

### 4. Các thuộc tính CSS quan trọng và hay dùng nhất

Dưới đây là danh sách các thuộc tính cơ bản thường xuyên được sử dụng khi xây dựng giao diện:

#### 4.1. Nhóm thuộc tính về văn bản (Text)
*   `color`: Thay đổi màu sắc của chữ. (Ví dụ: `red`, `#ffffff`, `rgb(0,0,0)`).
*   `font-size`: Kích thước chữ (Ví dụ: `14px`, `1.2rem`, `110%`).
*   `font-family`: Kiểu phông chữ (Ví dụ: `Arial`, `Times New Roman`).
*   `text-align`: Căn lề văn bản (`left`, `right`, `center`, `justify`).
*   `font-weight`: Độ đậm của chữ (`normal`, `bold`).

#### 4.2. Nhóm thuộc tính về màu nền (Background)
*   `background-color`: Màu nền của phần tử.

#### 4.3. Nhóm thuộc tính về kích thước và khung (Box Model)
Mọi phần tử web đều được coi là một hình hộp. Các thuộc tính này giúp điều chỉnh kích thước hộp đó:
*   `width`: Chiều rộng của phần tử.
*   `height`: Chiều cao của phần tử.
*   `padding`: Khoảng cách từ nội dung đến viền (khoảng trống bên trong hộp).
*   `margin`: Khoảng cách từ viền ra các phần tử xung quanh (khoảng trống bên ngoài hộp).
*   `border`: Đường viền bao quanh phần tử.
    *   *Ví dụ:* `border: 1px solid black;` (Viền đen, nét liền, dày 1px).

---

### 5. Ví dụ tổng hợp

Dưới đây là cách kết hợp HTML và CSS để định dạng một khối nội dung cơ bản:

**HTML:**
```html
<div class="card">
    <h2 id="title">Tiêu đề bài viết</h2>
    <p class="content">Đây là nội dung mô tả ngắn gọn về bài viết.</p>
</div>
```

**CSS:**
```css
/* Định dạng cho khối bao quanh */
.card {
    width: 300px;
    background-color: white;
    padding: 20px;          /* Khoảng cách bên trong */
    margin: 10px;           /* Khoảng cách bên ngoài */
    border: 1px solid #ccc; /* Viền xám nhạt */
}

/* Định dạng cho tiêu đề bên trong khối */
#title {
    color: darkblue;
    text-align: center;
}

/* Định dạng cho đoạn văn */
.content {
    font-family: sans-serif;
    line-height: 1.5;       /* Khoảng cách giữa các dòng */
}
```

---

### 6. Ghi chú trong CSS
Để ghi chú hoặc giải thích các đoạn mã, sử dụng cú pháp `/* nội dung ghi chú */`. Nội dung này sẽ không hiển thị trên trình duyệt.

```css
/* Tùy chỉnh màu chữ cho toàn bộ trang web */
body {
    color: #333;
}
```