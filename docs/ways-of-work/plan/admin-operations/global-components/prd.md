# PRD – Thành Phần Giao Diện Toàn Cục

## 1. Tên Tính năng  
**Thành Phần Giao Diện Toàn Cục** (Global UI Components Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Một hệ thống quản trị bao gồm nhiều module chức năng khác nhau. Nếu không có một bộ khung giao diện chung, mỗi trang sẽ trông khác biệt, gây khó khăn cho người dùng trong việc điều hướng, xác định vị trí và thực hiện các hành động quen thuộc. Hiệu suất làm việc sẽ giảm xuống và tạo cảm giác không chuyên nghiệp.

- **Giải pháp:**  
  Thiết kế và định nghĩa một tập hợp các thành phần giao diện toàn cục cho admin area, bao gồm: Sidebar điều hướng, Top Bar (thanh tiêu đề trên cùng), cấu trúc chuẩn cho khu vực nội dung chính, và hệ thống thông báo phản hồi. Các thành phần này sẽ được áp dụng nhất quán trên tất cả các trang trong khu vực quản trị.

- **Ảnh hưởng dự kiến:**  
  - Tạo sự nhất quán: Mọi trang tuân theo cấu trúc bố cục và phong cách thiết kế chung.
  - Cải thiện khả năng điều hướng: Người dùng di chuyển giữa các module một cách hiệu quả.
  - Nâng cao trải nghiệm: Giảm tải nhận thức, tăng hiệu suất làm việc cho đội ngũ quản trị.

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator)** – người quản lý toàn bộ hệ thống, cần điều hướng nhanh giữa các module quản trị.
- **Quản lý Nội dung (Content Manager)** – người quản lý khóa học, bài giảng, cần truy cập nhanh đến các phần nội dung.
- **QA (Chất lượng/Kiểm định)** – người kiểm tra chất lượng hệ thống, cần xem các module khác nhau một cách hiệu quả.
- **Hỗ trợ Khách hàng (Support Team)** – người xử lý các yêu cầu học viên, cần truy cập thông báo và thông tin từng học viên.

## 5. User Stories

1. Với tư cách **admin**, tôi muốn xem một menu điều hướng rõ ràng ở bên trái màn hình để nhanh chóng truy cập bất kỳ module nào.
2. Với tư cách **admin**, tôi muốn nhấp vào logo LetDiv từ bất kỳ trang nào để quay lại Dashboard.
3. Với tư cách **admin**, tôi muốn menu điều hướng hiển thị mục hiện tại được làm nổi bật để tôi biết mình đang ở đâu.
4. Với tư cách **admin**, tôi muốn các mục menu có thể mở rộng/thu gọn để xem các mục con mà không làm lộn xộn toàn bộ danh sách.
5. Với tư cách **admin/support**, tôi muốn xem các thông báo mới từ một biểu tượng chuông ở thanh tiêu đề để xử lý các vấn đề nhanh chóng.
6. Với tư cách **admin**, tôi muốn xem thông tin tài khoản của tôi và có nút đăng xuất dễ tìm ở thanh tiêu đề.
7. Với tư cách **admin**, tôi muốn mỗi trang có breadcrumb để biết vị trí hiện tại và quay lại các cấp cao hơn.
8. Với tư cách **admin**, tôi muốn mỗi trang có tiêu đề rõ ràng ở đầu để biết trang hiện tại làm gì.
9. Với tư cách **admin**, tôi muốn nhận được thông báo Toast khi một hành động thành công hoặc thất bại.
10. Với tư cách **admin**, tôi muốn có hộp thoại xác nhận trước khi thực hiện hành động quan trọng như xóa dữ liệu.

## 6. Yêu cầu

### Chức năng

- **Thanh Điều hướng Bên trái (Vertical Sidebar)**
  - Logo LetDiv ở vị trí cao nhất: khi nhấp sẽ điều hướng đến Dashboard.
  - Menu navigation với cấu trúc phân cấp (menu chính → mục con).
  - Menu chính có thể mở/đóng để xem/ẩn mục con.
  - Các mục menu con khi nhấp sẽ điều hướng đến trang tương ứng.
  - Mục menu của trang hiện tại phải được làm nổi bật (highlight active state).
  - Menu gồm các mục:
    - Tổng quan (Dashboard)
    - Quản lý Nội dung → Khóa học
    - Tương tác & Dịch vụ → Hỏi & Đáp, Chấm bài
    - Quản lý Người dùng
    - Quản lý Tài chính → Lịch sử Giao dịch

- **Thanh Header Ngang (Top Bar)**
  - Luôn cố định ở trên cùng, bên phải của Sidebar.
  - Chứa: Trung tâm Thông báo (Notification Center), Menu Tài khoản Người dùng.
  - **Trung tâm Thông báo:**
    - Icon chuông (🔔) với chỉ báo (chấm đỏ/số) khi có thông báo mới chưa đọc.
    - Khi nhấp, hiển thị danh sách thông báo dạng dropdown.
    - Mỗi thông báo là link dẫn đến trang xử lý tương ứng.
  - **Menu Tài khoản:**
    - Hiển thị Avatar + Tên nhân viên đang đăng nhập.
    - Khi nhấp, mở menu dropdown với nút **[Đăng xuất]**.

