# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-07


| Thuộc tính | Chi tiết |
|-----------|---------|
| **Mã lỗi** | BUG-07 |
| **TC liên quan** | `<!-- TC-xx -->` |
| **REQ liên quan** | `<!-- REQ-05 -->` |
| **Mức độ** | `<!-- High -->` |
| **Người phát hiện** | `<!-- Đỗ Hữu Đức -->` |
| **Ngày phát hiện** | `<!-- 25/05/2026 -->` |
| **Trạng thái** | `<!-- Open -->` |

**Tiêu đề:**

`<!-- Các thành viên có thể tra cứu mã của nhau. -->`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: `Tiếng Việt & Tiếng Anh`

**Điều kiện tiên quyết:**

`<!-- Tài khoản thành viên đã đăng nhập vào hệ thống. -->`
`<!-- Hệ thống có chức năng quản lý mã mượn sách/mã thành viên.. -->`

**Bước tái hiện:**

1. `<!-- Đăng nhập vào hệ thống bằng tài khoản thành viên VD:biet.hoang@email.com . -->`
2. `<!-- Truy cập vào chức năng tra cứu hoặc tìm kiếm thông tin thành viên/mã mượn sách. -->`
3. `<!-- Thực hiện tìm kiếm thông tin hoặc mã của thành viên B VD: Nhập mã MEM002 của tài khoản ba.nguyen@email.com. -->`

**Kết quả mong đợi:**
`<!-- Chỉ xem phiếu mượn của chính mình. KHÔNG được xem phiếu mượn của thành viên khác -->`

**Kết quả thực tế:**
`<!-- Hệ thống cho phép các thành viên dễ dàng tra cứu mã của nhau. -->`

**Tác động:**
`<!-- Gây rủi ro bảo mật thông tin tài khoản, vi phạm quy tắc định danh cá nhân -->`

**Minh chứng:**
`<!-- ![BUG-07](./images/BUG-07.png) -->`

**Đề xuất xử lý:**
`<!-- Phân quyền lại chức năng tra cứu mã thành viên (chỉ dành cho Thủ thư/Admin) -->` 

---
