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

## BUG-06

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | BUG-06           |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-06`           |
| **Mức độ**          | `High`             |
| **Người phát hiện** | `Bùi Mạnh Hiếu` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Lỗi popup thông báo về trạng thái tài khoản, tài khoảng "Tạm ngưng" nhưng báo bị "Hết Hạn"`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đăng nhập và sử dụng tài khoản trạng thái "Tạm ngưng"`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào tài khoản có trạng thái "Tạm ngưng" `
2. `Bước 2: Mượn sách`

**Kết quả mong đợi:**
`Mong đợi hệ thống thông báo popup sẽ hiện cảnh báo riêng cho từng loại tài khoản`

**Kết quả thực tế:**
`Thông báo lỗi sai trạng thái tài khoản`

**Tác động:**
`Gây hiểu nhầm về trạng thái thành viên, không đồng nhất trạng thái `

**Minh chứng:**
![BUG-06](/submisions/images/BUG-06.png)

**Đề xuất xử lý:**
`Thêm function toLowerCase() trước khi đưa server xử lý`