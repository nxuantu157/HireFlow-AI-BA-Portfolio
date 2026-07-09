# Use Case Specification – AI CV Screening

---

# UC-01: Upload CV

## General Information

| Item | Detail |
|------|--------|
| Use Case ID | UC-01 |
| Use Case Name | Upload CV |
| Primary Actor | HR Recruiter |
| Goal | Tải CV ứng viên lên hệ thống để bắt đầu quá trình AI CV Screening |
| Scope | HireFlow AI |
| Trigger | HR chọn chức năng Upload CV |

---

## Preconditions

- HR Recruiter đã đăng nhập vào hệ thống.
- Job Description đã được tạo trước đó.
- File CV có định dạng hợp lệ (.pdf hoặc .docx).

---

## Main Flow

| Step | Actor / System | Description |
|------|----------------|-------------|
| 1 | HR Recruiter | Chọn chức năng Upload CV |
| 2 | System | Hiển thị form tải lên CV |
| 3 | HR Recruiter | Chọn file CV từ thiết bị |
| 4 | System | Kiểm tra định dạng và kích thước file |
| 5 | System | Lưu file CV vào hệ thống |
| 6 | System | Kích hoạt Use Case "AI Parse CV" |
| 7 | System | Hiển thị thông báo upload thành công |

---

## Alternative Flow

### A1 – File không hợp lệ

| Step | Description |
|------|-------------|
| 4a | Hệ thống phát hiện file không đúng định dạng |
| 4b | Hệ thống hiển thị thông báo lỗi |
| 4c | HR chọn lại file hợp lệ |

### A2 – Kích thước file vượt giới hạn

| Step | Description |
|------|-------------|
| 4a | Hệ thống phát hiện file vượt quá kích thước cho phép |
| 4b | Hệ thống hiển thị thông báo lỗi |
| 4c | HR chọn file khác |

---

## Postconditions

### Success

- CV được lưu thành công vào hệ thống.
- Quá trình AI Parse CV được khởi động.

### Failure

- CV không được lưu vào hệ thống.
- AI Parse CV không được thực hiện.

---

## Business Rules

- Chỉ chấp nhận file `.pdf` và `.docx`.
- Kích thước tối đa của file là 10MB.
- Mỗi CV phải được gắn với một Job Description.
- Hệ thống phải lưu thời gian upload và người thực hiện upload.

---

## Related Use Cases

- UC-02: AI Parse CV
- UC-03: Calculate Matching Score

---

## Notes

- Upload CV là Use Case khởi đầu của toàn bộ quy trình AI CV Screening.
- Sau khi upload thành công, các bước AI Parse CV và Calculate Matching Score sẽ được hệ thống tự động thực hiện thông qua quan hệ `<<include>>`.
