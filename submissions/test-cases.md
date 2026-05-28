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

### REQ-07 — Quản lý thành viên

| Mã TC     | Mục tiêu kiểm thử                                                                | Tiền điều kiện                                                                                              | Bước thực hiện                                                                                                                                                                                                 | Dữ liệu đầu vào                                                       | Kết quả mong đợi                                                                                       | REQ    | Kỹ thuật |
| :-------- | :------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------- | :----- | :------- |
| **TC-70** | Thủ thư thêm thành viên mới hợp lệ                                               | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên.<br>Bước 3: Nhấn Thêm thành viên.<br>Bước 4: Nhập đầy đủ Họ tên, Email, SĐT hợp lệ.<br>Bước 5: Nhấn Xác nhận.                     | Họ tên: `Nguyễn Test`, Email: `newmember@test.com`, SĐT: `0912345678` | Thành viên mới được tạo thành công và xuất hiện trong danh sách thành viên                             | REQ-07 | EP       |
| **TC-71** | Thêm thành viên với email thiếu dấu chấm trong domain                            | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên → Thêm thành viên.<br>Bước 3: Nhập Email thiếu dấu chấm trong phần domain.<br>Bước 4: Nhấn Xác nhận.                              | Email: `user@domain`                                                  | Hệ thống từ chối và hiển thị thông báo email không hợp lệ (thiếu dấu '.' trong domain)                 | REQ-07 | EP       |
| **TC-72** | Thêm thành viên với email đã tồn tại                                             | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và tài khoản `ba.nguyen@email.com` đã có sẵn trên hệ thống | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên → Thêm thành viên.<br>Bước 3: Nhập Email đã tồn tại trong hệ thống.<br>Bước 4: Nhấn Xác nhận.                                     | Email: `ba.nguyen@email.com`                                          | Hệ thống từ chối và hiển thị thông báo email đã tồn tại                                                | REQ-07 | EP       |
| **TC-73** | Thêm thành viên với email hợp lệ ở mức biên tối thiểu                            | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập Thêm thành viên.<br>Bước 3: Nhập Email có độ dài ngắn nhất nhưng chứa đủ ký tự `@` và dấu `.`.<br>Bước 4: Nhấn Xác nhận.                         | Email: `a@b.c`                                                        | Thành viên được tạo thành công — email `a@b.c` hợp lệ theo hệ thống                                    | REQ-07 | BVA      |
| **TC-74** | Thêm thành viên với email thiếu ký tự `@`                                        | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên → Thêm thành viên.<br>Bước 3: Nhập Email không chứa ký tự `@`.<br>Bước 4: Nhấn Xác nhận.                                          | Email: `usertest.com`                                                 | Hệ thống từ chối và hiển thị thông báo định dạng email không hợp lệ (thiếu `@`)                        | REQ-07 | EP       |
| **TC-75** | Thêm thành viên nhưng bỏ trống trường bắt buộc (Email; Họ và Tên; Số Điện Thoại) | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên → Thêm thành viên.<br>Bước 3: Để trống trường Email (SĐT, Họ và Tên) và nhập đầy đủ các trường còn lại.<br>Bước 4: Nhấn Xác nhận. | Email(SĐT; Họ và Tên): `[Bỏ trống]`                                   | Hệ thống từ chối và hiển thị thông báo yêu cầu điền đầy đủ thông tin vào trường Email(SĐT; Họ và Tên)  | REQ-07 | EP       |
| **TC-76** | Kiểm tra phân quyền chức năng Thêm thành viên                                    | Đã đăng nhập vào hệ thống bằng tài khoản có vai trò Thành viên thường                                       | Bước 1: Đăng nhập bằng tài khoản Thành viên thường.<br>Bước 2: Cố gắng tìm nút hoặc truy cập trực tiếp đường dẫn chức năng Thêm thành viên.                                                                    | Vai trò tài khoản: `Thành viên`                                       | Hệ thống không hiển thị tab Thành viên hoặc chặn quyền truy cập trực tiếp kèm thông báo lỗi phân quyền | REQ-07 | EP       |
| **TC-77** | Thêm thành viên với số điện thoại hợp lệ (10 chữ số)                             | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên → Thêm thành viên.<br>Bước 3: Nhập Họ tên, Email hợp lệ và SĐT gồm 10 chữ số bắt đầu bằng 0.<br>Bước 4: Nhấn Xác nhận.            | SĐT: `0987654321`                                                     | Thành viên mới được tạo thành công và xuất hiện trong danh sách                                        | REQ-07 | EP       |
| **TC-78** | Thêm thành viên với số điện thoại chứa chữ cái/ký tự đặc biệt **`SRS GAP`**      | Đã đăng nhập vào hệ thống bằng tài khoản Thủ thư và đang ở trang Thành viên                                 | Bước 1: Đăng nhập bằng tài khoản Thủ thư.<br>Bước 2: Truy cập tab Thành viên → Thêm thành viên.<br>Bước 3: Nhập SĐT có chứa chữ cái hoặc ký tự đặc biệt.<br>Bước 4: Nhấn Xác nhận.                             | SĐT: `0987abc321`                                                     | Hệ thống từ chối và hiển thị thông báo lỗi định dạng số điện thoại (chỉ chấp nhận chữ số)              | REQ-07 | EP       |

### REQ-08 - Tra cứu phiếu mượn

---

## Tổng hợp

| Nhóm chức năng | Số TC             | REQ phủ | Kỹ thuật IDM áp dụng |
| -------------- | ----------------- | ------- | -------------------- |
|                |                   |         |                      |
| **Tổng**       | **<!-- ≥ 20 -->** |         |                      |
