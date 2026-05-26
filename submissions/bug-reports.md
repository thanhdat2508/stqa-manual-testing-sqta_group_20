# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-02

| Thuộc tính | Chi tiết |
|-----------|---------|
| **Mã lỗi** | BUG-02|
| **TC liên quan** | `<!-- TC-xx -->` |
| **REQ liên quan** | `<!-- REQ-04 -->` |
| **Mức độ** | `<!-- High -->` |
| **Người phát hiện** | `<!-- Nguyen Cao Hoang Dat -->`|
| **Ngày phát hiện** | `<!-- 25/05/2026-->` |
| **Trạng thái** | `<!-- Open -->` |

**Tiêu đề:**
`<!-- Mượn quá số sách cho phép  -->`

**Môi trường:**
- Trình duyệt: Chrome `<!-- Version 148.0.7778.179 -->`
- Hệ điều hành: `<!-- Window -->`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`<!-- Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, hệ thống đang ở trạng thái đã mượn đúng 3 sách (đạt giới hạn tối đa cho phép), dữ liệu chưa reset. -->`

**Bước tái hiện:**
1. `<!-- Đăng nhập tài khoàn thành công -->`
2. `<!-- Mượn lần lượt 3 cuốn sách bất kỳ còn trong kho -->`
3. `<!-- Tìm thêm 1 cuốn sách bất kỳ còn trong kho, bấm "Mượn sách" trên cuốn thứ 4 -->`

**Kết quả mong đợi:**
`<!-- Đã đạt giới hạn mượn sách tối đa (3 sách) -->`

**Kết quả thực tế:**
`<!-- Hệ thống vẫn cho phép mượn cuốn thứ 4, không có thông báo chặn nào xuất hiện. -->`

**Tác động:**
`<!--  Vi phạm quy tắc nghiệp vụ cốt lõi, cho phép mượn vượt giới hạn -->`

**Minh chứng:**
![BUG-02](./images/BUG-02.png)

**Đề xuất xử lý:**
`<!-- Kiểm tra số sách đang mượn hiện tại của người dùng trước khi hiển thị nút "Mượn sách". Nếu đã đạt 3 cuốn → vô hiệu hóa nút hoặc ẩn nút "Mượn sách" -->` 

---
