# MVP Feature List

## Mục tiêu

Tài liệu này xác định các tính năng cần phát triển trong phiên bản MVP (Minimum Viable Product) của HireFlow AI. Việc lựa chọn các tính năng dựa trên Pain Point, Business Value và phạm vi phát triển của dự án nhằm đảm bảo sản phẩm có thể giải quyết được những vấn đề cốt lõi của quy trình tuyển dụng.

---

| ID | Feature | Description | Primary Persona | Business Value | Priority | MVP |
|----|----------|-------------|-----------------|----------------|----------|-----|
| F-01 | AI CV Screening | AI phân tích CV và tính toán mức độ phù hợp với Job Description để hỗ trợ HR sàng lọc ứng viên. | HR Recruiter | Giảm thời gian sàng lọc CV và tăng hiệu quả tuyển dụng. | High |  Yes |
| F-02 | Candidate Management | Quản lý toàn bộ thông tin ứng viên trên một hệ thống tập trung. | HR Recruiter | Chuẩn hóa dữ liệu và giảm thất lạc hồ sơ. | High |  Yes |
| F-03 | Candidate Pipeline | Theo dõi trạng thái ứng viên theo từng giai đoạn tuyển dụng. | HR Recruiter | Dễ dàng quản lý tiến độ và giảm sai sót trong quy trình. | High |  Yes |
| F-04 | Search & Filter Candidate | Tìm kiếm và lọc ứng viên theo vị trí, kỹ năng, kinh nghiệm hoặc trạng thái tuyển dụng. | HR Recruiter | Rút ngắn thời gian tìm kiếm ứng viên. | High |  Yes |
| F-05 | Job Description Management | Tạo, chỉnh sửa và quản lý các Job Description phục vụ tuyển dụng. | HR Recruiter | Chuẩn hóa thông tin tuyển dụng. | Medium |  Yes |
| F-06 | Recruitment Dashboard | Thống kê số lượng ứng viên, tỷ lệ tuyển dụng và Time-to-Hire. | HR Recruiter / CEO | Hỗ trợ theo dõi hiệu quả tuyển dụng. | Medium |  No |
| F-07 | Candidate Portal | Ứng viên theo dõi trạng thái hồ sơ sau khi ứng tuyển. | Candidate | Nâng cao Candidate Experience. | Medium | No |
| F-08 | Interview Scheduler | Quản lý lịch phỏng vấn và gửi lời mời qua Email. | HR Recruiter | Giảm thao tác thủ công khi sắp lịch. | Medium |  No |
| F-09 | Email Notification | Tự động gửi Email khi trạng thái ứng viên thay đổi. | Candidate | Tăng tính minh bạch của quy trình tuyển dụng. | Low |  No |

---

# MVP Scope

## Included Features

### AI CV Screening
- Upload CV
- AI Parsing
- Matching Score
- Candidate Ranking

### Candidate Management
- Candidate Profile
- Candidate List
- Candidate Detail
- Candidate Search

### Candidate Pipeline
- Applied
- Screening
- Interview
- Offer
- Hired
- Rejected

### Search & Filter Candidate
- Search by Name
- Search by Skill
- Filter by Position
- Filter by Status

### Job Description Management
- Create Job Description
- Edit Job Description
- Archive Job Description

---

## Out of Scope

Các tính năng dưới đây sẽ không nằm trong phạm vi MVP và được xem xét phát triển ở các phiên bản tiếp theo:

- Recruitment Dashboard
- Candidate Portal
- Interview Scheduler
- Email Notification

---

# MVP Success Criteria

MVP được xem là thành công khi đạt được các mục tiêu sau:

- Giảm ít nhất **70% thời gian sàng lọc CV** so với quy trình thủ công.
- 100% hồ sơ ứng viên được quản lý trên một hệ thống tập trung.
- HR có thể theo dõi trạng thái của tất cả ứng viên trong quy trình tuyển dụng.
- Thời gian tìm kiếm hồ sơ ứng viên dưới **5 giây**.
- Hoàn thành quy trình tuyển dụng với ít thao tác thủ công hơn trước.

---

# My Analysis

Qua các Deliverable trước, có thể thấy phần lớn Pain Point đều tập trung vào ba hoạt động chính của HR: sàng lọc CV, quản lý hồ sơ và theo dõi tiến trình tuyển dụng. Vì vậy, MVP của HireFlow AI sẽ ưu tiên phát triển các tính năng trực tiếp giải quyết ba nhóm vấn đề này.

Các tính năng như Recruitment Dashboard, Candidate Portal và Interview Scheduler mang lại giá trị nhưng chưa ảnh hưởng trực tiếp đến Pain Point cốt lõi. Do đó, các tính năng này sẽ được đưa vào Product Backlog để xem xét phát triển trong các phiên bản tiếp theo sau khi MVP được triển khai và đánh giá hiệu quả.
