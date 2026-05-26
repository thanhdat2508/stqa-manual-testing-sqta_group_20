# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---


## BUG-03

| Thuộc tính          | Chi tiết               |
| ------------------- | ---------------------- |
| **Mã lỗi**          | BUG-03                 |
| **TC liên quan**    | `TC-03`                |
| **REQ liên quan**   | `REQ-04`               |
| **Mức độ**          | `Medium`               |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt` |
| **Ngày phát hiện**  | `25/05/2026`           |
| **Trạng thái**      | `Open`                 |

**Tiêu đề:**
`Không đổi ngôn ngữ ở thông báo popup đỏ`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Anh

**Điều kiện tiên quyết:**
`Đã đăng nhập tài khoản người dùng, hệ thống đang cài ngôn ngữ khác tiếng Việt (tiếng Anh)`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập thành công tài khoản`
2. `Bước 2: Vào Settings → đổi ngôn ngữ giao diện sang tiếng Anh`
3. `Bước 3: Thực hiện một thao tác gây ra thông báo popup đỏ`
**Kết quả mong đợi:**
`Popup đỏ hiển thị đúng ngôn ngữ đang được cài đặt trong hệ thống`

**Kết quả thực tế:**
`Popup đỏ vẫn hiển thị nội dung tiếng Việt, không đổi sang ngôn ngữ đã chọn`

**Tác động:**
`Trải nghiệm người dùng không nhất quán — giao diện hiển thị đúng ngôn ngữ nhưng thông báo lỗi thì không, gây khó hiểu cho người dùng không đọc được tiếng Việt`

**Minh chứng:**
![BUG-03](/submisions/images/BUG-03.png)

**Đề xuất xử lý:**
`Các chuỗi text trong popup đỏ cần được đưa vào file localization. Đảm bảo tất cả thông báo lỗi đều tuân theo ngôn ngữ đang được chọn — không hardcode tiếng Việt`
