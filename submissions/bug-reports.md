# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-08

| Thuộc tính          | Chi tiết               |
| ------------------- | ---------------------- |
| **Mã lỗi**          | BUG-08                 |
| **TC liên quan**    | `TC-08`                |
| **REQ liên quan**   | `REQ-05`               |
| **Mức độ**          | `High`                 |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt` |
| **Ngày phát hiện**  | `25/05/2026`           |
| **Trạng thái**      | `Open`                 |

**Tiêu đề:**
`Không hiển thị cảnh báo trả sách quá hạn khi trả quá hạn`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt - Tiếng Anh

**Điều kiện tiên quyết:**
`Đã đăng nhập tài khoản thành công, đang có ít nhất 1 cuốn sách quá hạn trả trong danh sách mượn`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thành công`
2. `Bước 2: Vào mục "Sách đang mượn"`
3. `Bước 3: Xác nhận có sách đã quá ngày hạn trả. Bấm "Trả sách" trên cuốn sách quá hạn đó`
4. `Bước 4: Xác nhận trả sách`

**Kết quả mong đợi:**
`Sau khi trả, hệ thống phải hiển thị thông báo cảnh báo kiểu "Sách đã quá hạn X ngày, bạn có thể bị phạt phí" để người dùng biết`

**Kết quả thực tế:**
`Hệ thống xử lý trả sách bình thường, không hiển thị bất kỳ cảnh báo hay thông báo phí phạt nào`

**Tác động:**
`Người dùng không biết mình bị phạt, gây bất ngờ và khiếu nại. Thủ thư không có cơ sở thông báo phí phạt vì hệ thống không ghi nhận. Ảnh hưởng đến tính minh bạch của hệ thống thư viện`

**Minh chứng:**
![BUG-08](/submisions/images/BUG-08.png)

**Đề xuất xử lý:**
`Thêm popup cảnh báo trước khi xác nhận trả sách quá hạn, hiển thị số ngày trễ và mức phí phạt tương ứng`
`Backend cần tính toán và trả về thông tin phí phạt kèm theo response khi trả sách quá hạn`
`Lưu lại lịch sử phạt vào database để thủ thư tra cứu`
