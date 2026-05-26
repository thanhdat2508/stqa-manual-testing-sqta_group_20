# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-15

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | BUG-15             |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-05`           |
| **Mức độ**          | `High`             |
| **Người phát hiện** | `Đỗ Hữu Đức` |
| **Ngày phát hiện**  | `26/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Cho phép thành viên tự ý gia hạn sách của người khác.`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt & Tiếng Anh

**Điều kiện tiên quyết:**
`Tài khoản thành viên đã đăng nhập vào hệ thống.`
`Có một thành viên khác (Thành viên B) đang mượn sách và lộ mã mượn hoặc ID lượt mượn.`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào hệ thống bằng tài khoản của thành viên A.`
2. `Bước 2: Truy cập vào mục Mượn/Trả (Tra cứu phiếu mượn) và nhập mã của thành viên B.`
3. `Bước 2: Tiến hành trả sách.`

**Kết quả mong đợi:**
`Hệ thống phải chặn hành động này lại và báo lỗi phân quyền. Chỉ chính chủ tài khoản đang mượn sách (hoặc Thủ thư) mới có quyền gửi yêu cầu hoặc thực hiện thao tác trả sách đó.`

**Kết quả thực tế:**
`Hệ thống cho phép thành viên A tự ý bấm trả sách (hoặc gửi lệnh trả sách thành công) cho các cuốn sách mà thành viên B đang mượn.`

**Tác động:**
`Phá hoại dữ liệu mượn trả của người khác. Gây lỗi logic nghiêm trọng trong quản lý quy trình mượn sách, khiến thành viên B bị mất sách trên thực tế nhưng trên hệ thống lại ghi nhận là đã trả, gây tranh chấp và khó khăn cho thủ thư khi đối chiếu kho.`

**Minh chứng:**
![BUG-15](/submisions/images/BUG-15.png)

**Đề xuất xử lý:**
`Bổ sung kiểm tra quyền sở hữu ở Backend đối với API xử lý trả sách: Đảm bảo CurrentUserID của session đăng nhập phải trùng khớp với UserID của người đang mượn cuốn sách đó, nếu không phải trả về lỗi.`
