# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-13

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | BUG-13             |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-05`           |
| **Mức độ**          | `Low`              |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Lỗi POPUP khi nhấn 2 lần nút trả sách`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `MacOS`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Tài khoản đủ yêu cầu và có sách đang mượn`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản đang hoạt động`
2. `Bước 2: Vào mục mượn trả`
3. `Bước 3: Nhấn liên tục vào nút trả sách`

**Kết quả mong đợi:**
`Chỉ hiện popup thành công khi nhấn trả sách`

**Kết quả thực tế:**
`Bị lỗi hiển thị popup thành công sau đó xuất hiện luôn popup lỗi`

**Tác động:**
`Gây hiểu nhầm đối với người dùng khi người dùng nhấn quá nhiều vào nút bấm`

**Minh chứng:**
![BUG-13-1](/submisions/images/BUG-13-1.png)
![BUG-13-2](/submisions/images/BUG-13-2.png)

**Đề xuất xử lý:**
`Khi đang xử lý yêu cầu, nút bấm hiển thị có thể disable và thêm dấu hiệu đang xử lý để người dùng biết máy chủ đang xử lý yêu cầu`
