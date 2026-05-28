# Test Cases — Bảng trường hợp kiểm thử

> **Hướng dẫn**: Viết tối thiểu **20 TC** phủ đủ các chức năng chính (REQ-01 → REQ-08).
> Xem [examples/sample-test-case.md](../examples/sample-test-case.md) để hiểu cách viết TC tốt.
> Tự tổ chức và phân nhóm test case theo cách hợp lý nhất.

| Thông tin      |                       |
| -------------- | --------------------- |
| **Nhóm**       | `<!-- Tên nhóm -->`   |
| **Ngày tạo**   | `<!-- DD/MM/YYYY -->` |
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

### REQ-07 — Quản lý thành viên

### REQ-08 - Tra cứu phiếu mượn

| Mã TC     | Mục tiêu kiểm thử                                                 | Tiền điều kiện                                                                                                                         | Bước thực hiện                                                                                                                                                                     | Dữ liệu đầu vào              | Kết quả mong đợi                                                                                                                                         | REQ    | Kỹ thuật |
| :-------- | :---------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------- | :----- | :------- |
| **TC-79** | Kiểm tra quyền Thủ thư: Xem được tất cả phiếu mượn                | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư. Hệ thống đang có dữ liệu phiếu mượn của nhiều thành viên khác nhau.                  | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập chức năng Tra cứu phiếu mượn/Quản lý mượn trả.<br>Bước 3: Quan sát danh sách hiển thị.                               | Không có                     | Danh sách hiển thị toàn bộ phiếu mượn của tất cả các thành viên trong hệ thống.                                                                          | REQ-08 | EP       |
| **TC-80** | Kiểm tra quyền Thành viên: Chỉ xem được phiếu mượn của chính mình | Đã đăng nhập bằng tài khoản Thành viên (VD: `dam.tran@email.com`). Hệ thống có phiếu mượn của tài khoản này và của các tài khoản khác. | Bước 1: Đăng nhập bằng tài khoản Thành viên.<br>Bước 2: Truy cập chức năng Tra cứu phiếu mượn.<br>Bước 3: Quan sát danh sách hiển thị.                                             | Không có                     | Danh sách CHỈ hiển thị các phiếu mượn thuộc về tài khoản `dam.tran@email.com`. Tuyệt đối không hiển thị phiếu của thành viên khác.                       | REQ-08 | EP       |
| **TC-81** | Thành viên cố tình tra cứu phiếu của người khác                   | Đã đăng nhập bằng tài khoản Thành viên. Có mã phiếu mượn hợp lệ của một thành viên khác.                                               | Bước 1: Đăng nhập bằng tài khoản Thành viên.<br>Bước 2: Sử dụng thanh tìm kiếm để tra cứu mã phiếu của người khác, HOẶC nhập trực tiếp URL chi tiết của phiếu đó trên trình duyệt. | Mã phiếu mượn của người khác | Hệ thống chặn truy cập, trả về kết quả rỗng (không tìm thấy) hoặc hiển thị thông báo lỗi "Bạn không có quyền xem phiếu mượn này".                        | REQ-08 | EP       |
| **TC-82** | Kiểm tra hiển thị đầy đủ thông tin trên phiếu mượn                | Đã đăng nhập vào hệ thống (Thủ thư hoặc Thành viên). Có ít nhất 1 phiếu mượn trong danh sách.                                          | Bước 1: Truy cập trang Tra cứu phiếu mượn.<br>Bước 2: Kiểm tra các cột thông tin được hiển thị cho một dòng phiếu mượn bất kỳ.                                                     | Không có                     | Mỗi phiếu mượn hiển thị đầy đủ và chính xác 5 trường thông tin: Mã phiếu, Sách mượn, Ngày mượn, Ngày hết hạn, Trạng thái (Đang mượn / Đã trả / Quá hạn). | REQ-08 | EP       |

---

## Tổng hợp

| Nhóm chức năng | Số TC             | REQ phủ | Kỹ thuật IDM áp dụng |
| -------------- | ----------------- | ------- | -------------------- |
|                |                   |         |                      |
| **Tổng**       | **<!-- ≥ 20 -->** |         |                      |
