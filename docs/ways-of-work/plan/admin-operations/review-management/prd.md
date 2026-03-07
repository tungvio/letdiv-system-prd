# PRD – Quản lý Review

## 1. Tên Tính năng  
**Quản lý Review** (Review Management Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Khi số lượng đánh giá tăng lên, đội ngũ admin/QA cần một nơi tập trung để theo dõi chất lượng review, xử lý review vi phạm/nội dung không phù hợp, và nhanh chóng khoanh vùng vấn đề theo từng khóa học. Nếu không có module riêng, việc tìm review phân tán, chậm và khó kiểm soát.

- **Giải pháp:**  
  Xây dựng module Quản lý Review tập trung, cho phép tìm kiếm, lọc và kiểm duyệt review theo khóa học, số sao, trạng thái hiển thị. Module được liên kết trực tiếp từ cột Đánh giá trong trang Quản lý Khóa học để điều hướng đúng ngữ cảnh.

- **Ảnh hưởng dự kiến:**  
  - Tăng tốc độ xử lý review tiêu cực/vi phạm.  
  - Đảm bảo chất lượng review hiển thị cho học viên được kiểm soát nhất quán.  
  - Giúp đội ngũ đánh giá được chất lượng từng khóa học dựa trên dữ liệu review có cấu trúc.

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý toàn bộ hệ thống, có quyền xem, lọc, cập nhật trạng thái hiển thị review, xóa review (nếu cần), và trả lời review.
- **QA (Chất lượng/Kiểm định)** – người kiểm định chất lượng nội dung, có quyền xem, lọc, cập nhật trạng thái hiển thị review, và trả lời review.

## 5. User Stories

### Điều hướng và Truy cập
1. Với tư cách **admin/QA**, tôi muốn mở module Review từ menu Admin để quản lý tất cả review toàn hệ thống.
2. Với tư cách **admin/QA**, tôi muốn click vào cột Đánh giá trong Quản lý Khóa học để đi đến module Review đã filter sẵn theo khóa học đó.

### Quản lý Danh sách Review
4. Với tư cách **admin/QA**, tôi muốn xem danh sách review với thông tin khóa học, học viên, số sao, nội dung, thời gian và trạng thái để dễ kiểm soát.
5. Với tư cách **admin/QA**, tôi muốn tìm kiếm review theo từ khóa (tên học viên, email, nội dung review) để xử lý nhanh.
6. Với tư cách **admin/QA**, tôi muốn lọc review theo khóa học, mức sao, trạng thái hiển thị, và khoảng thời gian để khoanh vùng vấn đề.
7. Với tư cách **admin/QA**, tôi muốn sắp xếp review theo mới nhất/cũ nhất hoặc số sao để ưu tiên xử lý.

### Xem chi tiết và Phản hồi Review
8. Với tư cách **admin/QA**, tôi muốn mở trang chi tiết review để xem đầy đủ thông tin và lịch sử phản hồi.
9. Với tư cách **admin/QA**, tôi muốn thêm phản hồi chính thức của hệ thống cho từng review để giải thích hoặc hướng dẫn học viên.

### Xóa và Khôi phục Review
10. Với tư cách **admin**, tôi muốn xóa review vi phạm/spam để bảo vệ chất lượng nền tảng.
11. Với tư cách **admin/QA**, tôi muốn xem lại các review đã xóa để kiểm tra lịch sử.
12. Với tư cách **admin**, tôi muốn khôi phục review đã xóa nếu phát hiện xóa nhầm.

## 6. Yêu cầu

### Chức năng

- **Điểm truy cập và Điều hướng**
  - Người dùng truy cập module từ menu `Quản lý Review` trong khu vực Admin.
  - Từ `Quản lý Khóa học`, khi click vào cột `Đánh giá` của một khóa học, điều hướng đến module Review với filter `Khóa học = [khóa học được chọn]`.
  - **Breadcrumb Navigation:** `Quản lý Review`

- **Trang Danh sách Review**
  - Hiển thị dạng bảng (table) với các cột:
    - **Khóa học:** Tên khóa học (click để mở trang Quản lý Khóa học của khóa học đó).
    - **Học viên:** Họ tên + email người đánh giá.
    - **Đánh giá:** Số sao (1-5) hiển thị bằng icon sao.
    - **Nội dung review:** Rút gọn 2-3 dòng, có nút `[Xem chi tiết]` nếu dài.
    - **Phản hồi hệ thống:** Hiển thị có/chưa có phản hồi.
    - **Thời gian tạo:** Ngày giờ review được tạo.
    - **Hành động:** `[Xóa]` (QA không có nút Xóa).
  - Mặc định chỉ hiển thị review chưa xóa.
  - Có tab để chuyển sang xem "Review đã xóa" (Admin/QA).
  - Hỗ trợ phân trang khi > 20 review/trang.
  - Có bộ lọc và tìm kiếm:
    - Tìm kiếm theo từ khóa: tên học viên, email, nội dung review.
    - Lọc theo khóa học.
    - Lọc theo số sao (1, 2, 3, 4, 5).
    - Lọc theo khoảng thời gian (từ ngày - đến ngày).
  - Hỗ trợ sắp xếp:
    - Mới nhất trước (mặc định).
    - Cũ nhất trước.
    - Số sao giảm dần/tăng dần.

- **Trang Chi tiết Review**
  - **Breadcrumb Navigation:** `Quản lý Review > Chi tiết Review`
  - Truy cập: Click vào nút `[Xem chi tiết]` hoặc click vào dòng review trong bảng danh sách.
  - **Hiển thị đầy đủ:**
    - Tên khóa học (có link đến trang Quản lý Khóa học)
    - Thông tin học viên (họ tên, email, avatar)
    - Số sao đánh giá
    - Nội dung review đầy đủ
    - Ngày giờ tạo review
    - Badge trạng thái nếu review đã bị xóa: `[Đã xóa]` màu đỏ
  - **Khu vực Phản hồi:**
    - Hiển thị danh sách phản hồi đã có (nếu có) với thông tin người phản hồi và thời gian.
    - Form nhập phản hồi mới với Rich Text Editor (có định dạng cơ bản + chèn link).
    - Nút `[Lưu phản hồi]`
    - Mỗi review có tối đa 1 phản hồi chính thức đang active (cho phép chỉnh sửa cập nhật nội dung phản hồi).
  - **Các hành động:**
    - Nếu review chưa xóa: Nút `[Xóa]` (chỉ Admin)
    - Nếu review đã xóa: Nút `[Khôi phục]` (chỉ Admin)
    - Nút `[Quay lại danh sách]`

- **Xóa Review (chỉ Admin)**
  - Nút `[Xóa]` chỉ hiện cho Admin (có trong bảng danh sách và trang chi tiết review).
  - Khi click, hiển thị modal xác nhận: `Bạn có chắc chắn muốn xóa review này?`
  - Nếu xác nhận, review được đánh dấu xóa.
  - Review đã xóa sẽ:
    - Không hiển thị bên phía học viên.
    - Không tính vào rating trung bình của khóa học.
    - Vẫn được lưu trong hệ thống để có thể xem lại hoặc khôi phục nếu cần.
  - Sau khi xóa từ trang chi tiết, tự động quay về trang danh sách.

- **Xem Review đã xóa (Admin/QA)**
  - Trong trang danh sách, có toggle/tab "Review đã xóa" để xem các review đã bị xóa.
  - Bảng review đã xóa hiển thị thêm cột: "Người xóa" và "Thời gian xóa".

- **Khôi phục Review (chỉ Admin)**
  - Trong trang chi tiết review đã xóa, hiển thị nút `[Khôi phục]`.
  - Khi click, review được khôi phục.
  - Review sau khi khôi phục sẽ hiển thị lại bên phía học viên và tính vào rating.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập module này.
  - **Admin:** Có quyền Xem, Lọc, Tìm kiếm, Phản hồi, Xóa, Xem review đã xóa, Khôi phục review.
  - **QA:** Có quyền Xem, Lọc, Tìm kiếm, Phản hồi review, Xem review đã xóa. Không có quyền Xóa hoặc Khôi phục review.

### Phi chức năng

- Trang danh sách phải tải < 400 ms với 1,000 review.
- Tìm kiếm + lọc kết hợp phải trả kết quả < 800 ms với dữ liệu 50,000 review.
- Phân trang, lọc, sắp xếp phải hoạt động ổn định và giữ nguyên state filter trên URL.
- Tuân thủ các yêu cầu phi chức năng chung trong Global UI Components PRD (WCAG AA, browser support, responsive).

## 7. Tiêu chí chấp nhận

### Điều hướng
- **Given** admin/QA đang ở trang Quản lý Khóa học  
  **When** click vào cột `Đánh giá` của khóa học A  
  **Then** điều hướng sang Quản lý Review với filter khóa học A được áp dụng sẵn

- **Given** admin/QA vào module Quản lý Review từ menu  
  **When** trang tải  
  **Then** hiển thị danh sách review toàn hệ thống

### Danh sách và Bộ lọc
- **Given** admin/QA vào trang Quản lý Review  
  **When** trang tải  
  **Then** hiển thị bảng review đầy đủ các cột đã định nghĩa

- **Given** admin/QA nhập từ khóa tìm kiếm  
  **When** từ khóa khớp tên học viên/email/nội dung review  
  **Then** trả về danh sách review phù hợp

- **Given** admin/QA chọn lọc `Số sao = 1`  
  **When** áp dụng bộ lọc  
  **Then** chỉ hiển thị review 1 sao chưa bị xóa

- **Given** admin/QA sắp xếp theo `Mới nhất trước`  
  **When** áp dụng sắp xếp  
  **Then** review mới nhất xuất hiện đầu danh sách

### Xem chi tiết Review
- **Given** admin/QA click vào nút `[Xem chi tiết]` hoặc click vào dòng review  
  **When** trang chi tiết tải  
  **Then** mở trang chi tiết review với breadcrumb `Quản lý Review > Chi tiết Review`

- **Given** admin/QA xem trang chi tiết review  
  **When** kiểm tra nội dung  
  **Then** hiển thị đầy đủ thông tin khóa học, học viên, số sao, nội dung review, trạng thái và ngày tạo

### Phản hồi Review
- **Given** admin/QA ở trang chi tiết review  
  **When** nhập nội dung phản hồi và nhấn `[Lưu phản hồi]`  
  **Then** phản hồi được lưu thành công và hiển thị trong khu vực phản hồi

- **Given** review đã có phản hồi  
  **When** admin/QA cập nhật nội dung phản hồi  
  **Then** hệ thống lưu phiên bản mới và hiển thị nội dung phản hồi mới nhất

- **Given** admin/QA ở trang chi tiết review  
  **When** nhấn nút `[Quay lại danh sách]`  
  **Then** quay về trang danh sách review với bộ lọc/tìm kiếm được giữ nguyên

### Xóa và Khôi phục Review
- **Given** QA truy cập danh sách review  
  **When** kiểm tra cột Hành động  
  **Then** không thấy nút `[Xóa]`

- **Given** Admin nhấn nút `[Xóa]` trên một review (từ danh sách hoặc trang chi tiết)  
  **When** xác nhận trong modal  
  **Then** review bị đánh dấu xóa và không còn hiển thị trong danh sách chính

- **Given** Admin xóa review từ trang chi tiết  
  **When** xác nhận xóa  
  **Then** review bị xóa và tự động quay về trang danh sách

- **Given** admin/QA chuyển sang tab "Review đã xóa"  
  **When** tab tải  
  **Then** hiển thị danh sách review đã xóa với thông tin người xóa và thời gian xóa

- **Given** Admin mở trang chi tiết review đã xóa  
  **When** kiểm tra  
  **Then** thấy badge `[Đã xóa]` và nút `[Khôi phục]`

- **Given** Admin nhấn nút `[Khôi phục]` trên review đã xóa  
  **When** xác nhận  
  **Then** review được khôi phục và hiển thị lại bên phía học viên

### Phân quyền
- **Given** người dùng không phải admin/QA cố gắng truy cập module Quản lý Review  
  **When** truy cập  
  **Then** hệ thống trả về lỗi 403 hoặc điều hướng về trang không có quyền

## 8. Ngoài phạm vi

- Cơ chế machine learning/AI để auto-detect review độc hại.
- Dashboard phân tích sentiment nâng cao.
- Gửi email tự động đến học viên khi review bị ẩn hoặc bị xóa.
- Cơ chế khiếu nại/appeal của học viên đối với review bị ẩn hoặc bị xóa.
