# Thuộc tính Display và Ứng dụng Thực tế

## 1. Display: Flex (Flexible Box) - Bố cục một chiều
`flex` là công cụ mạnh mẽ nhất để căn chỉnh các phần tử theo một chiều (hàng ngang hoặc cột dọc).

### Đặc điểm:
*   Biến phần tử cha thành một **Flex Container**.
*   Các phần tử con trực tiếp trở thành **Flex Items**.
*   Khả năng tự động co giãn, phân bổ khoảng cách và căn giữa cực kỳ linh hoạt.

### Ứng dụng thực tế: Thanh điều hướng (Navigation Bar)
```html
<nav class="navbar">
    <div class="logo">LOGO</div>
    <ul class="nav-links">
        <li>Trang chủ</li>
        <li>Sản phẩm</li>
        <li>Liên hệ</li>
    </ul>
    <button class="btn-login">Đăng nhập</button>
</nav>
```

```css
.navbar {
    display: flex; /* Kích hoạt Flexbox */
    justify-content: space-between; /* Đẩy logo sang trái, nút sang phải, menu ở giữa */
    align-items: center; /* Căn giữa tất cả các phần tử theo chiều dọc */
    padding: 10px 20px;
    background-color: #2c3e50;
    color: white;
}

.nav-links {
    display: flex; /* Menu cũng sử dụng flex để các thẻ li nằm ngang */
    list-style: none;
    gap: 20px; /* Tạo khoảng cách 20px giữa các mục menu */
}
```

---

## 2. Display: Grid - Bố cục hai chiều
`grid` cho phép kiểm soát cả hàng (rows) và cột (columns) cùng lúc, lý tưởng cho các bố cục trang phức tạp.

### Đặc điểm:
*   Chia giao diện thành các ô (cells) như một bảng nhưng linh hoạt hơn nhiều.
*   Kiểm soát vị trí phần tử con chính xác theo tọa độ hàng/cột.

### Ứng dụng thực tế: Danh mục sản phẩm (Product Grid)
```html
<div class="product-grid">
    <div class="item">Sản phẩm 1</div>
    <div class="item">Sản phẩm 2</div>
    <div class="item">Sản phẩm 3</div>
    <div class="item">Sản phẩm 4</div>
</div>
```

```css
.product-grid {
    display: grid;
    /* Tạo 4 cột có chiều rộng bằng nhau (1fr = 1 fraction) */
    grid-template-columns: repeat(4, 1fr); 
    /* Khoảng cách giữa các ô */
    gap: 15px;
}

.item {
    background: #ecf0f1;
    padding: 20px;
    text-align: center;
    border: 1px solid #bdc3c7;
}
```

---

## 3. Display: None - Loại bỏ phần tử
`display: none` dùng để ẩn hoàn toàn một phần tử khỏi trang web.

### Đặc điểm:
*   Phần tử bị xóa bỏ hoàn toàn khỏi luồng hiển thị (không chiếm bất kỳ không gian nào).
*   Khác với `visibility: hidden` (ẩn nhưng vẫn chiếm chỗ).

### Ứng dụng thực tế: Menu Mobile (Hamburger Menu)
```css
/* Mặc định ẩn menu trên máy tính (nếu là thiết kế mobile-first) */
.mobile-menu {
    display: none;
}

/* Khi người dùng nhấn nút hoặc trên màn hình nhỏ, dùng JavaScript để đổi thành display: block */
.mobile-menu.active {
    display: block;
}
```

---

## 4. Bảng so sánh và tình huống sử dụng

| Giá trị Display | Khi nào nên sử dụng? |
| :--- | :--- |
| **Block** | Khi muốn phần tử chiếm trọn một dòng (tiêu đề, đoạn văn). |
| **Inline** | Khi muốn phần tử nằm trong dòng văn bản (link, chữ đậm). |
| **Inline-block** | Khi tạo danh sách nằm ngang nhưng cần chỉnh kích thước/padding (nút bấm). |
| **Flex** | Khi căn giữa phần tử, chia cột đơn giản, hoặc làm thanh menu, sidebar. |
| **Grid** | Khi xây dựng toàn bộ khung trang web, dashboard phức tạp, hoặc lưới ảnh. |
| **None** | Khi muốn ẩn phần tử (popup, menu ẩn, tab nội dung). |

---

## 5. Mẹo nâng cao: Căn giữa tuyệt đối với Display
Trước khi có Flexbox, việc căn giữa một phần tử vào giữa màn hình rất phức tạp. Hiện nay, điều đó trở nên cực kỳ đơn giản:

### Cách dùng Flexbox:
```css
.parent {
    display: flex;
    justify-content: center; /* Căn giữa ngang */
    align-items: center;     /* Căn giữa dọc */
    height: 100vh;           /* Chiều cao toàn màn hình */
}
```

### Cách dùng Grid:
```css
.parent {
    display: grid;
    place-items: center;     /* Căn giữa cả hai chiều chỉ với 1 dòng */
    height: 100vh;
}
```