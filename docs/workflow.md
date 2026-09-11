# Quy Trình Sprint (Sprint Workflow)

Tài liệu này mô tả quy trình làm việc chuẩn trong một Sprint dành cho nhóm Phát triển Phần mềm (Software Engineering). Các thành viên cần tuân thủ quy trình này để đảm bảo tiến độ và chất lượng dự án.

## 1. Các Vai Trò (Roles)
*   **Product Owner (PO):** Quản lý Product Backlog, định nghĩa các yêu cầu, User Story và độ ưu tiên.
*   **Scrum Master (SM):** Đảm bảo quy trình Scrum được thực thi đúng đắn, hỗ trợ giải quyết các trở ngại (blockers) cho team.
*   **Development Team (Devs):** Các thành viên trực tiếp tham gia thiết kế, lập trình, kiểm thử và bàn giao sản phẩm.

## 2. Các Sự Kiện Trong Sprint (Sprint Events)

### 2.1. Lập Kế Hoạch Sprint
*   **Thời điểm:** Ngày đầu tiên của Sprint.
*   **Mục tiêu:** Xác định Sprint Goal (Mục tiêu của Sprint) và chọn các task từ Product Backlog đưa vào Sprint Backlog.
*   **Hoạt động:** Dev team estimate (ước lượng) thời gian/point cho từng task, phân rã công việc và phân công người phụ trách (Assignee).

### 2.2. Cập nhật tiến độ hằng ngày - Optional
*   **Thời điểm:** Buổi tối hằng ngày qua file `daily.md`.
*   **Mục tiêu:** Đồng bộ tiến độ công việc giữa các thành viên.
*   **Nội dung - Mỗi thành viên trả lời 3 câu hỏi:**
    1. Hôm qua tôi đã làm được gì?
    2. Hôm nay tôi dự định làm gì?
    3. Tôi có đang gặp khó khăn (blocker) nào cần hỗ trợ không?

### 2.3. Đánh Giá Sprint (Sprint Review)
*   **Thời điểm:** Ngày cuối cùng của Sprint (trước buổi Retrospective).
*   **Mục tiêu:** Demo các tính năng đã hoàn thành (Done) cho PO và các bên liên quan (Stakeholders).
*   **Đầu ra:** Nhận feedback và cập nhật lại Product Backlog nếu cần thiết.

### 2.4. Cải Tiến Sprint (Sprint Retrospective)
*   **Thời điểm:** Ngay sau Sprint Review, kết thúc Sprint.
*   **Mục tiêu:** Nhìn lại quá trình làm việc của team trong Sprint vừa qua để tối ưu cho Sprint tiếp theo.
*   **Nội dung thảo luận:**
    *   Điều gì team đã làm tốt? (What went well?)
    *   Điều gì chưa tốt/cần cải thiện? (What didn't go well?)
    *   Hành động cụ thể để cải thiện cho Sprint tới là gì? (Action items)

## 3. Quy Trình Code & Quản Lý Repository

Do làm việc trực tiếp với source code trên Repo, các thành viên cần tuân thủ quy trình Git Workflow sau:

### Bước 1: Nhận Task
*   Tự assign (hoặc được assign) task trên Board quản lý GitHub Projects.
*   Di chuyển task từ cột **To Do** sang **In Progress**.

### Bước 2: Tạo Branch
*   Luôn `git pull` để checkout từ nhánh `main` mới nhất trước khi làm việc.
*   Quy tắc đặt tên nhánh: `<số-issue>-<mô-tả-ngắn-bằng-gạch-ngang>`
    *   *Ví dụ tính năng mới:* `12-upload-csv`
    *   *Ví dụ sửa lỗi:* `27-fix-null-cart`

### Bước 3: Commit Code
*   Code cần được format chuẩn trước khi commit. Commit thường xuyên theo từng đơn vị công việc hoàn chỉnh.
*   Quy tắc viết commit message:
```powershell
git commit -m "loại: nội dung thay đổi ngắn gọn" -m "Refs #id-issue"
```
* Ví dụ:
```powershell
git commit -m "feat: thêm chức năng đăng nhập" -m "Refs #123"
git commit -m "fix: sửa lỗi tổng doanh thu khi file có dòng trống" -m "Refs #45"
git commit -m "test: thêm test cho trường hợp file rỗng" -m "Refs #12"
git commit -m "docs: cập nhật hướng dẫn cài đặt trong README" -m "Refs #7"
git commit -m "refactor: tách hàm đọc CSV ra module riêng" -m "Refs #31"
git commit -m "chore: nâng Flask lên 3.0" -m "Refs #8"
```

### Bước 4: Tạo Pull Request (PR)
*   Khi hoàn thành task và đã test ở local (Unit test pass), push code lên repo và tạo Pull Request merge vào nhánh `main`.
*   PR cần có description rõ ràng: Thay đổi những gì? Ảnh hưởng đến file nào? Đính kèm ảnh/video demo (nếu là UI) - theo template đã có.
*   Gắn thẻ (Reviewers) ít nhất 1-2 thành viên khác trong team để tiến hành **Code Review**.

### Bước 5: Code Review & Merge
*   **Reviewer** kiểm tra source code, để lại comment yêu cầu sửa đổi (Request Changes) nếu cần.
*   Nếu code đạt chuẩn, Reviewer chọn **Approve**.
*   Người tạo PR tiến hành **Merge** code vào nhánh chung.
*   Cập nhật trạng thái task trên Board sang cột **Done/Testing**.