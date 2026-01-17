# BÀI TẬP THỰC HÀNH: VẬN DỤNG CSS SELECTOR

### Đáp án (Tham khảo sau khi hoàn thành)


```css
/* 1. Bộ chọn toàn cục */
* {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* 2. Bộ chọn ID */
#profile-card {
    background-color: #f4f4f4;
    width: 400px;
    padding: 20px;
    margin: 50px auto; /* Căn giữa khối theo chiều ngang */
    border: 1px solid #ddd;
}

/* 3. Bộ chọn Class */
.name {
    color: darkblue;
    text-align: center;
    margin-bottom: 10px;
}

/* 4. Bộ chọn hậu duệ */
.description strong {
    color: red;
}

/* 5. Bộ chọn con trực tiếp */
.skill-list > li {
    margin-bottom: 10px;
}

/* 6. Bộ chọn giả lớp trạng thái */
.btn-contact:hover {
    background-color: black;
    color: white;
}

/* 7. Bộ chọn giả lớp vị trí */
.skill-list li:nth-child(2) {
    font-style: italic;
}

/* 8. Bộ chọn thuộc tính */
a[target="_blank"] {
    text-decoration: underline;
    color: blue;
}

/* Định dạng bổ sung cho các nút (tùy chọn) */
.btn-contact {
    display: inline-block;
    padding: 10px 15px;
    background-color: lightblue;
    text-decoration: none;
    color: #333;
    border-radius: 5px;
}
```