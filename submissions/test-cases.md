# Test Cases — Bảng trường hợp kiểm thử

> **Hướng dẫn**: Viết tối thiểu **20 TC** phủ đủ các chức năng chính (REQ-01 → REQ-08).
> Xem [examples/sample-test-case.md](../examples/sample-test-case.md) để hiểu cách viết TC tốt.
> Tự tổ chức và phân nhóm test case theo cách hợp lý nhất.

| Thông tin      |                       |
| -------------- | --------------------- |
| **Nhóm**       | `Nhóm 30`             |
| **Ngày tạo**   | `<!-- 28/05/2026 -->` |
| **Hệ thống**   | https://stqa.rbc.vn   |
| **Tham chiếu** | SRS v1.0              |

---

## Bước 1: Mô hình hóa miền đầu vào — Input Domain Modeling (IDM)

> 📖 **Textbook:** Chương 6 — _Input Domain Modeling_, Paul Ammann & Jeff Offutt.
>
> **Trước khi viết Test Case**, nhóm **phải** phân tích miền đầu vào bằng bảng IDM bên dưới.
> Mỗi chức năng cần xác định: **Đặc tính (Characteristic)**, **Phân vùng (Block/Partition)**, và **Giá trị đại diện (Value)**.

### IDM — Đăng nhập (REQ-01)

| Đặc tính (Characteristic)  | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi             |
| -------------------------- | ----------------- | ------------------------ | ---------------------------- |
| Email có tồn tại trong DB? | Có                | `librarian@library.com`  | Đăng nhập thành công         |
|                            | Không             | `noone@email.com`        | Thông báo lỗi                |
| Mật khẩu có đúng?          | Đúng              | `admin123`               | Đăng nhập thành công         |
|                            | Sai               | `wrongpass`              | Thông báo lỗi                |
| Ô nhập có rỗng?            | Không rỗng        | (giá trị bất kỳ)         | Xử lý bình thường            |
|                            | Rỗng              | `""`                     | Thông báo "Vui lòng nhập..." |

### IDM — Tìm kiếm sách (REQ-03)

| Đặc tính (Characteristic)    | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi                 |
| ---------------------------- | ----------------- | ------------------------ | -------------------------------- |
| Từ khóa có tồn tại trong DB? | Có (tên sách)     | `"Flutter"`              | Hiển thị sách chứa "Flutter"     |
|                              | Có (tên tác giả)  | `"Nguyễn"`               | Hiển thị sách của tác giả Nguyễn |
|                              | Không             | `"XYZ123"`               | Danh sách rỗng                   |
| Phân biệt HOA/thường?        | Chữ thường        | `"flutter"`              | Kết quả giống "Flutter"          |
|                              | Chữ HOA           | `"FLUTTER"`              | Kết quả giống "Flutter"          |

### IDM — Mượn sách (REQ-04, REQ-05)

| Đặc tính (Characteristic) | Phân vùng (Block)   | Giá trị đại diện (Value) | Kết quả mong đợi                 |
| ------------------------- | ------------------- | ------------------------ | -------------------------------- |
| Trạng thái sách?          | Có sẵn              | BOOK001                  | Cho phép mượn                    |
|                           | Đang mượn           | BOOK003                  | Không cho phép                   |
|                           | Thất lạc            | BOOK007                  | Không cho phép                   |
| Trạng thái thành viên?    | Hoạt động           | MEM002                   | Cho phép mượn                    |
|                           | Tạm ngưng           | MEM004                   | Từ chối, thông báo lỗi           |
|                           | Hết hạn             | MEM005                   | Từ chối, thông báo lỗi           |
| Số sách đang mượn?        | < 3 (BVA: 0, 1, 2)  | MEM006 (0 sách)          | Cho phép mượn                    |
|                           | = 3 (BVA: giới hạn) | MEM đã mượn 3 sách       | Từ chối, thông báo vượt giới hạn |

### IDM — `<!-- Nhóm tự bổ sung cho REQ-05 đến REQ-08 -->`

| Đặc tính (Characteristic) | Phân vùng (Block) | Giá trị đại diện (Value) | Kết quả mong đợi |
| ------------------------- | ----------------- | ------------------------ | ---------------- |
| `<!-- Nhóm tự điền -->`   |                   |                          |                  |

> 💡 **Gợi ý kỹ thuật**: Sử dụng **Phân lớp tương đương (EP)** cho các phân vùng rời rạc, **Phân tích giá trị biên (BVA)** cho các phân vùng số (ví dụ: giới hạn 3 sách). Xem textbook §6.1–6.3.

---

## Bước 2: Test Cases

<!-- Tự tổ chức bảng test case: có thể chia nhóm theo chức năng, theo REQ, hoặc theo luồng nghiệp vụ — tùy nhóm quyết định. -->
<!-- Mỗi TC phải ánh xạ ngược về ít nhất 1 dòng trong bảng IDM ở Bước 1. -->

