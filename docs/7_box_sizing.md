# Box-Sizing và Display trong CSS

## 1. Chi tiết về thuộc tính Box-Sizing

`box-sizing` quyết định phương thức trình duyệt tính toán tổng kích thước (chiều rộng và chiều cao) của một phần tử.

### 1.1. Content-box (Mặc định)
Đây là giá trị mặc định của CSS. Kích thước bạn thiết lập cho `width` và `height` chỉ áp dụng cho phần nội dung (content).

*   **Đặc điểm:** Nếu thêm `padding` hoặc `border`, phần tử sẽ phình to hơn kích thước ban đầu.
*   **Hệ quả:** Dễ gây vỡ bố cục khi tính toán sai số pixel.

### 1.2. Border-box (Tiêu chuẩn hiện đại)
Khi sử dụng `border-box`, kích thước `width` và `height` bao gồm cả nội dung, vùng đệm và viền.

*   **Đặc điểm:** Padding và Border sẽ lấn vào bên trong, không làm thay đổi tổng kích thước bên ngoài của phần tử.
*   **Lợi ích:** Giúp việc tính toán bố cục (layout) cực kỳ đơn giản và chính xác.

### So sánh qua mã nguồn:

```html
<div class="container">
    <div class="box content-box">Content-box</div>
    <div class="box border-box">Border-box</div>
</div>
```

```css
.box {
    width: 300px;
    height: 100px;
    padding: 20px;
    border: 10px solid #2c3e50;
    margin-bottom: 20px;
    color: white;
}

/* Kích thước thực tế: 300 + (20*2) + (10*2) = 360px */
.content-box {
    box-sizing: content-box;
    background-color: #e74c3c;
}

/* Kích thước thực tế: Luôn là 300px */
.border-box {
    box-sizing: border-box;
    background-color: #27ae60;
}
```

---

## 2. Các kiểu hiển thị: Block và Inline

Thuộc tính `display` xác định cách thức các "hộp" xếp chồng hoặc đứng cạnh nhau trong dòng chảy của văn bản (Normal Flow).

### 2.1. Block-level Elements (Phần tử khối)
Các phần tử mặc định là block: `<div>`, `<h1>` - `<h6>`, `<p>`, `<ul>`, `<li>`, `<section>`,...

*   **Hành vi:** Luôn bắt đầu trên một dòng mới. Chiếm toàn bộ chiều rộng của vùng chứa (container) nếu không thiết lập chiều rộng.
*   **Box Model:** Áp dụng đầy đủ và chính xác các thuộc tính `width`, `height`, `padding`, `border`, `margin`.

### 2.2. Inline Elements (Phần tử nội dòng)
Các phần tử mặc định là inline: `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`,...

*   **Hành vi:** Nằm trên cùng một dòng với các phần tử khác. Chỉ chiếm không gian vừa đủ theo nội dung của nó.
*   **Box Model bị hạn chế:**
    *   **Không** thể thiết lập `width` và `height`.
    *   `margin-top` và `margin-bottom` **không** đẩy các phần tử khác ra xa (không có tác dụng lên dòng chảy đứng).
    *   `padding-top/bottom` và `border` có hiển thị nhưng có thể đè lên các dòng văn bản xung quanh.

### 2.3. Inline-block (Sự kết hợp hoàn hảo)
Đây là giá trị lai giữa Block và Inline.

*   **Hành vi:** Nằm trên cùng một dòng (giống Inline).
*   **Box Model:** Cho phép thiết lập `width`, `height`, `margin`, `padding` đầy đủ (giống Block).

---

## 3. Mã minh họa sự khác biệt giữa các kiểu Display

```html
<!-- Minh họa Block -->
<div class="display-block">Block Element 1</div>
<div class="display-block">Block Element 2</div>

<hr>

<!-- Minh họa Inline -->
<span class="display-inline">Inline Element 1</span>
<span class="display-inline">Inline Element 2</span>

<hr>

<!-- Minh họa Inline-block -->
<div class="display-inline-block">Inline-block 1</div>
<div class="display-inline-block">Inline-block 2</div>
```

```css
/* BLOCK: Xếp chồng lên nhau, nhận đủ width/height */
.display-block {
    display: block;
    background-color: #3498db;
    width: 200px;
    height: 50px;
    margin: 10px 0;
}

/* INLINE: Nằm cùng dòng, phớt lờ width/height */
.display-inline {
    display: inline;
    background-color: #f1c40f;
    width: 500px; /* Sẽ bị trình duyệt bỏ qua */
    height: 100px; /* Sẽ bị trình duyệt bỏ qua */
    padding: 10px;
}

/* INLINE-BLOCK: Nằm cùng dòng nhưng vẫn nhận đủ width/height */
.display-inline-block {
    display: inline-block;
    background-color: #9b59b6;
    width: 150px;
    height: 60px;
    margin: 5px;
    text-align: center;
    vertical-align: middle; /* Căn chỉnh theo chiều dọc giữa các hộp inline */
}
```

---

## 4. Quy tắc áp dụng trong thực tế (Best Practices)

1.  **Thiết lập Global Border-box:** Để tránh việc phải tính toán thủ công mỗi khi thêm padding, hãy luôn đặt quy tắc sau ở đầu file CSS:
    ```css
    * {
        box-sizing: border-box;
    }
    ```
2.  **Sử dụng Inline-block cho Menu/Buttons:** Khi muốn các nút bấm hoặc các mục menu nằm ngang nhưng vẫn muốn điều chỉnh kích thước và khoảng cách chính xác, `display: inline-block` là lựa chọn tối ưu.
3.  **Thay đổi Display khi cần:** Không nhất thiết phải giữ nguyên kiểu hiển thị mặc định của thẻ HTML. Bạn hoàn toàn có thể biến một thẻ `<a>` (inline) thành một khối (block) để làm một nút bấm lớn bao phủ toàn bộ vùng chứa bằng `display: block`.
4.  **Lưu ý về Vertical-align:** Khi sử dụng `inline-block`, các phần tử có thể bị lệch dòng do sự khác biệt về nội dung. Hãy sử dụng thuộc tính `vertical-align: top/middle/bottom` để căn chỉnh chúng ngay hàng thẳng lối.