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

## BUG-16

| Thuộc tính          | Chi tiết          |
| ------------------- | ----------------- |
| **Mã lỗi**          | BUG-16            |
| **TC liên quan**    | ``                |
| **REQ liên quan**   | `REQ-03`          |
| **Mức độ**          | `low`             |
| **Người phát hiện** | `Hoàng Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`      |
| **Trạng thái**      | `Open`            |

**Tiêu đề:**
`Lỗi dịch phân loại (Category) khi chuyển tiếng anh vẫn để nguyên là tiếng việt`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Anh

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, chuyển giao diên sang tiếng anh`

**Bước tái hiện:**

1. `Đăng nhập tài khoàn thành công `
2. `Chuyển giao diện sang tiếng anh`
   **Kết quả mong đợi:**
   `Mong đợi khi chuyển giao diện sang tiếng anh toàn bộ trang web chuyển sang tiếng anh `

**Kết quả thực tế:**
`Lỗi hệ thống khi chuyển sang tiếng anh nhưng "avaliable categories:Công nghệ, giáo dục, kinh tế,kĩ năng mềm, quản trị,văn học" vẫn đang là tiếng việt`

**Tác động:**
`Gây khó khăn khi người dùng muốn dùng tiếng anh mà hệ thống vẫn có chỗ ghi tiếng việt`

**Minh chứng:**
![BUG-16](/submisions/images/BUG-16.png)
**Đề xuất xử lý:**
`Thay đổi chuyển toàn bộ sang tiếng anh `
