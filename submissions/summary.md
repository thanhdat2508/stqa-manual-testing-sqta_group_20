# Test Summary — Báo cáo tổng hợp kiểm thử

> **Hướng dẫn**: Đây là hoạt động **Quality Assurance** — bạn đánh giá chất lượng tổng thể của phần mềm, không chỉ liệt kê lỗi.

---

## 1. Thông tin nhóm

| Mục                   | Thông tin                  |
| --------------------- | -------------------------- |
| **Nhóm**              | `Nhóm 30`                  |
| **Lớp**               | `Class 2`                  |
| **Ngày báo cáo**      | `29/05/2026`               |
| **Hệ thống kiểm thử** | https://stqa.rbc.vn — v1.0 |

---

## 2. Tổng quan kết quả

| Chỉ số               | Giá trị |
| -------------------- | ------- |
| Tổng số test case    | `57`    |
| Pass                 | `41`    |
| Fail                 | `16`    |
| Blocked              | `0`     |
| Not Run              | `0`     |
| **Tỷ lệ Pass**       | `72%`   |
| **Số bug phát hiện** | `16`    |

### Phân bổ theo nhóm chức năng

| Nhóm chức năng                | TC  | Pass | Fail | Bug | Đánh giá                                                      |
| ----------------------------- | --- | ---- | ---- | --- | ------------------------------------------------------------- |
| Login (REQ-01)                | 6   | 5    | 1    | 1   | Rủi ro khi đăng nhập tài khoản                                |
| Danh sách sách (REQ-02)       | 4   | 4    | 0    | 0   | Hoạt động ổn định                                             |
| Tìm kiếm và lọc sách (REQ-03) | 12  | 10   | 2    | 2   | Rủi ro khi tìm kiếm danh sách sách                            |
| Mượn sách (REQ-04)            | 6   | 1    | 5    | 5   | Vi phạm quy tắc kinh doanh                                    |
| Trả sách (REQ-05)             | 7   | 3    | 4    | 4   | Vi phạm quy tắc kinh doanh                                    |
| Xử lý sách quá hạn (REQ-06)   | 7   | 5    | 2    | 2   | Rủi ro khi sách đã quá hạn                                    |
| Quản lý thành viên (REQ-07)   | 9   | 7    | 2    | 2   | Rủi ro khi thêm thành viên với mail không hợp lệ              |
| Tra cứu phiếu mượn (REQ-08)   | 1   | 0    | 1    | 1   | Rủi ro về bảo mật thông tin khi có thể tra cứu của người khác |

### Phân bổ bug theo mức độ

| Mức độ | Số lượng | Bug IDs                                                                       |
| ------ | -------- | ----------------------------------------------------------------------------- |
| High   |          | BUG-01, BUG-02, BUG-05, BUG-06, BUG-07, BUG-09, BUG-11,BUG-13, BUG-15, BUG-16 |
| Medium |          | BUG-03, REQ-10, BUG-12                                                        |
| Low    |          | BUG-08, BUG-14, BUG-17                                                        |

---

## 3. Kỹ thuật thiết kế đã sử dụng

| Kỹ thuật | Áp dụng cho REQ nào? | Số TC sử dụng | Giải thích cách áp dụng |
| -------- | -------------------- | ------------- | ----------------------- |
|          |                      |               |                         |

---

## 4. Phân tích chất lượng phần mềm

### 4.1. Điểm mạnh

`<!-- Liệt kê các chức năng hoạt động tốt -->`

### 4.2. Điểm yếu

`<!-- Liệt kê các vấn đề nghiêm trọng -->`

---

## 5. Đề xuất ưu tiên sửa lỗi

> 💡 Đây là phần **Quality Assurance**: bạn không chỉ tìm lỗi mà còn **đề xuất thứ tự ưu tiên** sửa chữa và đánh giá tác động.
> Nêu rõ tiêu chí ưu tiên: dựa vào **severity** (mức độ nghiêm trọng kỹ thuật) và/hoặc **priority** (mức độ ưu tiên kinh doanh).

| Thứ tự | Bug | Mức độ | Lý do ưu tiên |
| ------ | --- | ------ | ------------- |
|        |     |        |               |

---

## 6. Kết luận

`<!-- Đánh giá tổng thể: Hệ thống có sẵn sàng phát hành không? Tại sao? -->`

---

## 7. Bài học rút ra (Tùy chọn)

`<!-- Nhóm bạn học được gì từ quá trình kiểm thử này? -->`

---

## 8. Khai báo sử dụng AI (Tùy chọn)

> Nếu nhóm có sử dụng công cụ AI (ChatGPT, Copilot, Gemini...), hãy ghi rõ bên dưới. Khai báo trung thực **không ảnh hưởng điểm** — đây là kỹ năng minh bạch trong nghề.

| Công cụ AI | Dùng cho phần nào | Bạn đã kiểm tra/chỉnh sửa thế nào |
| ---------- | ----------------- | --------------------------------- |
|            |                   |                                   |
