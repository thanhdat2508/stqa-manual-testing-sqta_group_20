# Bug Reports — Báo cáo lỗi

> **Hướng dẫn**: Tạo 1 mục bug cho mỗi TC có kết quả **Fail**.
> Xem [examples/sample-bug-report.md](../examples/sample-bug-report.md) để hiểu cách viết bug report tốt.
> Mỗi bug cần: tiêu đề mô tả hành vi lỗi, bước tái hiện, expected vs actual, severity + giải thích.

| Thông tin        |              |
| ---------------- | ------------ |
| **Nhóm**         | `Group 30`   |
| **Ngày báo cáo** | `25/05/2026` |

---

## BUG-01

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | `BUG-01 `          |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-01`           |
| **Mức độ**          | `High`             |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

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

| Thuộc tính          | Chi tiết               |
| ------------------- | ---------------------- |
| **Mã lỗi**          | `BUG-02`               |
| **TC liên quan**    | `TC-xx`                |
| **REQ liên quan**   | `REQ-04`               |
| **Mức độ**          | `High`                 |
| **Người phát hiện** | `Nguyen Cao Hoang Dat` |
| **Ngày phát hiện**  | `25/05/2026`           |
| **Trạng thái**      | `Open`                 |

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
`Hệ thống báo lỗi đã đạt giới hạn mượn sách tối đa (3 sách) and không cho phép mượn tiếp cuốn thứ 4`

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
| ------------------- | ---------------------- |
| **Mã lỗi**          | `BUG-03`               |
| **TC liên quan**    | `TC-03`                |
| **REQ liên quan**   | `REQ-04`               |
| **Mức độ**          | `Medium`               |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt` |
| **Ngày phát hiện**  | `25/05/2026`           |
| **Trạng thái**      | `Open`                 |

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

| Thuộc tính          | Chi tiết        |
| ------------------- | --------------- |
| **Mã lỗi**          | `BUG-05`        |
| **TC liên quan**    | `TC-01`         |
| **REQ liên quan**   | `REQ-06`        |
| **Mức độ**          | `High`          |
| **Người phát hiện** | `Bùi Mạnh Hiếu` |
| **Ngày phát hiện**  | `25/05/2026`    |
| **Trạng thái**      | `Open`          |

**Tiêu đề:**
`Lỗi popup thông báo về trạng thái tài khoản, tài khoảng "Tạm ngưng" nhưng báo bị "Hết Hạn"`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đã đăng nhập và sử dụng tài khoản trạng thái "Tạm ngưng"`

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

---

## BUG-07

| Thuộc tính          | Chi tiết     |
| ------------------- | ------------ |
| **Mã lỗi**          | `BUG-07`     |
| **TC liên quan**    | `TC-xx`      |
| **REQ liên quan**   | `REQ-05`     |
| **Mức độ**          | `High`       |
| **Người phát hiện** | `Đỗ Hữu Đức` |
| **Ngày phát hiện**  | `25/05/2026` |
| **Trạng thái**      | `Open`       |

**Tiêu đề:**
`Các thành viên có thể tự do tra cứu mã của nhau`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: `Tiếng Việt & Tiếng Anh`

**Điều kiện tiên quyết:**
`Tài khoản thành viên đã đăng nhập vào hệ thống và hệ thống đang kích hoạt chức năng quản lý mã mượn sách/mã thành viên.`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào hệ thống bằng tài khoản thành viên (VD: biet.hoang@email.com)`
2. `Bước 2: Truy cập vào chức năng tra cứu hoặc tìm kiếm thông tin thành viên/mã mượn sách`
3. `Bước 3: Thực hiện tìm kiếm thông tin hoặc mã của thành viên khác (VD: Nhập mã MEM002 của tài khoản ba.nguyen@email.com)`

**Kết quả mong đợi:**
`Thành viên chỉ được phép xem phiếu mượn của chính mình và hoàn toàn KHÔNG được quyền xem phiếu mượn của thành viên khác.`

**Kết quả thực tế:**
`Hệ thống không chặn quyền, cho phép các thành viên dễ dàng tra cứu thông tin và mã mượn sách of nhau.`

**Tác động:**
`Gây rủi ro nghiêm trọng về bảo mật thông tin tài khoản, vi phạm quy tắc định danh cá nhân và rò rỉ dữ liệu người dùng.`

**Minh chứng:**
![BUG-07](./images/BUG-07.png)

