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

### REQ-05 — Trả sách

### REQ-06 — Xử lý sách quá hạn

| Mã TC | Mục tiêu kiểm thử                                    | Tiền điều kiện                                                               | Bước thực hiện                                                                                                                              | Dữ liệu đầu vào                                                       | Kết quả mong đợi                                                                                                   | REQ    | Kỹ thuật |
| ----- | ---------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------ | -------- |
| TC 61 | kiểm tra phiều quá hạn một ngày                      | Hệ thống có phiều mượn chưa trả                                              | 1.Đăng nhập thành công bằng tài khoản thủ thư vào hệ thống 2.Chọn chức năng "kiểm tra sách quá hạn"                                         | Hạn trả: 20/05/2026, Ngày hiện tại: 21/05/2026                        | Hệ thống đánh dấu phiếu mượn là "Quá hạn".                                                                         | REQ-06 | BVA      |
| TC 62 | Kiểm tra phiếu mượn đúng hạn                         | Hệ thống có phiếu mượn chưa trả                                              | 1. Đăng nhập thành công bằng tài khoản thủ thư vào hệ thống. 2. Chọn chức năng "Kiểm tra sách quá hạn".                                     | Hạn trả: 20/05/2026, Ngày hiện tại: 20/05/2026                        | Hệ thống không đánh dấu phiếu mượn là "Quá hạn".                                                                   | REQ-06 | BVA      |
| TC 63 | Kiểm tra phiếu mượn chưa đến hạn trả                 | Hệ thống có phiếu mượn chưa trả                                              | 1. Đăng nhập thành công bằng tài khoản thủ thư vào hệ thống. 2. Chọn chức năng "Kiểm tra sách quá hạn".                                     | Hạn trả: 25/05/2026, Ngày hiện tại: 20/05/2026                        | Hệ thống không đánh dấu phiếu mượn là "Quá hạn".                                                                   | REQ-06 | BVA      |
| TC 64 | Kiểm tra cập nhật trạng thái phiếu quá hạn           | Đăng nhập bằng tài khoản Thủ thư. Tồn tại phiếu mượn chưa trả và đã quá hạn. | 1. Đăng nhập thành công bằng tài khoản thủ thư vào hệ thống. 2. Truy cập màn hình "Tất cả phiếu mượn". 3. Nhấn nút "Kiểm tra sách quá hạn". | Mã phiếu: BR001. Hạn trả: 15/09/2024. Trạng thái hiện tại: Đang mượn. | Hệ thống cập nhật trạng thái phiếu BR001 từ "Đang mượn" thành "Quá hạn" và hiển thị thông báo cập nhật thành công. | REQ-06 | EP,BVA   |
| TC 65 | Kiểm tra hiển thị danh sách phiếu mượn quá hạn       | Kiểm tra hiển thị danh sách phiếu mượn quá hạn                               | 1.Đăng nhập thành công bằng tài khoản thủ thư 2. Chọn mục "kiểm tra sách quá hạn"                                                           | Danh sách gồm BR001 (quá hạn), BR002 (còn hạn), BR003 (quá hạn)       | Hệ thống chỉ hiển thị BR001 và BR003 trong danh sách quá hạn.                                                      | REQ-06 | EP       |
| TC 66 | Kiểm tra khi không có phiếu mượn quá hạn             | Tất cả phiếu mượn đều còn hạn                                                | 1. Đăng nhập thành công bằng tài khoản thủ thư vào hệ thống. 2. Chọn chức năng "Kiểm tra sách quá hạn".                                     | Danh sách phiếu mượn còn hạn                                          | Hệ thống hiển thị thông báo "Không có sách quá hạn".                                                               | REQ-06 | EP       |
| TC 67 | Kiểm tra phiếu mượn đã trả không bị đánh dấu quá hạn | Có phiếu mượn trạng thái "Đã trả"                                            | 1. Đăng nhập thành công bằng tài khoản thủ thư vào hệ thống. 2. Chọn chức năng "Kiểm tra sách quá hạn".                                     | BR002 - Trạng thái: Đã trả                                            | Hệ thống không đưa BR002 vào danh sách sách quá hạn.                                                               | REQ-06 | EP       |

### REQ-07 — Quản lý thành viên

### REQ-08 - Tra cứu phiếu mượn

---

## Tổng hợp

| Nhóm chức năng | Số TC             | REQ phủ | Kỹ thuật IDM áp dụng |
| -------------- | ----------------- | ------- | -------------------- |
|                |                   |         |                      |
| **Tổng**       | **<!-- ≥ 20 -->** |         |                      |
