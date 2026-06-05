# Test Summary — Báo cáo tổng hợp kiểm thử

> **Hướng dẫn**: Đây là hoạt động **Quality Assurance** — bạn đánh giá chất lượng tổng thể của phần mềm, không chỉ liệt kê lỗi.

---

## 1. Team Information

| Item | Details |
|-----|----------|
| **Group** | `Group 30` |
| **Class** | `Class 2` |
| **Report Date** | `5/6/2026` |
| **Testing System** | https://stqa.rbc.vn — v1.0 |

---

## 2. Overall Results

| Metric              | Value |
| -------------------- | ------- |
| Tổng số test case    | `60`    |
| Pass                 | `42`    |
| Fail                 | `18`    |
| Blocked              | `0`     |
| Not Run              | `0`     |
| **Tỷ lệ Pass**       | `70%`   |
| **Số bug phát hiện** | `16`    |

### Distribution by Feature Group


| Nhóm chức năng                | TC  | Pass | Fail | Bug | Đánh giá                                                      |
| ----------------------------- | --- | ---- | ---- | --- | ------------------------------------------------------------- |
| Login (REQ-01)                | 6   | 5    | 1    | 1   | Risky when login user account                                |
| View Book List (REQ-02)       | 4   | 4    | 0    | 0   | Fully stable                                             |
| Search & Filter (REQ-03) | 12  | 10   | 2    | 2   | Risky when search and filter books                            |
| Borrow Book (REQ-04)            | 6   | 1    | 5    | 5   | Business rules violated                                    |
| Return Book (REQ-05)             | 7   | 3    | 4    | 4   | Business rules violated                                    |
| Overdue Handling (REQ-06)   | 7   | 5    | 2    | 2   | Risky when have book overdue                                    |
| Member Management (REQ-07)   | 9   | 7    | 2    | 2   | Risky when add member when email is not correct format              |
| Borrow Record Lookup (REQ-08)   | 1   | 0    | 1    | 1   | Risk of user information leakage |


### Bug Distribution by Severity

| Mức độ | Số lượng | Bug IDs                                                                       |
| ------ | -------- | ----------------------------------------------------------------------------- |
| High   |          | BUG-01, BUG-02, BUG-05, BUG-06, BUG-07, BUG-09, BUG-11,BUG-13, BUG-15, BUG-16 |
| Medium |          | BUG-03, REQ-10, BUG-12                                                        |
| Low    |          | BUG-08, BUG-14, BUG-17                                                        |

---

## 3. Design Techniques Applied

| Kỹ thuật | Áp dụng cho REQ nào? | Số TC sử dụng | Giải thích cách áp dụng |
|----------|---------------------|---------------|------------------------|
| Equivalence Partitioning - EP | REQ-01, REQ-02, REQ-03, REQ-04, REQ-05, REQ-06, REQ-07, REQ-08 | 49 TC | Divides the input domain into Valid and Invalid data classes. Example: Email exists / email does not exists |
| Boundary Value Analysis - BVA | REQ-02, REQ-04, REQ-05, REQ-06, REQ-07 | 10 TCs | Testing extreme boundaries of numeric and dates. Example: Borrow Limit = 3 and test with 2 and 4 |
| Decision Table - DT | REQ-07, REQ-08 | 13 TCs | Combines multiple logical input conditions. Example: map combinations for adding new member: Requires Librarian role AND Valid email AND 10-digit phone |

---

## 4. Software Quality Analysis

### 4.1. Strengths
- Authentication Message (REQ-01): Error message work exactly as specified in the SRS
- Book display (REQ-02): Realtime display and display full book exist in library
- Keyword search (REQ-03): Case-insensitive search is fully functional for both book title and author name. The message when cant show correctly

