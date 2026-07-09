# Acceptance Criteria – AI CV Screening

## Mục tiêu

Tài liệu này xác định các Acceptance Criteria cho các User Story của tính năng AI CV Screening theo định dạng Given / When / Then.

---

# US-01: Upload Candidate CV

## Acceptance Criteria

### AC-01

**Given** HR Recruiter đã đăng nhập vào hệ thống  
**When** HR upload một file CV hợp lệ (.pdf hoặc .docx)  
**Then** hệ thống lưu CV thành công và hiển thị thông báo xác nhận.

### AC-02

**Given** HR Recruiter đang ở màn hình Upload CV  
**When** HR upload file không đúng định dạng  
**Then** hệ thống hiển thị thông báo lỗi và không lưu file.

### AC-03

**Given** HR Recruiter đang ở màn hình Upload CV  
**When** HR upload file vượt quá kích thước cho phép  
**Then** hệ thống hiển thị thông báo lỗi và yêu cầu chọn file khác.

---

# US-02: Parse CV Automatically

## Acceptance Criteria

### AC-04

**Given** CV đã được upload thành công  
**When** hệ thống bắt đầu quá trình parse  
**Then** hệ thống trích xuất được các thông tin cơ bản của ứng viên.

### AC-05

**Given** CV không thể đọc được  
**When** hệ thống thực hiện parse  
**Then** hệ thống đánh dấu trạng thái "Parse Failed" và ghi log lỗi.

---

# US-03: Calculate Matching Score

## Acceptance Criteria

### AC-06

**Given** CV đã được parse thành công  
**When** hệ thống tính Matching Score  
**Then** hệ thống tạo điểm phù hợp trong khoảng từ 0 đến 100.

### AC-07

**Given** Job Description không tồn tại  
**When** hệ thống thực hiện tính điểm  
**Then** hệ thống không tạo Matching Score và ghi log lỗi.

### AC-08

**Given** dữ liệu ứng viên không đầy đủ  
**When** hệ thống thực hiện tính điểm  
**Then** hệ thống vẫn tính điểm dựa trên dữ liệu hiện có và đánh dấu "Partial Score".

---

# US-04: View Candidate Ranking

## Acceptance Criteria

### AC-09

**Given** có ít nhất một ứng viên đã có Matching Score  
**When** HR truy cập màn hình Candidate Ranking  
**Then** hệ thống hiển thị danh sách ứng viên theo thứ tự điểm giảm dần.

### AC-10

**Given** hai ứng viên có cùng Matching Score  
**When** hệ thống thực hiện xếp hạng  
**Then** ứng viên được upload sớm hơn sẽ được hiển thị trước.

### AC-11

**Given** chưa có ứng viên nào được tính điểm  
**When** HR truy cập màn hình Candidate Ranking  
**Then** hệ thống hiển thị thông báo "Chưa có dữ liệu xếp hạng".

---

# My Analysis

Acceptance Criteria giúp chuyển đổi User Story từ mức mô tả nhu cầu sang mức có thể kiểm thử được. Mỗi tiêu chí đều xác định rõ điều kiện đầu vào (Given), hành động (When) và kết quả mong đợi (Then), từ đó giúp Developer và Tester hiểu thống nhất về hành vi của hệ thống.
