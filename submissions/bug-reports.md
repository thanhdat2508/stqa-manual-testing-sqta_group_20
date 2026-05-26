# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-04

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | `BUG-04`           |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-03`           |
| **Mức độ**          | `Cao`              |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện**  | `26/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Filter bị phân biệt chữ hoa và chữ thường`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `MacOS`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đăng nhập vào hệ thống thành công và vào được trang ```Sách``` `

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào hệ thống ( Bất kỳ tài khoản nào )`
2. `Bước 2: Tìm kiếm theo filter không in hoa`

**Kết quả mong đợi:**
`Mong đợi ra được kết quả các sách có cùng thể loại dù lọc theo thể loại in hoa hay không in hoa`

**Kết quả thực tế:**
`Không ra kết quả danh sách sách với thể loại được lọc`

**Tác động:**
`Gây ảnh hưởng đến việc tìm kiếm sản phẩm`

**Minh chứng:**
![BUG-04](./images/BUG-04.png)

**Đề xuất xử lý:**
`Lấy filter từ user sau đó sử dụng function toLowerCase() để chuyển thành dạng viết thường. Sau đó mới đưa có function logic xử lý`