### 4.2. Weaknesses
- Authentication & Security (REQ-01): Email parsing remains strictly case-sensitive
- Critical Business Rule Enforcement (REQ-04, REQ-05): It bypasses strict business rules: Can borrow more than 4 books when it reached maximum books allowance of 3
- Sync Data of borrow book (REQ-05, REQ-06): The overdue counting tracker is decoupled from current timestamps, displaying 0 books borrowed for past-due users
- Input validation (REQ-07): The email validation is to loose - the system accept email wrong format (abc@gmail) without accept valid email (abc@gmail.com)
- Message language when switching language: The message is hardcode in red toast messages/popup, it doesnt change when in English layer
- Case-intensitive when filter: The filter box is case-intensity. This will make user hard to find book when they dont know exactly the case of book title or author name

---

## 5. Recommended Fix Priority

> 💡 Đây là phần **Quality Assurance**: bạn không chỉ tìm lỗi mà còn **đề xuất thứ tự ưu tiên** sửa chữa và đánh giá tác động.
> Nêu rõ tiêu chí ưu tiên: dựa vào **severity** (mức độ nghiêm trọng kỹ thuật) và/hoặc **priority** (mức độ ưu tiên kinh doanh).

| Thứ tự | Bug | Mức độ | Lý do ưu tiên |
|--------|-----|--------|---------------|
| 01 | BUG-06 | High | Violates critical data privacy rules. Member can only view their own borrowing history |
| 02 | BUG-13 | High | Allows unauthorized mutation of other users' data. Other user can return books on behalf of others |
| 03 | BUG-02 | High | Violates business rules regarding maximum number of books that can be borrowed |
| 04 | BUG-10 | High | Bypasses the essential librarian verification checkpoint |
| 05 | BUG-15 | High | Bypasses the validation for email format when add member |
| 06 | BUG-09 | High | App crashes completely (blank screen) under standard user spamming behavior |
| 07 | BUG-11 | High | Sends redundant, conflicting API requests to the server, threatening sequential data stability |
| 08 | BUG-16 | High | Shows corrupted metrics due to un-cleared UI memory buffers |
| 09 | BUG-01 | High | Deny when user tries to access with case-insensitive email |
| 10 | BUG-05 | High | Users receive completely wrong information regarding their membership status |
| 11 | BUG-07 | High | Wrong overdue book return warnings |
| 12 | BUG-04 | High | Breaks the core search and catalog filtering mechanism |
| 13 | BUG-12 | Medium | Confuses with wrong error messages |
| 14 | BUG-08 | Medium | Displaying the number of overdue books incorrectly cause confusion for users |
| 15 | BUG-14 | Low | Minor static localization mismatch. Only affects the category layout |
| 16 | BUG-03 | Low | Confuses users with incorrect language display on error message |

---

## 6. Summary & Conclusion
This system is not ready to got to PRODUCTION.
The system has critical issues in core functionalities such as borrowing and returning books, which violate essential business rules and data privacy. The login mechanism also has significant flaws that could lead to unauthorized access. While some features like book display and search work well, the overall quality is compromised by the high-severity bugs that need immediate attention before deployment.

---

## 7. Lessons Learned
- **Test Design**: Applying a combination of EP, BVA, and DT allowed us to cover a wide range of scenarios efficiently. However, we should have also considered state transition testing for the borrowing and returning processes to catch more complex bugs.
- **Bug Reporting**: Clear and detailed bug reports with proper categorization of severity and priority helped us to communicate effectively with the development team. However, we could improve by including more screenshots and logs to provide better context for the developers.
- **Team Collaboration**: Regular communication and collaboration within the team were crucial in identifying and addressing issues quickly. We learned the importance of having a shared understanding of the requirements and testing goals to ensure everyone is aligned.

---

## 8. Khai báo sử dụng AI (Tùy chọn)

> Nếu nhóm có sử dụng công cụ AI (ChatGPT, Copilot, Gemini...), hãy ghi rõ bên dưới. Khai báo trung thực **không ảnh hưởng điểm** — đây là kỹ năng minh bạch trong nghề.

| Công cụ AI | Dùng cho phần nào | Bạn đã kiểm tra/chỉnh sửa thế nào |
|------------|-------------------|-----------------------------------|
| | | |