### REQ-01 — Login

| Mã TC | Mục tiêu kiểm thử | Tiền điều kiện | Bước thực hiện | Dữ liệu đầu vào | Kết quả mong đợi | REQ | Kỹ thuật |
| ----- | ----------------- | -------------- | -------------- | --------------- | ---------------- | --- | -------- |
|       |                   |                |                |                 |                  |     |          |

### REQ-02 — Xem danh sách sách

### REQ-03 — Tìm kiếm và lọc sách

### REQ-04 — Mượn sách
| Mã TC | Mục tiêu kiểm thử | Tiền điều kiện | Bước thực hiện | Dữ liệu đầu vào | Kết quả mong đợi | REQ | Kỹ thuật |
| TC-31 | Không thể mượn khi đã đạt giới hạn 3 sách | Đã đăng nhập biet.hoang@email.com; thành viên đang mượn đúng 3 cuốn sách | Bước 1: Xác nhận đang mượn 3 sách. Bước 2: Tìm một cuốn sách có sẵn bất kỳ. Bước 3: Bấm "Mượn sách" | Email: biet.hoang@email.com; Số sách đang mượn: 3/3 | Hệ thống từ chối mượn; hiển thị thông báo "Bạn đã đạt giới hạn 3 sách mượn" | REQ-04 | BVA |

| TC-32 | Không thể mượn sách khi tài khoản bị tạm ngưng | Tài khoản cu.le@email.com (MEM004) đang ở trạng thái "Tạm ngưng" | Bước 1: Đăng nhập cu.le@email.com. Bước 2: Chọn sách Có sẵn bất kỳ. Bước 3: Bấm "Mượn sách" | Email: cu.le@email.com, password: password123 (Tạm ngưng – MEM004) | Hệ thống từ chối với thông báo rõ lý do "Tài khoản đang bị tạm ngưng" | REQ-04 | EP |

| TC-33 | Không thể mượn sách khi tài khoản hết hạn | Tài khoản binh.pham@email.com (MEM005) đang ở trạng thái Hết hạn | Bước 1: Đăng nhập binh.pham@email.com. Bước 2: Chọn sách Có sẵn bất kỳ. Bước 3: Bấm "Mượn sách" | Email: binh.pham@email.com, password: password123 (Hết hạn – MEM005) | Hệ thống từ chối với thông báo rõ lý do "Tài khoản đã hết hạn" | REQ-04 | EP |

| TC-34 | Số lượng sách đang mượn hiển thị đúng trong mục "Thành viên" | Đã đăng nhập librarian@library.com; nhấn vào mục "kiểm tra quá hạn" | Bước 1: Vào mục Thành viên. Bước 2: Kiểm tra số sách đang mượn hiển thị | Email: librarian@library.com | Số sách đang mượn hiển thị đúng và khớp với số thực tế trong "Sách đang mượn" | REQ-04 | EP |

| TC-35 | Hệ thống chỉ xử lý 1 lần khi spam bấm nút "Mượn sách" nhiều lần liên tiếp | Đã đăng nhập biet.hoang@email.com; đang xem chi tiết sách Có sẵn | Bước 1: Vào trang chi tiết sách Có sẵn. Bước 2: Bấm nút "Mượn sách" liên tục 5–10 lần rất nhanh. | Email: biet.hoang@email.com; thao tác: spam click nút Mượn sách | Hệ thống chỉ xử lý đúng 1 lần mượn; không bị trắng màn hình, không mất dữ liệu | REQ-04 | EP |

| Tc-36 | Thông báo lỗi từ chối mượn hiển thị đúng ngôn ngữ giao diện | Đã đăng nhập dam.tran@email.com; giao diện đang bật ngôn ngữ tiếng Anh | Bước 1: Chuyển ngôn ngữ giao diện sang tiếng Anh. Bước 2: Thực hiện thao tác bị từ chối mượn (VD: mượn quá 3 sách). Bước 3: Quan sát popup thông báo lỗi | Email: dam.tran@email.com; ngôn ngữ: tiếng Anh | Popup thông báo lỗi hiển thị đúng ngôn ngữ đang được chọn | REQ-04 | EP |

### REQ-05 — Trả sách

### REQ-06 — Xử lý sách quá hạn

### REQ-07 — Quản lý thành viên

### REQ-08 - Tra cứu phiếu mượn

---

## Tổng hợp

| Nhóm chức năng | Số TC             | REQ phủ | Kỹ thuật IDM áp dụng |
| -------------- | ----------------- | ------- | -------------------- |
|                |                   |         |                      |
| **Tổng**       | **<!-- ≥ 20 -->** |         |                      |