**Đề xuất xử lý:**
`Thực hiện phân quyền nghiêm ngặt ở cả Client-side (ẩn ô tìm kiếm của user khác) lẫn Server-side (kiểm tra session/token, nếu ID yêu cầu tra cứu không trùng với ID đăng nhập và không phải role Thủ thư/Admin thì lập tức từ chối request).`

---

## BUG-08

| Thuộc tính          | Chi tiết               |
| ------------------- | ---------------------- |
| **Mã lỗi**          | `BUG-08`               |
| **TC liên quan**    | `TC-08`                |
| **REQ liên quan**   | `REQ-05`               |
| **Mức độ**          | `High`                 |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt` |
| **Ngày phát hiện**  | `25/05/2026`           |
| **Trạng thái**      | `Open`                 |

**Tiêu đề:**
`Không hiển thị cảnh báo trả sách quá hạn khi trả quá hạn`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt - Tiếng Anh

**Điều kiện tiên quyết:**
`Đã đăng nhập tài khoản thành công, đang có ít nhất 1 cuốn sách quá hạn trả trong danh sách mượn`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thành công`
2. `Bước 2: Vào mục "Sách đang mượn"`
3. `Bước 3: Xác nhận có sách đã quá ngày hạn trả. Bấm "Trả sách" trên cuốn sách quá hạn đó`
4. `Bước 4: Xác nhận trả sách`

**Kết quả mong đợi:**
`After returning, the system must display a warning notification like "Book is overdue by X days, you may be fined" so users are aware`

**Kết quả thực tế:**
`Hệ thống xử lý trả sách bình thường, không hiển thị bất kỳ cảnh báo hay thông báo phí phạt nào`

**Tác động:**
`Người dùng không biết mình bị phạt, gây bất ngờ và khiếu nại. Thủ thư không có cơ sở thông báo phí phạt vì hệ thống không ghi nhận. Ảnh hưởng đến tính minh bạch của hệ thống thư viện`

**Minh chứng:**
![BUG-08](/submisions/images/BUG-08.png)

**Đề xuất xử lý:**
`Thêm popup cảnh báo trước khi xác nhận trả sách quá hạn, hiển thị số ngày trễ và mức phí phạt tương ứng. Đồng thời Backend cần tính toán và trả về thông tin phí phạt kèm theo response khi trả sách quá hạn và lưu lại lịch sử phạt vào database để thủ thư tra cứu.`

---

## BUG-10

| Thuộc tính          | Chi tiết          |
| ------------------- | ----------------- |
| **Mã lỗi**          | `BUG-10`          |
| **TC liên quan**    | `TC-xx`           |
| **REQ liên quan**   | `REQ-04`          |
| **Mức độ**          | `Low`             |
| **Người phát hiện** | `Hoàng Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`      |
| **Trạng thái**      | `Open`            |

**Tiêu đề:**
`Lỗi hiển thị số sách đang mượn ở mục Thành Viên, quá hạn đang mượn nhưng vẫn hiển thị là đang mượn: 0`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, hệ thống đang ở mục Mượn/Trả`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thành công`
2. `Bước 2: Mượn một cuốn sách bất kỳ và để trạng thái rơi vào quá hạn.`

**Kết quả mong đợi:**
`Khi có sách quá hạn, hệ thống cần có cơ chế đếm riêng hoặc hiển thị thông báo trạng thái "Quá hạn" rõ ràng thay vì bỏ qua bộ đếm.`

**Kết quả thực tế:**
`Lỗi hệ thống khi sách rơi vào trạng thái quá hạn vẫn hiển thị số lượng sách đang mượn là: 0.`

**Tác động:**
`Gây hiểu nhầm, không phân biệt rõ ràng giữa sách đang mượn trong hạn và sách đã quá hạn cho người dùng quản lý.`

**Minh chứng:**
![BUG-10](./images/BUG-10/BUG-1O_01.png)
![BUG-10](./images/BUG-10/BUG-1O_02.png)

**Đề xuất xử lý:**
`Thực hiện so sánh thời gian hiện tại (Current Timestamp) và hạn trả sách (Due Date). Nếu thời gian hiện tại lớn hơn hạn trả sách, hệ thống phải cập nhật trạng thái bản ghi thành "Quá hạn" và cộng dồn vào bộ đếm thống kê thích hợp trên UI.`

---

## BUG-11

| Thuộc tính          | Chi tiết        |
| ------------------- | --------------- |
| **Mã lỗi**          | `BUG-11`        |
| **TC liên quan**    | `TC-01`         |
| **REQ liên quan**   | `REQ-04`        |
| **Mức độ**          | `High`          |
| **Người phát hiện** | `Bùi Mạnh Hiếu` |
| **Ngày phát hiện**  | `25/05/2026`    |
| **Trạng thái**      | `Open`          |

