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

---

# UC-02: AI Parse CV

## General Information

| Item | Detail |
|------|--------|
| Use Case ID | UC-02 |
| Use Case Name | AI Parse CV |
| Primary Actor | System |
| Goal | Phân tích và trích xuất thông tin từ CV ứng viên |
| Scope | HireFlow AI |
| Trigger | UC-01 Upload CV hoàn thành thành công |

---

## Preconditions

- CV đã được upload thành công vào hệ thống.
- File CV có thể đọc được.
- Dịch vụ AI Parsing đang hoạt động.

---

## Main Flow

| Step | Actor / System | Description |
|------|----------------|-------------|
| 1 | System | Nhận file CV từ UC-01 |
| 2 | System | Đọc nội dung file CV |
| 3 | System | Trích xuất thông tin cá nhân |
| 4 | System | Trích xuất kỹ năng |
| 5 | System | Trích xuất kinh nghiệm làm việc |
| 6 | System | Trích xuất học vấn |
| 7 | System | Chuẩn hóa dữ liệu |
| 8 | System | Lưu thông tin đã phân tích |
| 9 | System | Kích hoạt UC-03 Calculate Matching Score |

---

## Alternative Flow

### A1 – Không đọc được file

| Step | Description |
|------|-------------|
| 2a | Hệ thống không thể đọc nội dung file |
| 2b | Hệ thống ghi log lỗi |
| 2c | Hệ thống đánh dấu CV ở trạng thái "Parse Failed" |

### A2 – Thiếu dữ liệu trong CV

| Step | Description |
|------|-------------|
| 3a | Hệ thống không tìm thấy một số trường thông tin |
| 3b | Hệ thống tiếp tục phân tích các trường còn lại |
| 3c | Các trường thiếu được để trống |

---

## Postconditions

### Success

- Thông tin từ CV được trích xuất và lưu vào hệ thống.
- UC-03 Calculate Matching Score được khởi động.

### Failure

- CV được đánh dấu "Parse Failed".
- Matching Score không được tính.

---

## Business Rules

- Hệ thống phải hỗ trợ file `.pdf` và `.docx`.
- Các trường thông tin không tìm thấy sẽ được lưu dưới dạng rỗng.
- Dữ liệu sau khi parse phải được chuẩn hóa trước khi tính Matching Score.
- Hệ thống phải lưu trạng thái parse của từng CV.

---

## Related Use Cases

- UC-01: Upload CV
- UC-03: Calculate Matching Score

---

## Notes

- AI Parse CV là Use Case xử lý nội bộ của hệ thống và không có tương tác trực tiếp từ HR Recruiter.
- Kết quả của quá trình parse sẽ được sử dụng để tính Matching Score và xếp hạng ứng viên.

---

# UC-03: Calculate Matching Score

## General Information

| Item | Detail |
|------|--------|
| Use Case ID | UC-03 |
| Use Case Name | Calculate Matching Score |
| Primary Actor | System |
| Goal | Tính toán mức độ phù hợp giữa CV ứng viên và Job Description |
| Scope | HireFlow AI |
| Trigger | UC-02 AI Parse CV hoàn thành thành công |

---

## Preconditions

- CV đã được parse thành công.
- Job Description tương ứng đã tồn tại.
- Dữ liệu kỹ năng, kinh nghiệm và học vấn đã được chuẩn hóa.

---

## Main Flow

| Step | Actor / System | Description |
|------|----------------|-------------|
| 1 | System | Nhận dữ liệu CV đã parse |
| 2 | System | Lấy thông tin Job Description tương ứng |
| 3 | System | So sánh kỹ năng của ứng viên với yêu cầu công việc |
| 4 | System | So sánh số năm kinh nghiệm |
| 5 | System | So sánh trình độ học vấn |
| 6 | System | Tính điểm phù hợp tổng hợp |
| 7 | System | Gán Matching Score cho ứng viên |
| 8 | System | Lưu kết quả vào hệ thống |
| 9 | System | Cập nhật danh sách Candidate Ranking |

---

## Alternative Flow

### A1 – Không tìm thấy Job Description

| Step | Description |
|------|-------------|
| 2a | Hệ thống không tìm thấy Job Description |
| 2b | Hệ thống ghi log lỗi |
| 2c | Matching Score không được tính |

