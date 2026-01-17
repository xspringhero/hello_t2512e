# Display Flex trong CSS

**Flexbox (Flexible Box Layout)** là mô hình bố cục một chiều (1D), được thiết kế để phân bổ không gian và căn chỉnh các phần tử trong một giao diện ngay cả khi kích thước của chúng không xác định hoặc linh hoạt.

## 1. Các khái niệm cốt lõi
Để làm chủ Flexbox, cần nắm vững hệ trục tọa độ:
*   **Main Axis (Trục chính):** Trục mặc định dọc theo hướng các phần tử được sắp xếp (mặc định là từ trái sang phải).
*   **Cross Axis (Trục vuông góc):** Trục vuông góc với trục chính (mặc định là từ trên xuống dưới).

---

## 2. Thuộc tính dành cho Flex Container (Phần tử cha)

Để bắt đầu, ta cần thiết lập `display: flex;` hoặc `display: inline-flex;` cho phần tử cha.

### 2.1. flex-direction (Xác định hướng trục chính)
Thuộc tính này quyết định hướng sắp xếp của các phần tử con.
*   `row` (mặc định): Trái sang phải.
*   `row-reverse`: Phải sang trái.
*   `column`: Trên xuống dưới (Trục chính lúc này là trục dọc).
*   `column-reverse`: Dưới lên trên.

### 2.2. flex-wrap (Xác định việc xuống dòng)
*   `nowrap` (mặc định): Tất cả phần tử con cố gắng nằm trên một dòng.
*   `wrap`: Tự động xuống dòng khi không đủ không gian.
*   `wrap-reverse`: Xuống dòng theo hướng ngược lại.

### 2.3. justify-content (Căn chỉnh trên Trục chính)
Đây là thuộc tính quan trọng nhất để điều khiển khoảng cách ngang (khi ở chế độ `row`).
*   `flex-start`: Các phần tử dồn về đầu dòng.
*   `flex-end`: Các phần tử dồn về cuối dòng.
*   `center`: Căn giữa.
*   `space-between`: Khoảng cách giữa các phần tử bằng nhau, phần tử đầu và cuối sát mép.
*   `space-around`: Khoảng cách xung quanh mỗi phần tử bằng nhau.
*   `space-evenly`: Khoảng cách giữa mọi phần tử và mép container là bằng nhau hoàn toàn.

### 2.4. align-items (Căn chỉnh trên Trục dọc)
Xác định cách các phần tử con dàn hàng theo chiều dọc trong một dòng đơn.
*   `stretch` (mặc định): Kéo dài phần tử con để lấp đầy chiều cao container.
*   `flex-start`: Nằm ở đỉnh của dòng.
*   `flex-end`: Nằm ở đáy của dòng.
*   `center`: Căn giữa theo chiều dọc.
*   `baseline`: Căn theo đường chân chữ của nội dung bên trong.

### 2.5. align-content (Căn chỉnh các dòng)
Chỉ có tác dụng khi các phần tử con đã xuống dòng (`flex-wrap: wrap`). Nó căn chỉnh khoảng cách giữa các hàng với nhau.
*   Các giá trị tương tự `justify-content`: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `stretch`.

---

## 3. Thuộc tính dành cho Flex Items (Phần tử con trực tiếp)

### 3.1. flex-grow (Khả năng giãn)
Xác định tỷ lệ phần tử con sẽ lớn lên khi container còn trống.
*   Giá trị mặc định là `0`. Nếu đặt là `1`, phần tử sẽ chiếm toàn bộ không gian còn lại.

### 3.2. flex-shrink (Khả năng co)
Xác định tỷ lệ phần tử con sẽ co lại khi container bị thiếu không gian.
*   Giá trị mặc định là `1`. Nếu đặt là `0`, phần tử sẽ giữ nguyên kích thước mà không bị bóp nghẹt.

### 3.3. flex-basis (Kích thước cơ sở)
Xác định kích thước ban đầu của phần tử trước khi các không gian trống được phân phối. Thay thế cho `width` khi ở trong Flexbox.

### 3.4. flex (Viết tắt)
Kết hợp của `grow`, `shrink`, và `basis`.
*   Ví dụ: `flex: 1 0 200px;` (Grow = 1, Shrink = 0, Basis = 200px).

### 3.5. align-self
Cho phép một phần tử con ghi đè thuộc tính `align-items` của cha.

---

## 4. Code mẫu thực tế: Xây dựng Layout Card

Dưới đây là ví dụ kết hợp các thuộc tính Flexbox để tạo một hàng danh sách sản phẩm.

### Mã HTML
```html
<div class="product-container">
    <div class="product-card">Sản phẩm 1</div>
    <div class="product-card">Sản phẩm 2</div>
    <div class="product-card special">Sản phẩm 3 (Nổi bật)</div>
    <div class="product-card">Sản phẩm 4</div>
</div>
```

### Mã CSS
```css
/* Thiết lập cho Container */
.product-container {
    display: flex;             /* Kích hoạt Flexbox */
    flex-direction: row;       /* Sắp xếp theo hàng ngang */
    flex-wrap: wrap;           /* Tự động xuống dòng trên mobile */
    justify-content: center;   /* Căn giữa các card */
    align-items: stretch;      /* Các card cao bằng nhau */
    gap: 20px;                 /* Khoảng cách giữa các card */
    padding: 20px;
    background-color: #f4f4f4;
}

/* Thiết lập cho các Item */
.product-card {
    flex: 0 1 200px;           /* Không giãn, được co, kích thước gốc 200px */
    background-color: white;
    padding: 20px;
    border: 1px solid #ddd;
    text-align: center;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

/* Ghi đè căn chỉnh cho một item cụ thể */
.product-card.special {
    flex-grow: 1;              /* Riêng phần tử này sẽ giãn ra chiếm hết chỗ trống */
    border: 2px solid #e74c3c;
    align-self: center;        /* Tự căn giữa mình nó bất chấp thuộc tính cha */
}
```

---

## 5. Bảng tổng hợp nhanh các giá trị Flexbox

| Mục tiêu | Thuộc tính cha | Giá trị phổ biến |
| :--- | :--- | :--- |
| **Hướng trục** | `flex-direction` | `row`, `column` |
| **Căn ngang** | `justify-content` | `center`, `space-between`, `flex-end` |
| **Căn dọc** | `align-items` | `center`, `stretch` |
| **Xuống dòng** | `flex-wrap` | `wrap`, `nowrap` |
| **Khoảng cách** | `gap` | Kích thước (px, rem, %) |

**Lưu ý chuyên môn:** Flexbox hoạt động theo cơ chế tính toán động. Khi sử dụng `flex: 1`, bạn đang yêu cầu trình duyệt ưu tiên phân phối lại không gian cho phần tử đó sau khi đã trừ đi kích thước của các phần tử cố định khác. Đây là kỹ thuật cốt lõi để xử lý giao diện Responsive (tương thích mọi màn hình).