**Tiêu đề:**
`Lỗi trắng trang web + mất dữ liệu khi spam nhiều lần mục mượn sách`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window 10`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đã đăng nhập được vào tài khoản và tương tác với trang web`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản khả dụng`
2. `Bước 2: Spam nhiều lần nút Mượn sau khi ấn vào ô dấu cộng`

**Kết quả mong đợi:**
`Hệ thống cần ngăn người dùng spam liên tiếp nhằm phòng tránh các lỗi phát sinh từ máy chủ hoặc làm mất tính đồng bộ dữ liệu.`

**Kết quả thực tế:**
`Người dùng vẫn spam click được liên tục dẫn đến xung đột request gây lỗi trắng trang và mất dữ liệu hiển thị.`

**Tác động:**
`Gây quá tải cục bộ cho server nhận request và làm hỏng trải nghiệm cốt lõi của người dùng.`

**Minh chứng:**
![BUG-11](/submisions/images/BUG-11.png)

**Đề xuất xử lý:**
`Thêm thuộc tính disabled cho button mượn sách ngay sau lượt click đầu tiên để tránh người dùng tiếp tục spam request trong lúc server đang xử lý dữ liệu.`

---

## BUG-12

| Thuộc tính          | Chi tiết     |
| ------------------- | ------------ |
| **Mã lỗi**          | `BUG-12`     |
| **TC liên quan**    | `TC-01`      |
| **REQ liên quan**   | `REQ-05`     |
| **Mức độ**          | `Medium`     |
| **Người phát hiện** | `Đỗ Hữu Đức` |
| **Ngày phát hiện**  | `25/05/2026` |
| **Trạng thái**      | `Open`       |

**Tiêu đề:**
`Người dùng có thể tự ý trả sách mà không cần thủ thư xác nhận`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt & Tiếng Anh

**Điều kiện tiên quyết:**
`Thành viên đang có sách trong trạng thái "Đang mượn".`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào tài khoản thành viên.`
2. `Bước 2: Truy cập vào mục quản lý sách đang mượn hoặc lịch sử mượn trả`
3. `Bước 3: Nhấn vào nút hoặc thực hiện hành động "Trả sách" từ phía giao diện người dùng.`

**Kết quả mong đợi:**
`Hành động trả sách từ phía người dùng chỉ là gửi "Yêu cầu trả sách". Sách chỉ được tính là đã trả sau khi Thủ thư tiếp nhận, kiểm tra tình trạng sách vật lý và xác nhận trên hệ thống.`

**Kết quả thực tế:**
`Hệ thống cho phép người dùng tự ý bấm trả sách và trạng thái chuyển thành đã trả thành công mà không cần qua bước kiểm tra, xác nhận của thủ thư.`

**Tác động:**
`Sai lệch dữ liệu kho sách vật lý và hệ thống. Thành viên có thể gian lận bằng cách bấm trả trên hệ thống nhưng không trả sách thật, gây thất thoát tài sản của thư viện.`

**Minh chứng:**
![BUG-12](./images/BUG-12.png)

**Đề xuất xử lý:**
`Chuyển luồng xử lý: Khi user bấm trả sách, trạng thái chuyển thành "Chờ thủ thư xác nhận". Chỉ tài khoản có quyền Thủ thư mới có quyền phê duyệt hoàn thành quy trình trả sách.`

---

## BUG-13

| Thuộc tính          | Chi tiết           |
| ------------------- | ------------------ |
| **Mã lỗi**          | `BUG-13`           |
| **TC liên quan**    | `TC-01`            |
| **REQ liên quan**   | `REQ-05`           |
| **Mức độ**          | `Low`              |
| **Người phát hiện** | `Nguyễn Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`       |
| **Trạng thái**      | `Open`             |

**Tiêu đề:**
`Lỗi POPUP khi nhấn 2 lần nút trả sách`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Tài khoản đủ yêu cầu và có sách đang mượn`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản đang hoạt động`
2. `Bước 2: Vào mục mượn trả`
3. `Bước 3: Nhấn liên tục vào nút trả sách`

**Kết quả mong đợi:**
`Chỉ hiện duy nhất 1 popup thành công khi nhấn trả sách`

**Kết quả thực tế:**
`Bị lỗi hiển thị popup thành công sau đó xuất hiện luôn popup lỗi`

