# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-19

| Thuộc tính          | Chi tiết                |
| ------------------- | ----------------------- |
| **Mã lỗi**          | BUG-19                  |
| **TC liên quan**    | `TC-19`                 |
| **REQ liên quan**   | `REQ-06`                |
| **Mức độ**          | `High`                  |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt`  |
| **Ngày phát hiện**  | `25/05/2026`            |
| **Trạng thái**      | `Open`                  |

**Tiêu đề:**
`Hiển thị sai số lượng sách quá hạn khi nhấn nút lần thứ 2 'Kiểm tra quá hạn'`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt- Tiếng Anh

**Điều kiện tiên quyết:**
`Đã đăng nhập tài khoản thủ thư, hệ thống có ít nhất 1 số sách đang quá hạn, đang ở màn hình quản lý/ kiểm tra quá hạn`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thủ thư thành công`
2. `Bước 2: Vào mục "Kiểm tra quá hạn". Bấm nút "Kiểm tra quá hạn" lần đầu → ghi nhận số lượng sách quá hạn hiển thị`
3. `Bước 3: Bấm nút "Kiểm tra quá hạn" lần thứ 2`

**Kết quả mong đợi:**
`Mỗi lần bấm "Kiểm tra quá hạn" phải trả về cùng một kết quả chính xác nếu dữ liệu không thay đổi`

**Kết quả thực tế:**
`Lần bấm thứ 2 hiển thị số lượng sách quá hạn khác với lần đầu, dù không có thay đổi dữ liệu nào giữa 2 lần bấm`

**Tác động:**
`Thủ thư không biết tin vào kết quả nào — mất độ tin cậy vào hệ thống`
`Có thể dẫn đến bỏ sót sách quá hạn hoặc xử lý nhầm người dùng`
`Ảnh hưởng trực tiếp đến nghiệp vụ quản lý của thủ thư`

**Minh chứng:**
![BUG-19](/submisions/images/BUG-19.png)

**Đề xuất xử lý:**
`Kiểm tra logic xử lý phía frontend: reset danh sách trước mỗi lần gọi API mới, không append thêm vào list cũ`
`Backend cần đảm bảo mỗi lần gọi API trả về snapshot dữ liệu tại thời điểm đó, không bị ảnh hưởng bởi lần gọi trước`