- **Khu vực Nội dung Chính**
  - Mỗi trang bắt đầu bằng **Page Header** chứa:
    - **Breadcrumb Navigation:** Hiển thị đường dẫn phân cấp (ví dụ: `Quản lý Nội dung > Khóa học > Chương`). Mỗi cấp là link để quay lại.
    - **Page Title:** Tiêu đề trang rõ ràng, to, đậm (h1).
  - Nội dung chính của module hiển thị dưới Page Header.

- **Hệ thống Phản hồi Toàn cục**
  - **Toast Notifications:**
    - Hiển thị tự động ở góc màn hình (trên cùng bên phải).
    - Các loại: Thành công (xanh), Cảnh báo (vàng), Lỗi (đỏ).
    - Tự động ẩn sau 3-5 giây hoặc nhấp để đóng.
    - Ví dụ: "Cập nhật thành công!", "Đã có lỗi xảy ra."
  - **Modal/Pop-up Xác nhận:**
    - Hiện ra giữa màn hình tránh các hành động quan trọng (xóa, khóa tài khoản).
    - Chặn tương tác với phần còn lại của trang.
    - Có nút **[Xác nhận]** và **[Hủy]**.
    - Ví dụ: "Bạn chắc chắn muốn xóa khóa học này?"

### Phi chức năng

- Sidebar cần tải <200 ms.
- Top Bar phải responsive và hiển thị đúng trên desktop, tablet.
- Toast notification phải hiển thị < 100 ms.
- UI tuân WCAG AA (accessibility).
- Hỗ trợ các trình duyệt: Chrome, Firefox, Safari, Edge (phiên bản mới nhất).
- Consistent styling across tất cả trang.

## 7. Tiêu chí chấp nhận

### Sidebar Navigation
- **Given** admin đang xem bất kỳ trang nào  
  **When** nhìn vào thanh Sidebar  
  **Then** nhìn thấy menu điều hướng với tất cả các mục chính và mục con được tổ chức

- **Given** admin nhấp vào menu chính có mục con  
  **When** menu mở/đóng  
  **Then** các mục con hiển thị/ẩn đi một cách mượt mà

- **Given** admin đang xem trang "Khóa học"  
  **When** observe menu  
  **Then** mục "Khóa học" được làm nổi bật/active

- **Given** admin nhấp vào logo LetDiv  
  **When** trang tải  
  **Then** điều hướng về Dashboard

### Top Bar
- **Given** admin xem thanh Top Bar  
  **When** kiểm tra các phần tử  
  **Then** thấy icon thông báo và menu tài khoản ở bên phải

- **Given** có thông báo mới chưa đọc  
  **When** xem icon thông báo  
  **Then** hiển thị chỉ báo (chấm đỏ hoặc số)

- **Given** admin nhấp vào icon thông báo  
  **When** dropdown mở  
  **Then** hiển thị danh sách thông báo với link đến trang xử lý

- **Given** admin nhấp vào menu tài khoản  
  **When** dropdown mở  
  **Then** thấy Avatar, Tên, nút **[Đăng xuất]**

### Page Header
- **Given** admin truy cập một trang bất kỳ  
  **When** trang tải  
  **Then** thấy Breadcrumb ở trên cùng và Page Title rõ ràng phía dưới

- **Given** admin nhấp vào breadcrumb cấp cao hơn  
  **When** điều hướng  
  **Then** quay lại trang tương ứng

### Thông báo
- **Given** admin thực hiện hành động thành công (lưu, xóa)  
  **When** hành động hoàn tất  
  **Then** Toast notification xuất hiện với tin nhắn thành công

- **Given** admin thực hiện hành động thất bại  
  **When** hành động bị lỗi  
  **Then** Toast notification xuất hiện với tin nhắn lỗi

- **Given** admin thực hiện hành động quan trọng (xóa dữ liệu)  
  **When** kích hoạt hành động  
  **Then** Modal xác nhận hiện ra với tin nhắn rõ ràng và nút **[Xác nhận]**, **[Hủy]**

- **Given** admin nhấp **[Xác nhận]** trong modal  
  **When** xác nhận  
  **Then** hành động được thực hiện

- **Given** admin nhấp **[Hủy]** trong modal  
  **When** hủy  
  **Then** modal đóng, hành động không thực hiện

## 8. Ngoài phạm vi

- Tùy chỉnh theme/giao diện cho từng người dùng (dark mode, light mode).
- Multi-language support (hiện tại là tiếng Việt).
- Advanced notification filtering/preferences.
- Drag-and-drop để custom sidebar menu order.
- Mobile app version (hiện tại là web).
- Real-time collaboration features.
- Animation/transition details (sẽ xác định trong Design System sau).
