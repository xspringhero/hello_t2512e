# SỬ DỤNG PSEUDO-CLASS VÀ PSEUDO-ELEMENT

Trong CSS, **Pseudo-class** (lớp giả) và **Pseudo-element** (phần tử giả) là hai khái niệm nâng cao giúp chọn lọc và định dạng các trạng thái hoặc các phần cụ thể của phần tử mà không cần thêm mã HTML dư thừa.

---

### 1. Pseudo-class (Lớp giả)

**Định nghĩa:** Pseudo-class được sử dụng để xác định một **trạng thái đặc biệt** của một phần tử.
**Cú pháp:** Sử dụng một dấu hai chấm (`:`) liền sau bộ chọn.

#### Các nhóm Pseudo-class phổ biến:

*   **Trạng thái người dùng:** `:hover` (di chuột qua), `:active` (đang nhấn giữ), `:focus` (khi ô nhập liệu được chọn).
*   **Trạng thái cấu trúc:** `:first-child` (con đầu tiên), `:last-child` (con cuối cùng), `:nth-child(n)` (con thứ n).
*   **Trạng thái biểu mẫu:** `:checked` (khi checkbox được chọn), `:disabled` (khi phần tử bị vô hiệu hóa).

**Ví dụ minh họa:**

```css
/* Thay đổi màu liên kết khi người dùng di chuột qua */
a:hover {
    color: #ff5722;
    text-decoration: underline;
}

/* Định dạng cho ô input khi đang được nhập liệu */
input:focus {
    border: 2px solid #4CAF50;
    outline: none;
}

/* Chọn các dòng lẻ trong danh sách để tô màu nền */
li:nth-child(odd) {
    background-color: #f2f2f2;
}

/* Loại bỏ lề dưới của phần tử con cuối cùng trong một khối */
.container p:last-child {
    margin-bottom: 0;
}
```

---

### 2. Pseudo-element (Phần tử giả)

**Định nghĩa:** Pseudo-element được sử dụng để định kiểu cho một **phần cụ thể** của phần tử hoặc **chèn nội dung** vào trước/sau phần tử đó.
**Cú pháp:** Sử dụng hai dấu hai chấm (`::`) liền sau bộ chọn. (Mặc dù một dấu `:` vẫn hoạt động cho các trình duyệt cũ, nhưng tiêu chuẩn CSS3 quy định dùng `::` để phân biệt với Pseudo-class).

#### Các Pseudo-element phổ biến:

*   `::before`: Chèn nội dung vào trước nội dung của phần tử.
*   `::after`: Chèn nội dung vào sau nội dung của phần tử.
*   `::first-letter`: Định dạng chữ cái đầu tiên của văn bản.
*   `::selection`: Định dạng phần văn bản được người dùng bôi đen.

**Ví dụ minh họa:**

```css
/* Chèn một biểu tượng hoặc văn bản trước tiêu đề */
h2::before {
    content: "📍"; /* Thuộc tính content là bắt buộc với ::before và ::after */
    margin-right: 8px;
}

/* Tạo hiệu ứng chữ cái đầu tiên (Drop cap) */
p::first-letter {
    font-size: 200%;
    font-weight: bold;
    color: #333;
    float: left;
    margin-right: 5px;
}

/* Thay đổi màu nền khi người dùng bôi đen văn bản */
p::selection {
    background-color: yellow;
    color: black;
}
```

---

### 3. Sự khác biệt chính

| Đặc điểm | Pseudo-class (`:`) | Pseudo-element (`::`) |
| :--- | :--- | :--- |
| **Mục đích** | Thay đổi định dạng theo **trạng thái** hoặc vị trí. | Thay đổi định dạng một **phần nội dung** cụ thể. |
| **Tác động** | Tác động lên toàn bộ phần tử hiện có. | Có thể tạo ra "thành phần ảo" không tồn tại trong HTML. |
| **Ký hiệu** | Sử dụng 1 dấu hai chấm (ví dụ: `:hover`). | Sử dụng 2 dấu hai chấm (ví dụ: `::after`). |
| **Số lượng** | Một phần tử có thể có nhiều trạng thái cùng lúc. | Một phần tử thường chỉ dùng một số ít phần tử giả. |

---

### 4. Ví dụ tổng hợp thực tế

Dưới đây là cách kết hợp cả hai để tạo ra một nút bấm (button) có hiệu ứng chuyên nghiệp:

**HTML:**
```html
<button class="custom-button">Gửi tin nhắn</button>
```

**CSS:**
```css
.custom-button {
    position: relative;
    padding: 10px 20px;
    background-color: #007bff;
    color: white;
    border: none;
    cursor: pointer;
}

/* Sử dụng Pseudo-element để tạo một đường gạch dưới ảo */
.custom-button::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0%; /* Ban đầu đường kẻ có độ dài bằng 0 */
    height: 2px;
    background-color: white;
    transition: width 0.3s; /* Tạo hiệu ứng mượt mà */
}

/* Sử dụng Pseudo-class :hover để kích hoạt Pseudo-element */
.custom-button:hover::after {
    width: 100%; /* Khi di chuột vào, đường kẻ chạy dài ra 100% */
}

/* Thay đổi màu nền nút khi di chuột qua */
.custom-button:hover {
    background-color: #0056b3;
}
```

### Lưu ý quan trọng:
1.  **Thuộc tính `content`:** Đối với `::before` và `::after`, nếu không có thuộc tính `content` (ngay cả khi giá trị là rỗng `""`), phần tử giả sẽ không hiển thị trên trình duyệt.
2.  **Tính ngữ nghĩa:** Không nên lạm dụng `::before` và `::after` để chèn các nội dung quan trọng về mặt thông tin (như văn bản chính), vì các trình đọc màn hình cho người khiếm thị có thể gặp khó khăn khi nhận diện nội dung này. Chỉ nên dùng cho mục đích trang trí.