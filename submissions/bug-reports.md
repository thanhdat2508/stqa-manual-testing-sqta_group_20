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

## BUG-10

| Thuộc tính          | Chi tiết          |
| ------------------- | ----------------- |
| **Mã lỗi**          | BUG-10            |
| **TC liên quan**    | ``                |
| **REQ liên quan**   | `REQ-04`          |
| **Mức độ**          | `low`             |
| **Người phát hiện** | `Hoàng Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`      |
| **Trạng thái**      | `Open`            |

**Tiêu đề:**
`Lỗi hiển thị số sách đang mượn ở mục Thành Viên, quá hạn đang mượn nhưng vẫn là đang mượn:0`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, hệ thống đang ở mục Mượn/Trả`

**Bước tái hiện:**

1. `Đăng nhập tài khoàn thành công`
2. `Mượn một cuốn sách bất kì`
   **Kết quả mong đợi:**
   `Mong đợi khi mượn quá hạn hệ thống thông báo đã quá hạn`

**Kết quả thực tế:**
`Lỗi hệ thống sách quá hạn vẫn hiện thị là đang mượn:0`

**Tác động:**
`Gây hiểu lầm và chưa phân biệt sách đang mượn và quá hạn cho người dùng`

**Minh chứng:**
![BUG-10](./images/BUG-10/BUG-1O_01.png)
![BUG-10](./images/BUG-10/BUG-1O_02.png)

**Đề xuất xử lý:**
`So sách time hiện tại và time trả sách. Nếu như time hiện tại nhỏ hơn hoặc bằng time trả sánh thì hiện thị là đang mượn và ngược lại`