### A2 – Thiếu dữ liệu để tính điểm

| Step | Description |
|------|-------------|
| 3a | Hệ thống phát hiện thiếu dữ liệu kỹ năng hoặc kinh nghiệm |
| 3b | Hệ thống tính điểm dựa trên dữ liệu còn lại |
| 3c | Hệ thống đánh dấu kết quả là "Partial Score" |

---

## Postconditions

### Success

- Matching Score được tính thành công.
- Điểm phù hợp được lưu vào hồ sơ ứng viên.
- Candidate Ranking được cập nhật.

### Failure

- Matching Score không được tạo.
- Candidate Ranking không được cập nhật.

---

## Business Rules

- Matching Score được tính trên thang điểm từ 0 đến 100.
- Kỹ năng bắt buộc có trọng số cao hơn kỹ năng ưu tiên.
- Kinh nghiệm làm việc ảnh hưởng trực tiếp đến điểm phù hợp.
- Hệ thống phải lưu thời gian tính điểm và phiên bản thuật toán được sử dụng.

---

## Related Use Cases

- UC-02: AI Parse CV
- UC-04: View Candidate Ranking

---

## Notes

- Calculate Matching Score là Use Case xử lý nội bộ của hệ thống.
- Kết quả Matching Score sẽ được sử dụng để sắp xếp thứ tự ứng viên trong Candidate Ranking.

---

# UC-04: View Candidate Ranking

## General Information

| Item | Detail |
|------|--------|
| Use Case ID | UC-04 |
| Use Case Name | View Candidate Ranking |
| Primary Actor | HR Recruiter |
| Goal | Xem danh sách ứng viên được xếp hạng theo Matching Score |
| Scope | HireFlow AI |
| Trigger | HR truy cập màn hình Candidate Ranking |

---

## Preconditions

- Ít nhất một CV đã được upload và xử lý thành công.
- Matching Score đã được tính cho ứng viên.
- HR Recruiter đã đăng nhập vào hệ thống.

---

## Main Flow

| Step | Actor / System | Description |
|------|----------------|-------------|
| 1 | HR Recruiter | Truy cập chức năng Candidate Ranking |
| 2 | System | Lấy danh sách ứng viên đã có Matching Score |
| 3 | System | Sắp xếp ứng viên theo điểm phù hợp giảm dần |
| 4 | System | Hiển thị danh sách ứng viên |
| 5 | HR Recruiter | Xem thông tin ứng viên |
| 6 | HR Recruiter | Chọn ứng viên để xem chi tiết nếu cần |

---

## Alternative Flow

### A1 – Chưa có dữ liệu xếp hạng

| Step | Description |
|------|-------------|
| 2a | Hệ thống không tìm thấy ứng viên có Matching Score |
| 2b | Hệ thống hiển thị thông báo "Chưa có dữ liệu xếp hạng" |

### A2 – Lỗi tải dữ liệu

| Step | Description |
|------|-------------|
| 2a | Hệ thống không thể truy xuất dữ liệu |
| 2b | Hệ thống hiển thị thông báo lỗi |
| 2c | HR có thể tải lại trang |

---

## Postconditions

### Success

- Danh sách ứng viên được hiển thị thành công.
- HR có thể xem thứ hạng và điểm phù hợp của từng ứng viên.

### Failure

- Danh sách ứng viên không được hiển thị.
- HR không thể xem thông tin xếp hạng.

---

## Business Rules

- Ứng viên có Matching Score cao hơn sẽ được hiển thị trước.
- Nếu hai ứng viên có cùng điểm, hệ thống ưu tiên ứng viên được upload sớm hơn.
- Hệ thống phải hiển thị tối thiểu các thông tin: tên ứng viên, vị trí ứng tuyển và Matching Score.
- Kết quả xếp hạng phải được cập nhật sau mỗi lần tính điểm mới.

---

## Related Use Cases

- UC-01: Upload CV
- UC-02: AI Parse CV
- UC-03: Calculate Matching Score

---

## Notes

- View Candidate Ranking là Use Case duy nhất trong chuỗi AI CV Screening mà HR Recruiter trực tiếp sử dụng để đưa ra quyết định sàng lọc ban đầu.
- Kết quả hiển thị phụ thuộc hoàn toàn vào dữ liệu được tạo từ UC-02 và UC-03.