**Tác động:**
`Gây hiểu nhầm đối với người dùng khi thực hiện thao tác click đúp hoặc nhấn quá nhanh vào nút bấm`

**Minh chứng:**
![BUG-13-1](/submisions/images/BUG-13-1.png)
![BUG-13-2](/submisions/images/BUG-13-2.png)

**Đề xuất xử lý:**
`Khi đang xử lý yêu cầu, nút bấm hiển thị cần được chuyển sang trạng thái disabled (hoặc thêm hiệu ứng loading spinner) để chặn các tương tác tiếp theo từ phía client cho đến khi nhận được response từ server.`

---

## BUG-14

| Thuộc tính          | Chi tiết        |
| ------------------- | --------------- |
| **Mã lỗi**          | `BUG-14`        |
| **TC liên quan**    | `TC-01`         |
| **REQ liên quan**   | `REQ-07`        |
| **Mức độ**          | `Medium`        |
| **Người phát hiện** | `Bùi Mạnh Hiếu` |
| **Ngày phát hiện**  | `25/05/2026`    |
| **Trạng thái**      | `Open`          |

**Tiêu đề:**
`Nhập email đã tồn tại nhưng lại báo "Email không hợp lệ" thay vì báo "Email đã tồn tại"`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Windows 10`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Đăng nhập được vào tài khoản thủ thư`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thủ thư`
2. `Bước 2: Thêm thành viên`
3. `Bước 3: Nhập vào 1 email đã tồn tại`

**Kết quả mong đợi:**
`Hệ thống trả về thông báo lỗi phân biệt rõ ràng: "Email này đã được đăng ký trên hệ thống" để người vận hành nắm rõ lý do.`

**Kết quả thực tế:**
`Hệ thống hiển thị một thông báo chung chung là "Email không hợp lệ", dễ gây lầm tưởng rằng định dạng cấu trúc chuỗi email bị sai.`

**Tác động:**
`Gây cản trở và nhầm lẫn cho thủ thư trong quá trình quản lý, tạo mới hồ sơ thành viên.`

**Minh chứng:**
![BUG-14](/submisions/images/BUG-14.png)

**Đề xuất xử lý:**
`Cập nhật lại logic validate ở cả Client-side và Server-side. Khi nhận mã lỗi trùng lặp cơ sở dữ liệu (ví dụ: lỗi Unique Constraint từ cơ sở dữ liệu), hệ thống cần map đúng thông báo tương ứng thay vì gộp chung vào validation định dạng.`

---

## BUG-15

| Thuộc tính          | Chi tiết     |
| ------------------- | ------------ |
| **Mã lỗi**          | `BUG-15`     |
| **TC liên quan**    | `TC-01`      |
| **REQ liên quan**   | `REQ-05`     |
| **Mức độ**          | `High`       |
| **Người phát hiện** | `Đỗ Hữu Đức` |
| **Ngày phát hiện**  | `26/05/2026` |
| **Trạng thái**      | `Open`       |

**Tiêu đề:**
`Cho phép thành viên tự ý gia hạn hoặc trả sách của người khác`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt & Tiếng Anh

**Điều kiện tiên quyết:**

- Tài khoản thành viên đã đăng nhập vào hệ thống thành công.
- Có một thành viên khác (Thành viên B) đang mượn sách và vô tình lộ mã mượn hoặc ID lượt mượn.

**Bước tái hiện:**

1. `Bước 1: Đăng nhập vào hệ thống bằng tài khoản của thành viên A.`
2. `Bước 2: Truy cập vào mục Mượn/Trả (Tra cứu phiếu mượn) và nhập mã của thành viên B.`
3. `Bước 3: Tiến hành thực hiện thao tác trả sách hoặc gia hạn.`

**Kết quả mong đợi:**
`Hệ thống phải chặn hành động này lại và báo lỗi phân quyền (403 Forbidden). Chỉ chính chủ tài khoản đang mượn sách (hoặc Thủ thư/Admin) mới có quyền gửi yêu cầu hoặc thực hiện thao tác xử lý phiếu mượn đó.`

**Kết quả thực tế:**
`Hệ thống cho phép thành viên A tự ý bấm trả sách (hoặc gửi lệnh API trả sách thành công) cho các cuốn sách thuộc sở hữu lượt mượn của thành viên B.`

**Tác động:**
`Phá hoại dữ liệu mượn trả của người khác. Gây lỗi logic nghiêm trọng trong quản lý quy trình mượn sách, khiến thành viên B bị mất sách trên thực tế nhưng hệ thống lại ghi nhận là đã trả, gây tranh chấp và khó khăn khi thủ thư đối chiếu dữ liệu kho.`

**Minh chứng:**
![BUG-15](/submisions/images/BUG-15.png)

**Đề xuất xử lý:**
`Bổ sung kiểm tra quyền sở hữu (Authorization Check) ở tầng Backend đối với các API liên quan đến mượn/trả/gia hạn sách: Đảm bảo Session/Token ID của người dùng đang gửi Request phải trùng khớp với UserID ghi nhận trên lượt mượn của cuốn sách đó trong Database.`

---

## BUG-16

| Thuộc tính          | Chi tiết          |
| ------------------- | ----------------- |
| **Mã lỗi**          | `BUG-16`          |
| **TC liên quan**    | `TC-01`           |
| **REQ liên quan**   | `REQ-03`          |
| **Mức độ**          | `Low`             |
| **Người phát hiện** | `Hoàng Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`      |
| **Trạng thái**      | `Open`            |

**Tiêu đề:**
`Lỗi dịch phân loại (Category) khi chuyển tiếng Anh vẫn để nguyên là tiếng Việt`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Anh

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, chuyển giao diện sang tiếng Anh.`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thành công.`
2. `Bước 2: Chuyển giao diện sang tiếng Anh.`

**Kết quả mong đợi:**
`Khi chuyển đổi giao diện sang ngôn ngữ tiếng Anh, toàn bộ các nhãn văn bản và dữ liệu tĩnh của phân loại (Category) hiển thị trên trang web phải được dịch sang tiếng Anh tương ứng.`

**Kết quả thực tế:**
`Hệ thống đổi giao diện nhưng danh mục phân loại "Available Categories: Công nghệ, giáo dục, kinh tế, kĩ năng mềm, quản trị, văn học" vẫn giữ nguyên nội dung hiển thị bằng tiếng Việt.`

**Tác động:**
`Gây mất tính đồng bộ nhất quán về trải nghiệm đa ngôn ngữ (Localization), cản trở khả năng tiếp cận đối với người dùng không sử dụng tiếng Việt.`

**Minh chứng:**
![BUG-16](/submisions/images/BUG-16.png)

**Đề xuất xử lý:**
`Đưa mảng danh sách phân loại (Categories) vào tệp lưu trữ localization dữ liệu đa ngôn ngữ hệ thống. Khi người dùng thực hiện switch ngôn ngữ, trigger hàm map để lấy chính xác bản dịch tiếng Anh tương ứng từ tệp ngôn ngữ.`

---

## BUG-17

| Thuộc tính          | Chi tiết          |
| ------------------- | ----------------- |
| **Mã lỗi**          | `BUG-17`          |
| **TC liên quan**    | `TC-01`           |
| **REQ liên quan**   | `REQ-07`          |
| **Mức độ**          | `High`            |
| **Người phát hiện** | `Hoàng Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`      |
| **Trạng thái**      | `Open`            |

**Tiêu đề:**
`Lỗi thêm được thành viên với email không hợp lệ định dạng domain`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, đăng nhập bằng tài khoản thủ thư, vào mục thêm thành viên.`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thành công bằng tài khoản thủ thư.`
2. `Bước 2: Vào mục thêm thành viên.`
3. `Bước 3: Nhập một thành viên với cấu trúc chuỗi email không hợp lệ (VD: hoangthanhdat212@gmail thay vì hoangthanhdat212@gmail.com).`

**Kết quả mong đợi:**
`Hệ thống kích hoạt validator validate định dạng email, chặn hành động submit dữ liệu và thông báo lỗi cấu trúc email sai.`

**Kết quả thực tế:**
`Hệ thống bỏ qua kiểm tra, vẫn thêm mới email không hợp lệ này vào cơ sở dữ liệu bình thường.`

**Tác động:**
`Gây khó khăn, sai lệch khi quản lý dữ liệu người dùng của thủ thư và làm rác hệ thống thông tin liên lạc.`

**Minh chứng:**
![BUG-17](/submisions/images/BUG-11/BUG-11_01.png)
![BUG-17](/submisions/images/BUG-11/BUG-11_02.png)

**Đề xuất xử lý:**
`Triển khai Regex kiểm tra chặt chẽ định dạng email ở cả Front-end trước khi submit và Back-end trước khi ghi dữ liệu. Đồng thời kết hợp gửi mã/link kích hoạt xác thực tài khoản đến email để đảm bảo hòm thư đó tồn tại thật.`

---

## BUG-19

| Thuộc tính          | Chi tiết               |
| ------------------- | ---------------------- |
| **Mã lỗi**          | `BUG-19`               |
| **TC liên quan**    | `TC-19`                |
| **REQ liên quan**   | `REQ-06`               |
| **Mức độ**          | `High`                 |
| **Người phát hiện** | `Nguyễn Cao Hoàng Đạt` |
| **Ngày phát hiện**  | `25/05/2026`           |
| **Trạng thái**      | `Open`                 |

**Tiêu đề:**
`Hiển thị sai số lượng sách quá hạn khi nhấn nút lần thứ 2 'Kiểm tra quá hạn'`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt - Tiếng Anh

**Điều kiện tiên quyết:**
`Đã đăng nhập tài khoản thủ thư, hệ thống có ít nhất 1 số sách đang quá hạn, đang ở màn hình quản lý/ kiểm tra quá hạn.`

**Bước tái hiện:**

1. `Bước 1: Đăng nhập tài khoản thủ thư thành công.`
2. `Bước 2: Vào mục "Kiểm tra quá hạn". Bấm nút "Kiểm tra quá hạn" lần đầu → ghi nhận số lượng sách quá hạn hiển thị.`
3. `Bước 3: Bấm nút "Kiểm tra quá hạn" lần thứ 2.`

**Kết quả mong đợi:**
`Mỗi lần bấm "Kiểm tra quá hạn" phải trả về cùng một kết quả chính xác, nhất quán nếu dữ liệu hệ thống không có sự thay đổi nào.`

**Kết quả thực tế:**
`Lần bấm thứ 2 hiển thị số lượng sách quá hạn sai lệch, khác với lần đầu, dù không có sự biến động dữ liệu nào giữa 2 lần tương tác.`

**Tác động:**
`Làm giảm độ tin cậy của hệ thống, khiến thủ thư bối rối không biết tin vào kết quả nào. Có thể dẫn đến nghiệp vụ bỏ sót hoặc xử lý sai lệch hồ sơ sách quá hạn của người dùng.`

**Minh chứng:**
![BUG-19](/submisions/images/BUG-19.png)

**Đề xuất xử lý:**
`Kiểm tra lại luồng xử lý dữ liệu ở Client-side: đảm bảo làm sạch (clear/reset) cấu trúc lưu trữ danh sách hoặc bộ đếm đè cũ trước khi nhận mảng dữ liệu mới từ API trả về để tránh tình trạng append (gộp dữ liệu thừa). Phía Server-side cần cam kết cung cấp snapshot dữ liệu độc lập tại thời điểm request.`

## BUG-10

| Thuộc tính          | Chi tiết          |
| ------------------- | ----------------- |
| **Mã lỗi**          | BUG-10            |
| **TC liên quan**    | ``                |
| **REQ liên quan**   | `REQ-04`          |
| **Mức độ**          | `low`             |
| **Người phát hiện** | `Hoàng Thành Đạt` |
| **Ngày phát hiện**  | `25/05/2026`      |
| **Trạng thái**      | `Open`            |

**Tiêu đề:**
`Lỗi hiển thị số sách đang mượn ở mục Thành Viên, quá hạn đang mượn nhưng vẫn là đang mượn:0`

**Môi trường:**

- Trình duyệt: Chrome `Version 148.0.7778.179`
- Hệ điều hành: `Window`
- Ngôn ngữ giao diện: Tiếng Việt

**Điều kiện tiên quyết:**
`Trang đăng nhập đã mở, tài khoản đã đăng nhập thành công, hệ thống đang ở mục Mượn/Trả`

**Bước tái hiện:**

1. `Đăng nhập tài khoàn thành công`
2. `Mượn một cuốn sách bất kì`
   **Kết quả mong đợi:**
   `Mong đợi khi mượn quá hạn hệ thống thông báo đã quá hạn`

**Kết quả thực tế:**
`Lỗi hệ thống sách quá hạn vẫn hiện thị là đang mượn:0`

**Tác động:**
`Gây hiểu lầm và chưa phân biệt sách đang mượn và quá hạn cho người dùng`

**Minh chứng:**
![BUG-10](./images/BUG-10/BUG-1O_01.png)
![BUG-10](./images/BUG-10/BUG-1O_02.png)

**Đề xuất xử lý:**
`So sách time hiện tại và time trả sách. Nếu như time hiện tại nhỏ hơn hoặc bằng time trả sánh thì hiện thị là đang mượn và ngược lại`
