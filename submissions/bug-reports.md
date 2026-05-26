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

## BUG-12

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | BUG-12             |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-05`           |
| **Mức độ**          | `Medium`             |
| **Người phát hiện** | `Đỗ Hữu Đức` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Người dùng có thể tự ý trả sách mà không cần thủ thư xác nhận.`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt & Tiếng Anh

**Điều kiện tiên quyết:**
`Thành viên đang có sách trong trạng thái "Đang mượn".`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào tài khoản thành viên.`
2. `Bước 2: Truy cập vào mục quản lý sách đang mượn hoặc lịch sử mượn trả`
3. `Bước 3: Nhấn vào nút hoặc thực hiện hành động "Trả sách" từ phía giao diện người dùng.`

**Kết quả mong đợi:**
`Hành động trả sách từ phía người dùng chỉ là gửi "Yêu cầu trả sách". Sách chỉ được tính là đã trả sau khi Thủ thư tiếp nhận, kiểm tra tình trạng sách vật lý và xác nhận trên hệ thống.`

**Kết quả thực tế:**
`Hệ thống cho phép người dùng tự ý bấm trả sách và trạng thái chuyển thành đã trả thành công mà không cần qua bước kiểm tra, xác nhận của thủ thư.`

**Tác động:**
`Sai lệch dữ liệu kho sách vật lý và hệ thống. Thành viên có thể gian lận bằng cách bấm trả trên hệ thống nhưng không trả sách thật, gây thất thoát tài sản của thư viện.`

**Minh chứng:**
![BUG-12](/submisions/images/BUG-12.png)

**Đề xuất xử lý:**
`Chuyển luồng xử lý: Khi user bấm trả sách, trạng thái chuyển thành "Chờ thủ thư xác nhận". Chỉ tài khoản có quyền Thủ thư mới có quyền phê duyệt hoàn thành quy trình trả sách.`

