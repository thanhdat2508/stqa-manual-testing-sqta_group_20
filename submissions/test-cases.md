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

| Mã TC | Mục tiêu kiểm thử                                                                      | Tiền điều kiện                                                       | Bước thực hiện                                                                                | Dữ liệu đầu vào                                    | Kết quả mong đợi                                                                                                                                                                     | REQ    | Kỹ thuật |
| ----- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------ | -------- |
| TC-21 | Tìm kiếm tên sách tồn tại                                                              | Sách đó có tồn tại trên hệ thống                                     | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm tên sách `Linux`                    | Tên sách: `Linux`                                  | Danh sách hiện ra sách có tựa đề chứa `Linux`: `Hệ điều hành Linux`, các sách khác không được trả trong danh sách                                                                    | REQ-03 | EP       |
| TC-22 | Tìm kiếm tên tác giả tồn tại                                                           | Tác giả có sách trên hệ thống                                        | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm tên tác giả `Lý Văn Tài`            | Tên tác giả: `Lý Văn Tài`                          | Danh sách hiện ra các đầu sách của tác giả `Lý Văn Tài`, các đầu sách của tác giả khác không được trả trong danh sách                                                                | REQ-03 | EP       |
| TC-23 | Tìm kiếm tên sách không tồn tại                                                        | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm tên sách không tồn tại `anything`   | Tên sách không tồn tại: `anything`                 | Danh sách trả ra rỗng kèm lời nhắn `Không tìm thấy sách nào`                                                                                                                         | REQ-03 | EP       |
| TC-24 | Tìm kiếm tên sách không tồn tại                                                        | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm tên sách không tồn tại `anything`   | Tên sách không tồn tại: `anything`                 | Danh sách trả ra rỗng kèm lời nhắn `Không tìm thấy sách nào`                                                                                                                         | REQ-03 | EP       |
| TC-25 | Tìm kiếm tên tác giả không tồn tại                                                     | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm tên tác giả không tồn tại `Dat Cao` | Tên tác giả không tồn tại: `Dat Cao`               | Danh sách trả ra rỗng kèm lời nhắn `Không tìm thấy sách nào`                                                                                                                         | REQ-03 | EP       |
| TC-26 | Tìm kiếm với chữ thường (Case-insensitive search)                                      | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm với chữ thường `linux`              | Tìm kiếm với chữ thường: `linux`                   | Danh sách hiện ra sách có tựa đề chứa `Linux`: `Hệ điều hành Linux`, các sách khác không được trả trong danh sách                                                                    | REQ-03 | EP       |
| TC-27 | Tìm kiếm với chữ in hoa (Case-insensitive search)                                      | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Tìm kiếm với chữ thường `LINUX`              | Tìm kiếm với chữ thường: `LINUX`                   | Danh sách hiện ra sách có tựa đề chứa `LINUX`: `Hệ điều hành Linux`, các sách khác không được trả trong danh sách                                                                    | REQ-03 | EP       |
| TC-28 | Lọc sách với thể loại tồn tại                                                          | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Lọc sách với `Công nghệ`                     | Lọc với thể loại: `Công nghệ`                      | Danh sách sách hiện ra các đầu sách có thể loại là `Công nghệ`                                                                                                                       | REQ-03 | EP       |
| TC-29 | Lọc sách với thể loại không tồn tại                                                    | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Lọc sách với `Truyện tranh`                  | Lọc với thể loại: `Truyện tranh`                   | Danh sách trả ra rỗng kèm lời nhắn `Không tìm thấy sách nào`                                                                                                                         | REQ-03 | EP       |
| TC-30 | Lọc sách với thể loại được in thường (Case-insensitive search)                         | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Lọc sách với `công nghệ`                     | Lọc với thể loại: `công nghệ`                      | Danh sách sách hiện ra các đầu sách có thể loại là `Công nghệ`                                                                                                                       | REQ-03 | EP       |
| TC-31 | Vừa tìm kiếm vừa lọc thể loại sách khi cả 2 đều tồn tại **`SRS GAP`**                  | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Lọc sách với `Công nghệ` và tìm kiếm `Linux` | Lọc với thể loại: `Công nghệ`, Tìm kiếm `Linux`    | TH1: Danh sách hiển thị tất cả sách chứa Linux và tất cả sách thuộc thể loại Công nghệ **(OR)**. TH2: Chỉ hiển thị đầu sách có chứa `Linux` và thuộc thể loại `Công nghệ` **(AND)**  | REQ-03 | EP       |
| TC-32 | Vừa tìm kiếm vừa lọc thể loại sách khi 1 trong 2 hoặc cả 2 không tồn tại **`SRS GAP`** | Đã đăng nhập vào hệ thống bằng tài khoản hợp lệ và đang ở trang Sách | Bước 1: Đăng nhập bằng tài khoản hợp lệ. Bước 2: Lọc sách với `Công nghệ` và tìm kiếm `Linux` | Lọc với thể loại: `Truyện tranh`, Tìm kiếm `Linux` | TH1: Danh sách hiển thị tất cả sách chứa Linux và tất cả sách thuộc thể loại Công nghệ **(OR)**. TH2: Trả về danh sách rỗng và hiển thị lời nhắn `Không tìm thấy sách nào` **(AND)** | REQ-03 | EP       |

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
