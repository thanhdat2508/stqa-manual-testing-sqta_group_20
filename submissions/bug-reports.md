# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-01

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | BUG-01             |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-01`           |
| **Mức độ**          | `High`             |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Đăng nhập với email viết hoa không thành công`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `MacOS`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Khi vào trang và bắt đầu đăng nhập với email được viết hoa`

**Bước tái hiện:**

1. `Bước 1: Nhập email với chữ cái in hoa, VD: Ba.nguyen@email.com thay vì ba.nguyen@email.com`
2. `Bước 2: Nhập mật khẩu`

**Kết quả mong đợi:**
`Mong đợi vẫn có thể đăng nhập khi email đăng nhập viết hoa hay viết thường`

**Kết quả thực tế:**
`Lỗi đăng nhập khi viết hoa email đăng nhập`

**Tác động:**
`Gây cản trở việc đăng nhập khi người dùng nhập in hoa thay vì in thường`

**Minh chứng:**
![BUG-01](/submisions/images/BUG-01.png)

**Đề xuất xử lý:**
`Thêm function toLowerCase() trước khi đưa server xử lý`

## BUG-11

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | BUG-11           |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-04`           |
| **Mức độ**          | `High`             |
| **Người phát hiện** | `Bùi Mạnh Hiếu` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Lỗi trắng trang web + mất dữ liệu khi spam nhiều lần mục mượn sách`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window 10`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đăng nhập được vào tài khoản và tương tác với trang web`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản khả dụng`
2. `Bước 2: Spam nhiều lần nút Mượn sau khi ấn vào ô dấu cộng`

**Kết quả mong đợi:**
`Mong đợi ngăn người dùng spam để tránh lỗi server và mất dữ liệu `

**Kết quả thực tế:**
`Người dùng vẫn spam được gây lỗi và mất dữ liệu`

**Tác động:**
`Gây ảnh hưởng tới server và giảm trải nghiệm người dùng `

**Minh chứng:**
![BUG-01](/submisions/images/BUG-01.png)

**Đề xuất xử lý:**
`thêm disable button để tránh người dùng tiếp tục spam sau khi ấn và không ảnh hưởng tới server dữ liệu`

