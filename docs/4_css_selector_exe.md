# BÀI TẬP THỰC HÀNH: VẬN DỤNG CSS SELECTOR

### 1. Đề bài: Xây dựng giao diện "Hồ sơ cá nhân"

Hãy sử dụng đoạn mã HTML dưới đây và viết các quy tắc CSS để hoàn thành các yêu cầu định dạng cụ thể.

#### Mã nguồn HTML (Yêu cầu không thay đổi nội dung HTML):
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Bài tập CSS Selector</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div id="profile-card">
        <h1 class="name">Nguyễn Văn A</h1>
        <p class="title">Lập trình viên Front-end</p>
        
        <div class="description">
            <p>Tôi yêu thích việc xây dựng giao diện người dùng bằng <strong>HTML</strong> và <strong>CSS</strong>.</p>
            <p>Kỹ năng hiện có:</p>
            <ul class="skill-list">
                <li>Thiết kế giao diện (UI Design)</li>
                <li>Lập trình JavaScript cơ bản</li>
                <li>Sử dụng Git/GitHub</li>
            </ul>
        </div>

        <a href="#" class="btn-contact">Liên hệ với tôi</a>
        <a href="https://google.com" target="_blank">Tìm hiểu thêm</a>
    </div>

</body>
</html>
```

---

### 2. Yêu cầu định dạng (CSS Tasks)

Sử dụng các Selector phù hợp để thực hiện các nhiệm vụ sau trong tệp `style.css`:

1.  **Bộ chọn toàn cục (`*`):** Đặt phông chữ mặc định cho toàn bộ trang là `Arial, sans-serif` và đặt `margin`, `padding` về `0`.
2.  **Bộ chọn ID (`#`):** Tìm phần tử có ID là `profile-card` để đặt màu nền là `#f4f4f4`, chiều rộng `400px`, khoảng đệm (padding) `20px` và căn giữa khối này trên trang.
3.  **Bộ chọn Class (`.`):** Tìm phần tử có class `name` để đổi màu chữ thành `darkblue` và căn giữa văn bản.
4.  **Bộ chọn hậu duệ (Dấu cách):** Chỉ chọn các thẻ `<strong>` nằm bên trong class `description` để tô màu đỏ (`red`).
5.  **Bộ chọn con trực tiếp (`>`):** Chọn các thẻ `<li>` là con trực tiếp của `ul.skill-list` để đặt khoảng cách dòng (margin-bottom) là `10px`.
6.  **Bộ chọn giả lớp (`:hover`):** Khi di chuột qua thẻ có class `btn-contact`, hãy đổi màu nền của nó thành màu đen (`black`) và màu chữ thành trắng (`white`).
7.  **Bộ chọn giả lớp vị trí (`:nth-child`):** Chọn mục danh sách (`li`) thứ hai trong danh sách kỹ năng và đổi chữ thành in nghiêng (`italic`).
8.  **Bộ chọn thuộc tính (`[]`):** Chọn thẻ `<a>` nào có thuộc tính `target="_blank"` để thêm một đường gạch chân màu xanh dưới văn bản.

### 3. Tiêu chí đánh giá hoàn thành
*   Hiểu rõ sự khác biệt giữa việc tác động vào thẻ, class và ID.
*   Biết cách giới hạn phạm vi tác động của CSS (ví dụ: chỉ thẻ `strong` trong phần mô tả mới có màu đỏ).
*   Sử dụng thành thạo các trạng thái tương tác cơ bản như `:hover`.