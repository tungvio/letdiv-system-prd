# PRD – Quản lý Hỏi đáp

## 1. Tên Tính năng  
**Quản lý Hỏi đáp** (Q&A Management Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Khi học viên tham gia khóa học, các câu hỏi và thắc mắc phát sinh liên tục. Đội ngũ quản trị cần một công cụ tập trung để theo dõi, trả lời các câu hỏi này kịp thời và đánh dấu những câu đã giải quyết xong để tránh bỏ sót.

- **Giải pháp:**  
  Xây dựng module Quản lý Hỏi đáp tập trung, cho phép admin/QA xem tất cả câu hỏi từ mọi khóa học, lọc theo khóa học/trạng thái, trả lời câu hỏi và đánh dấu "Đã giải quyết" khi hoàn tất.

- **Ảnh hưởng dự kiến:**  
  - Đảm bảo 100% câu hỏi của học viên được xem và có cơ hội được trả lời.
  - Đội ngũ admin/QA quản lý công việc hiệu quả hơn thông qua trạng thái rõ ràng.
  - Tăng cường tương tác và uy tín của nền tảng.

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý toàn bộ hệ thống, có quyền xem, trả lời, đánh dấu trạng thái, xóa và khôi phục câu hỏi.
- **QA (Chất lượng/Kiểm định)** – người kiểm tra chất lượng nội dung, có quyền xem, trả lời và đánh dấu trạng thái câu hỏi để đảm bảo các thắc mắc được xử lý đầy đủ.

## 5. User Stories

### Điều hướng và Truy cập
1. Với tư cách **admin/QA**, tôi muốn truy cập module Hỏi đáp từ menu Admin để quản lý câu hỏi của học viên.

### Quản lý Danh sách Câu hỏi
2. Với tư cách **admin/QA**, tôi muốn xem danh sách tất cả câu hỏi với thông tin người hỏi, khóa học, bài học, số câu trả lời và trạng thái.
3. Với tư cách **admin/QA**, tôi muốn lọc câu hỏi theo khóa học để tập trung vào nhóm câu hỏi cần xử lý.
4. Với tư cách **admin/QA**, tôi muốn lọc theo trạng thái (Đang chờ/Đã giải quyết) để ưu tiên xử lý câu hỏi chưa giải quyết.
5. Với tư cách **admin/QA**, tôi muốn tìm kiếm câu hỏi theo từ khóa để nhanh chóng tìm thắc mắc cụ thể.
6. Với tư cách **admin/QA**, tôi muốn sắp xếp theo mới nhất/cũ nhất để đảm bảo không bỏ sót câu hỏi.

### Xem chi tiết và Trả lời
7. Với tư cách **admin/QA**, tôi muốn mở trang chi tiết câu hỏi để xem đầy đủ nội dung và các câu trả lời đã có.
8. Với tư cách **admin/QA**, tôi muốn thêm câu trả lời mới cho câu hỏi để hỗ trợ học viên.
9. Với tư cách **admin/QA**, tôi muốn chỉnh sửa câu trả lời của chính mình nếu cần cập nhật thông tin.

### Đánh dấu Giải quyết
10. Với tư cách **admin/QA**, tôi muốn đánh dấu câu hỏi "Đã giải quyết" khi vấn đề đã được trả lời đầy đủ.
11. Với tư cách **admin/QA**, tôi muốn mở lại câu hỏi đã giải quyết nếu phát hiện cần bổ sung thêm thông tin.

## 6. Yêu cầu

### Chức năng

- **Điểm truy cập và Điều hướng**
  - Người dùng truy cập module từ menu `Quản lý Hỏi đáp` trong khu vực Admin.
  - **Breadcrumb Navigation:** `Quản lý Hỏi đáp`

- **Trang Danh sách Câu hỏi**
  - Hiển thị dạng bảng (table) với các cột:
    - **Câu hỏi:** Tiêu đề câu hỏi, rút gọn 1-2 dòng, có nút `[Xem chi tiết]` nếu dài.
    - **Người hỏi:** Họ tên + avatar học viên.
    - **Ngữ cảnh:** Hiển thị dạng `[Tên khóa học] > [Tên bài học]` để biết câu hỏi được đặt ở đâu.
    - **Số câu trả lời:** Tổng số câu trả lời hiện có (ví dụ: `3 câu trả lời`).
    - **Trạng thái:** `Đang chờ` hoặc `Đã giải quyết`.
    - **Thời gian tạo:** Ngày giờ đặt câu hỏi.
    - **Hành động:** Nút `[Xem & Trả lời]`.
  - Mặc định hiển thị câu hỏi chưa bị xóa.
  - Hỗ trợ phân trang khi > 20 câu hỏi/trang.
  - Có bộ lọc và tìm kiếm:
    - Tìm kiếm theo từ khóa: tiêu đề câu hỏi, nội dung câu hỏi, tên người hỏi.
    - Lọc theo khóa học.
    - Lọc theo trạng thái: `Đang chờ`, `Đã giải quyết`, `Tất cả`.
    - Lọc theo khoảng thời gian (từ ngày - đến ngày).
  - Hỗ trợ sắp xếp:
    - Mới nhất trước (mặc định).
    - Cũ nhất trước.

- **Trang Chi tiết Câu hỏi**
  - **Breadcrumb Navigation:** `Quản lý Hỏi đáp > Chi tiết Câu hỏi`
  - Truy cập: Click vào nút `[Xem & Trả lời]` hoặc click vào dòng câu hỏi trong bảng danh sách.
  - **Hiển thị đầy đủ:**
    - **Câu hỏi gốc:** Tiêu đề, nội dung đầy đủ, thông tin người hỏi (tên, avatar, email), ngày giờ đặt câu hỏi.
    - **Ngữ cảnh:** Tên khóa học và tên bài học (có link đến trang quản lý tương ứng).
    - **Trạng thái hiện tại:** Badge `Đang chờ` hoặc `Đã giải quyết`.
  - **Khu vực Câu trả lời:**
    - Hiển thị danh sách các câu trả lời đã có (sắp xếp theo thời gian, mới nhất trước).
    - Mỗi câu trả lời hiển thị: nội dung, thông tin người trả lời, thời gian.
    - Câu trả lời của chính mình có nút `[Sửa]` để chỉnh sửa.
  - **Form thêm câu trả lời mới:**
    - Rich Text Editor (hỗ trợ định dạng cơ bản + chèn link + code block).
    - Nút `[Gửi trả lời]`.
  - **Các hành động:**
    - Nếu câu hỏi đang ở trạng thái `Đang chờ`: Nút `[Đánh dấu Đã giải quyết]`.
    - Nếu câu hỏi đã `Đã giải quyết`: Nút `[Mở lại]` để chuyển về trạng thái `Đang chờ`.
    - Nút `[Quay lại danh sách]`.

- **Trả lời Câu hỏi**
  - Admin/QA có thể thêm câu trả lời mới bằng Rich Text Editor.
  - Có thể chỉnh sửa câu trả lời của chính mình.
  - Không thể sửa/xóa câu trả lời của người khác (bao gồm cả học viên).

- **Đánh dấu Trạng thái**
  - **Đánh dấu "Đã giải quyết":**
    - Khi click nút `[Đánh dấu Đã giải quyết]`, câu hỏi chuyển sang trạng thái `Đã giải quyết`.
    - Trạng thái này hiển thị ở cả danh sách và trang chi tiết.
    - Badge màu xanh để dễ nhận biết.
  - **Mở lại câu hỏi:**
    - Khi click nút `[Mở lại]`, câu hỏi chuyển về trạng thái `Đang chờ`.
    - Dùng khi phát hiện câu trả lời chưa đầy đủ hoặc cần bổ sung.

- **Xóa Câu hỏi (chỉ Admin)**
  - Admin có thể xóa câu hỏi vi phạm/spam.
  - Khi click xóa, hiển thị modal xác nhận: `Bạn có chắc chắn muốn xóa câu hỏi này?`
  - Khi xóa, câu hỏi được đánh dấu xóa (không hiển thị cho học viên).
  - Admin/QA có thể xem lại câu hỏi đã xóa để kiểm tra lịch sử.
  - Chỉ Admin có quyền khôi phục câu hỏi đã xóa.
  - Tab `Câu hỏi đã xóa` hiển thị thêm thông tin: người xóa và thời gian xóa.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập module này.
  - **Admin:** Có quyền xem toàn bộ câu hỏi, trả lời, chỉnh sửa câu trả lời của mình, đánh dấu trạng thái, xóa câu hỏi, xem và khôi phục câu hỏi đã xóa.
  - **QA:** Có quyền xem toàn bộ câu hỏi, trả lời, chỉnh sửa câu trả lời của mình, đánh dấu trạng thái và xem câu hỏi đã xóa. Không có quyền xóa hoặc khôi phục câu hỏi.

### Phi chức năng

- Trang danh sách phải tải < 500 ms với 1,000 câu hỏi.
- Tìm kiếm + lọc kết hợp phải trả kết quả < 800 ms.
- Rich Text Editor phải tương thích với các trình duyệt chính (Chrome, Firefox, Safari, Edge).
- Tuân thủ các yêu cầu phi chức năng chung trong Global UI Components PRD (WCAG AA, browser support, responsive).

## 7. Tiêu chí chấp nhận

### Điều hướng
- **Given** admin/QA vào module Quản lý Hỏi đáp từ menu  
  **When** trang tải  
  **Then** hiển thị danh sách câu hỏi toàn hệ thống (hoặc theo phạm vi được phân quyền)

### Danh sách và Bộ lọc
- **Given** admin/QA vào trang Quản lý Hỏi đáp  
  **When** trang tải  
  **Then** hiển thị bảng câu hỏi đầy đủ các cột đã định nghĩa

- **Given** admin/QA nhập từ khóa tìm kiếm  
  **When** từ khóa khớp tiêu đề/nội dung câu hỏi/tên người hỏi  
  **Then** trả về danh sách câu hỏi phù hợp

- **Given** admin/QA chọn lọc `Trạng thái = Đang chờ`  
  **When** áp dụng bộ lọc  
  **Then** chỉ hiển thị câu hỏi chưa giải quyết

- **Given** admin/QA sắp xếp theo `Cũ nhất trước`  
  **When** áp dụng sắp xếp  
  **Then** câu hỏi cũ nhất xuất hiện đầu danh sách

### Xem chi tiết Câu hỏi
- **Given** admin/QA click vào nút `[Xem & Trả lời]` hoặc click vào dòng câu hỏi  
  **When** trang chi tiết tải  
  **Then** mở trang chi tiết câu hỏi với breadcrumb `Quản lý Hỏi đáp > Chi tiết Câu hỏi`

- **Given** admin/QA xem trang chi tiết câu hỏi  
  **When** kiểm tra nội dung  
  **Then** hiển thị đầy đủ câu hỏi gốc, ngữ cảnh, trạng thái, danh sách câu trả lời

### Trả lời Câu hỏi
- **Given** admin/QA ở trang chi tiết câu hỏi  
  **When** nhập nội dung trả lời và nhấn `[Gửi trả lời]`  
  **Then** câu trả lời được lưu thành công và hiển thị trong danh sách câu trả lời

- **Given** admin/QA đã trả lời câu hỏi  
  **When** nhấn nút `[Sửa]` trên câu trả lời của mình  
  **Then** mở form chỉnh sửa và có thể cập nhật nội dung

- **Given** admin/QA cập nhật nội dung câu trả lời  
  **When** nhấn `[Lưu]`  
  **Then** hệ thống lưu phiên bản mới và hiển thị nội dung đã cập nhật

### Đánh dấu Trạng thái
- **Given** câu hỏi đang ở trạng thái `Đang chờ`  
  **When** admin/QA nhấn `[Đánh dấu Đã giải quyết]`  
  **Then** câu hỏi chuyển sang `Đã giải quyết` và badge đổi màu xanh

- **Given** câu hỏi đã `Đã giải quyết`  
  **When** admin/QA nhấn `[Mở lại]`  
  **Then** câu hỏi chuyển về `Đang chờ`

### Quay lại Danh sách
- **Given** admin/QA ở trang chi tiết câu hỏi  
  **When** nhấn nút `[Quay lại danh sách]`  
  **Then** quay về trang danh sách với bộ lọc/tìm kiếm được giữ nguyên

### Xóa và Khôi phục
- **Given** Admin nhấn nút `[Xóa]` trên một câu hỏi  
  **When** xác nhận trong modal  
  **Then** câu hỏi bị đánh dấu xóa và không còn hiển thị trong danh sách chính

- **Given** admin/QA chuyển sang tab "Câu hỏi đã xóa"  
  **When** tab tải  
  **Then** hiển thị danh sách câu hỏi đã xóa với thông tin người xóa và thời gian xóa

- **Given** Admin mở trang chi tiết câu hỏi đã xóa  
  **When** kiểm tra  
  **Then** thấy badge `[Đã xóa]` và nút `[Khôi phục]`

- **Given** Admin nhấn nút `[Khôi phục]` trên câu hỏi đã xóa  
  **When** xác nhận  
  **Then** câu hỏi được khôi phục và hiển thị lại cho học viên

### Phân quyền
- **Given** người dùng không phải admin/QA cố gắng truy cập module Quản lý Hỏi đáp  
  **When** truy cập  
  **Then** hệ thống trả về lỗi 403 hoặc điều hướng về trang không có quyền

- **Given** QA truy cập  
  **When** xem danh sách câu hỏi  
  **Then** thấy toàn bộ câu hỏi, có thể trả lời và đánh dấu trạng thái nhưng không có quyền xóa/khôi phục

- **Given** Admin truy cập  
  **When** xem danh sách câu hỏi  
  **Then** thấy toàn bộ câu hỏi từ tất cả khóa học

## 8. Ngoài phạm vi

- Hệ thống phân công (assignment) câu hỏi cho giảng viên/TA cụ thể.
- Upvote/downvote câu trả lời.
- Đánh dấu "Câu trả lời chính thức" hoặc "Pin câu trả lời tốt nhất".
- Báo cáo/thống kê (thời gian trả lời trung bình, số câu hỏi mỗi giảng viên xử lý).
- Chỉnh sửa/xóa câu hỏi hoặc câu trả lời của người khác.
- Thông báo real-time cho giảng viên khi có câu hỏi mới.
- Tính năng @mention hoặc tag người khác trong câu trả lời.
