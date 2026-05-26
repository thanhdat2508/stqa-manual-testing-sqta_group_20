# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm** | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-01

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi** | `BUG-01 `          |
| **TC liên quan** | `TC-01`            |
| **REQ liên quan** | `REQ-01`           |
| **Mức độ** | `High`             |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện** | `25/05/2026`       |
| **Trạng thái** | `Open`             |

**Tiêu đề:**
`Email phân biệt chữ hoa và chữ thường khi đăng nhập`

**Môi trường:**
- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đã tồn tại tài khoản trên hệ thống`

**Bước tái hiện:**

1. `Bước 1: Nhập email với chữ cái in hoa, VD: Ba.nguyen@email.com thay vì ba.nguyen@email.com`
2. `Bước 2: Nhập mật khẩu`
3. `Bước 3: Nhấn đăng nhập`

**Kết quả mong đợi:**
`Hệ thống cho phép đăng nhập thành công (không phân biệt chữ hoa/thường đối với Email)`

**Kết quả thực tế:**
`Hệ thống không nhận diện được tài khoản và báo lỗi đăng nhập`

**Tác động:**
`Ảnh hưởng trực tiếp đến trải nghiệm người dùng khi đăng nhập`

**Minh chứng:**
![BUG-01](./images/BUG-01.png)

**Đề xuất xử lý:**
`Thêm function toLowerCase() để biến hết tất cả email được truyền từ user sang kiểu lowercase, sau đó mới đưa cho logic đăng nhập xử lý`

---

## BUG-02

| Thuộc tính          | Chi tiết                   |
| ------------------- | -------------------------- |
| **Mã lỗi** | `BUG-02`                   |
| **TC liên quan** | `TC-xx`                    |
| **REQ liên quan** | `REQ-04`                   |
| **Mức độ** | `High`                     |
| **Người phát hiện** | `Nguyen Cao Hoang Dat`     |
| **Ngày phát hiện** | `25/05/2026`               |
| **Trạng thái** | `Open`                     |

**Tiêu đề:**
`Mượn quá số sách cho phép`

**Môi trường:**
- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, hệ thống đang ở trạng thái đã mượn đúng 3 sách (đạt giới hạn tối đa cho phép), dữ liệu chưa reset.`

**Bước tái hiện:**
1. `Đăng nhập tài khoàn thành công`
2. `Mượn lần lượt 3 cuốn sách bất kỳ còn trong kho`
3. `Tìm thêm 1 cuốn sách bất kỳ còn trong kho, bấm "Mượn sách" trên cuốn thứ 4`

**Kết quả mong đợi:**
`Hệ thống báo lỗi đã đạt giới hạn mượn sách tối đa (3 sách) và không cho phép mượn tiếp cuốn thứ 4`

**Kết quả thực tế:**
`Hệ thống vẫn cho phép mượn cuốn thứ 4, không có thông báo chặn nào xuất hiện.`

**Tác động:**
`Vi phạm quy tắc nghiệp vụ cốt lõi, cho phép mượn vượt giới hạn`

**Minh chứng:**
![BUG-02](./images/BUG-02.png)

**Đề xuất xử lý:**
`Kiểm tra số sách đang mượn hiện tại của người dùng trước khi hiển thị nút "Mượn sách". Nếu đã đạt 3 cuốn → vô hiệu hóa nút hoặc ẩn nút "Mượn sách"`

---

## BUG-03

| Thuộc tính          | Chi tiết               |
| ------------------- | ------------------ |
| **Mã lỗi** | `BUG-03`               |
| **TC liên quan** | `TC-03`                |
| **REQ liên quan** | `REQ-04`               |
| **Mức độ** | `Medium`               |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt` |
| **Ngày phát hiện** | `25/05/2026`           |
| **Trạng thái** | `Open`                 |

**Tiêu đề:**
`Không đổi ngôn ngữ ở thông báo popup đỏ`

**Môi trường:**
- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Anh

**Điều kiện tiên quyết:**
`Đã đăng nhập tài khoản người dùng, hệ thống đang cài ngôn ngữ khác tiếng Việt (tiếng Anh)`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập thành công tài khoản`
2. `Bước 2: Vào Settings → đổi ngôn ngữ giao diện sang tiếng Anh`
3. `Bước 3: Thực hiện một thao tác gây ra thông báo popup đỏ`

**Kết quả mong đợi:**
`Popup đỏ hiển thị đúng ngôn ngữ đang được cài đặt trong hệ thống`

**Kết quả thực tế:**
`Popup đỏ vẫn hiển thị nội dung tiếng Việt, không đổi sang ngôn ngữ đã chọn`

**Tác động:**
`Trải nghiệm người dùng không nhất quán — giao diện hiển thị đúng ngôn ngữ nhưng thông báo lỗi thì không, gây khó hiểu cho người dùng không đọc được tiếng Việt`

**Minh chứng:**
![BUG-03](/submisions/images/BUG-03.png)

**Đề xuất xử lý:**
`Các chuỗi text trong popup đỏ cần được đưa vào file localization. Đảm bảo tất cả thông báo lỗi đều tuân theo ngôn ngữ đang được chọn — không hardcode tiếng Việt`

---

## BUG-04

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi** | `BUG-04`           |
| **TC liên quan** | `TC-01`            |
| **REQ liên quan** | `REQ-03`           |
| **Mức độ** | `Cao`              |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện** | `26/05/2026`       |
| **Trạng thái** | `Open`             |

**Tiêu đề:**
`Filter bị phân biệt chữ hoa và chữ thường`

**Môi trường:**
- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đăng nhập vào hệ thống thành công và vào được trang Sách`

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

---

## BUG-05

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi** | `BUG-05`           |
| **TC liên quan** | `TC-01`            |
| **REQ liên quan** | `REQ-06`           |
| **Mức độ** | `High`             |
| **Người phát hiện** | `Bùi Mạnh Hiếu`    |
| **Ngày phát hiện** | `25/05/2026`       |
| **Trạng thái** | `Open`             |

**Tiêu đề:**
`Lỗi popup thông báo về trạng thái tài khoản, tài khoảng "Tạm ngưng" nhưng báo bị "Hết Hạn"`

**Môi trường:**
- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đăng nhập và sử dụng tài khoản trạng thái "Tạm ngưng"`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào tài khoản có trạng thái "Tạm ngưng"`
2. `Bước 2: Mượn sách`

**Kết quả mong đợi:**
`Mong đợi hệ thống thông báo popup sẽ hiện cảnh báo riêng cho từng loại tài khoản`

**Kết quả thực tế:**
`Thông báo lỗi sai trạng thái tài khoản`

**Tác động:**
`Gây hiểu nhầm về trạng thái thành viên, không đồng nhất trạng thái`

**Minh chứng:**
![BUG-05](./images/BUG-05.png)

**Đề xuất xử lý:**
`Kiểm tra chính xác enum hoặc chuỗi điều kiện trạng thái tài khoản trả về từ API trước khi hiển thị text trên popup thông báo, tránh hardcode chung một câu thông báo lỗi.`
