# HƯỚNG DẪN CHI TIẾT VỀ BỘ CHỌN (SELECTORS) TRONG CSS

Bộ chọn (Selectors) là thành phần quan trọng nhất trong CSS, đóng vai trò xác định chính xác các phần tử HTML nào sẽ được áp dụng các quy tắc định kiểu. Việc nắm vững Selector giúp tối ưu hóa mã nguồn và quản lý giao diện một cách khoa học.

---

### 1. Bộ chọn cơ bản (Basic Selectors)

Đây là nhóm bộ chọn được sử dụng thường xuyên nhất để tác động trực tiếp vào các phần tử.

*   **Bộ chọn toàn cục (`*`):** Chọn tất cả các phần tử có trên trang web. Thường dùng để reset lề (margin) và đệm (padding).
    ```css
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box; /* Quy định cách tính kích thước hộp */
    }
    ```
*   **Bộ chọn thẻ (Type Selector):** Chọn dựa trên tên thẻ HTML.
    ```css
    h1 { color: navy; } /* Áp dụng cho tất cả thẻ <h1> */
    p { line-height: 1.6; } /* Áp dụng cho tất cả thẻ <p> */
    ```
*   **Bộ chọn Class (`.`):** Chọn các phần tử có thuộc tính `class` tương ứng. Một class có thể dùng cho nhiều phần tử.
    ```css
    .text-red { color: red; } 
    /* Áp dụng cho bất kỳ thẻ nào có class="text-red" */
    ```
*   **Bộ chọn ID (`#`):** Chọn phần tử có thuộc tính `id` tương ứng. Mỗi ID là duy nhất trong một trang HTML.
    ```css
    #main-navigation { background-color: #eee; }
    /* Áp dụng cho thẻ có id="main-navigation" */
    ```

---

### 2. Bộ chọn gom nhóm (Grouping Selector)

Khi nhiều phần tử có cùng một phong cách định dạng, có thể sử dụng dấu phẩy `,` để liệt kê các bộ chọn, giúp giảm thiểu lặp lại mã.

```css
/* Gom nhóm các thẻ tiêu đề để dùng chung phông chữ */
h1, h2, h3 {
    font-family: 'Arial', sans-serif;
    color: #333;
}
```

---

### 3. Bộ chọn kết hợp (Combinators)

Bộ chọn kết hợp xác định mối quan hệ giữa các phần tử HTML (cha, con, anh em).

*   **Bộ chọn hậu duệ (Dấu cách):** Chọn tất cả phần tử con, cháu nằm bên trong một phần tử cha.
    ```css
    /* Chọn tất cả thẻ <a> nằm bên trong thẻ <nav> */
    nav a {
        text-decoration: none;
    }
    ```
*   **Bộ chọn con trực tiếp (`>`):** Chỉ chọn các phần tử là con trực tiếp của cha (không chọn cấp cháu).
    ```css
    /* Chỉ chọn thẻ <li> là con trực tiếp của <ul> */
    ul > li {
        list-style: square;
    }
    ```
*   **Bộ chọn anh em liền kề (`+`):** Chọn một phần tử nằm ngay sau một phần tử khác.
    ```css
    /* Chọn thẻ <p> đầu tiên nằm ngay sau thẻ <h1> */
    h1 + p {
        font-weight: bold;
    }
    ```
*   **Bộ chọn anh em chung (`~`):** Chọn tất cả các phần tử anh em nằm phía sau.
    ```css
    /* Chọn tất cả thẻ <p> nằm phía sau <h1> cùng cấp */
    h1 ~ p {
        color: gray;
    }
    ```

---

### 4. Bộ chọn giả lớp (Pseudo-classes)

Dùng để xác định trạng thái của một phần tử hoặc chọn phần tử dựa trên vị trí của nó. Cú pháp sử dụng dấu hai chấm `:`.

*   **Trạng thái tương tác:**
    ```css
    a:hover { color: orange; }  /* Khi di chuột qua liên kết */
    input:focus { border: 2px solid blue; } /* Khi ô nhập liệu được nhấn vào */
    ```
*   **Dựa trên vị trí:**
    ```css
    li:first-child { color: red; }    /* Phần tử con đầu tiên */
    li:last-child { color: green; }   /* Phần tử con cuối cùng */
    li:nth-child(2) { color: blue; }  /* Phần tử con thứ 2 */
    li:nth-child(odd) { background: #f9f9f9; } /* Các phần tử ở vị trí lẻ */
    ```

---

### 5. Bộ chọn giả phần tử (Pseudo-elements)

Dùng để định kiểu cho một phần cụ thể của phần tử. Cú pháp sử dụng hai dấu hai chấm `::`.

*   `::before`: Chèn nội dung vào trước nội dung của phần tử.
*   `::after`: Chèn nội dung vào sau nội dung của phần tử.
*   `::first-letter`: Định dạng chữ cái đầu tiên của văn bản.

```css
/* Thêm ký hiệu trước mỗi mục danh sách */
li::before {
    content: "• ";
    color: red;
}

/* Định dạng chữ cái đầu tiên to hơn */
p::first-letter {
    font-size: 200%;
    font-weight: bold;
}
```

---

### 6. Bộ chọn thuộc tính (Attribute Selectors)

Chọn phần tử dựa trên các thuộc tính mà phần tử đó sở hữu.

```css
/* Chọn các thẻ <input> có thuộc tính type="text" */
input[type="text"] {
    width: 100%;
    padding: 10px;
}

/* Chọn các thẻ <a> có thuộc tính target */
a[target] {
    background-color: yellow;
}
```

---

### 7. Quy tắc ưu tiên (Specificity)

Khi một phần tử bị tác động bởi nhiều bộ chọn khác nhau, trình duyệt sẽ tính điểm ưu tiên để quyết định CSS nào được áp dụng:

1.  **Inline style:** Viết trực tiếp vào thẻ HTML (Ưu tiên cao nhất).
2.  **ID Selector:** `#header`.
3.  **Class/Pseudo-class:** `.menu`, `:hover`.
4.  **Element Selector:** `div`, `p`.

**Nguyên tắc:** Bộ chọn càng chi tiết (ID > Class > Thẻ) thì độ ưu tiên càng cao. Nếu độ ưu tiên bằng nhau, quy tắc nào viết sau trong tệp CSS sẽ được thực thi.

---

### 8. Ví dụ minh họa tổng hợp

```css
/* Chọn thẻ <div> có class "container" */
div.container {
    max-width: 1200px;
}

/* Chọn thẻ <button> bên trong thẻ có ID "login-form" khi di chuột qua */
#login-form button:hover {
    cursor: pointer;
    opacity: 0.8;
}

/* Chọn mọi thẻ <p> là con của <article>, nhưng chỉ chọn dòng đầu tiên */
article p::first-line {
    text-transform: uppercase;
}
```