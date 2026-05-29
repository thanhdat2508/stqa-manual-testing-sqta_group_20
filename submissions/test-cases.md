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

| TC-11 | Hiển thị danh sách tất cả sách trong thư viện | Đã đăng nhập tài khoản thành viên hợp lệ | Bước 1: Đăng nhập thành công. Bước 2: Vào trang danh sách sách. Bước 3: Quan sát danh sách hiển thị | "biet.hoang@email.com" và password: password123" | Hiển thị đầy đủ danh sách sách, không bị trống hay lỗi | REQ-02 | EP    |

| TC-12 | Mỗi sách hiển thị đủ thông tin: tên, tác giả, thể loại, năm XB, trạng thái | Đã đăng nhập, đang xem danh sách sách | Bước 1: Vào danh sách sách. Bước 2: Quan sát thông tin từng cuốn sách. Bước 3: Kiểm tra đủ 5 trường thông tin | Sách mẫu: BOOK001 – Lập trình Flutter cơ bản | Mỗi sách hiển thị đủ: Tên sách, Tác giả, Thể loại, Năm xuất bản, Trạng thái | REQ-02 | EP |

| TC-13 | Sách đang được mượn hiển thị trạng thái "Đang mượn" | Đã đăng nhập, trong phần danh sách sách | Bước 1: Tìm BOOK003 và BOOK013 | BOOK003: đã mượn bởi MEM002. BOOK013: đã mượn bởi MEM006 | Cả hai sách hiển thị trạng thái "Đang mượn" | REQ-02 | EP |

| TC-14 | Sách thất lạc hiển thị đúng trạng thái "Thất lạc" | Đã đăng nhập, trong phần danh sách sách | Bước 1: Tìm BOOK007 và BOOK020 | BOOK007 và BOOK020: Thất lạc | Cả hai sách hiển thị trạng thái "Thất lạc" | REQ-02 | BVA |


### REQ-03 — Tìm kiếm và lọc sách

### REQ-04 — Mượn sách

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
