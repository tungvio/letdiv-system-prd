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

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý toàn bộ hệ thống, cần điều hướng nhanh giữa các module quản trị và thực hiện các thao tác quản lý toàn nền tảng.
- **QA (Chất lượng/Kiểm định)** – người kiểm tra chất lượng hệ thống, cần xem các module khác nhau một cách hiệu quả để kiểm định và giám sát hoạt động của hệ thống.

## 5. User Stories

### Sidebar Navigation (Menu bên trái)
1. Với tư cách **admin**, tôi muốn xem một menu điều hướng rõ ràng ở bên trái màn hình để nhanh chóng truy cập bất kỳ module nào.
2. Với tư cách **admin**, tôi muốn nhấp vào logo LetDiv ở Sidebar để quay lại Dashboard từ bất kỳ trang nào.
3. Với tư cách **admin**, tôi muốn menu Sidebar hiển thị mục hiện tại được làm nổi bật để tôi biết mình đang ở đâu.
4. Với tư cách **admin**, tôi muốn nhấp vào menu không có menu con để điều hướng đến trang tương ứng ngay lập tức.
5. Với tư cách **admin**, tôi muốn nhấp vào menu cha (có menu con) để mở rộng/thu gọn danh sách menu con mà không bị điều hướng.

### Top Bar (Thanh Header ngang)
6. Với tư cách **admin**, tôi muốn xem các thông báo mới từ một biểu tượng chuông ở Top Bar để xử lý các vấn đề nhanh chóng.
7. Với tư cách **admin**, tôi muốn xem thông tin tài khoản của tôi và có nút đăng xuất dễ tìm ở Top Bar.

### Page Header (Khu vực nội dung)
8. Với tư cách **admin**, tôi muốn mỗi trang có breadcrumb để biết vị trí hiện tại và quay lại các cấp cao hơn.
9. Với tư cách **admin**, tôi muốn mỗi trang có tiêu đề rõ ràng ở đầu để biết trang hiện tại làm gì.

### Hệ thống Phản hồi
10. Với tư cách **admin**, tôi muốn nhận được thông báo Toast khi một hành động thành công hoặc thất bại.
11. Với tư cách **admin**, tôi muốn có hộp thoại xác nhận trước khi thực hiện hành động quan trọng như xóa dữ liệu.

## 6. Yêu cầu

### Chức năng

- **Thanh Điều hướng Bên trái (Vertical Sidebar)**
  - Logo LetDiv ở vị trí cao nhất: khi nhấp sẽ điều hướng đến Dashboard.
  - Menu navigation với cấu trúc phân cấp, gồm 2 loại:
    - **Menu đơn (không có menu con):** Khi nhấp sẽ điều hướng đến trang tương ứng ngay lập tức.
    - **Menu cha (có menu con):** Khi nhấp sẽ mở rộng/thu gọn để hiển thị/ẩn các menu con, không điều hướng.
  - Các mục menu con khi nhấp sẽ điều hướng đến trang tương ứng.
  - Mục menu của trang hiện tại phải được làm nổi bật (highlight active state).
  - **Trạng thái mặc định:** Khi load trang lần đầu, tất cả menu cha ở trạng thái mở (expanded).
  - Menu gồm các mục:
    - Tổng quan (Dashboard) - menu đơn [Cả Admin & QA]
    - Khóa học video - menu đơn [Cả Admin & QA]
    - Tương tác & Dịch vụ (menu cha) → Hỏi & Đáp (menu con) [Chỉ Admin]
    - Quản lý Người dùng - menu đơn [Cả Admin & QA]
    - Quản lý Tài chính (menu cha) → Lịch sử Giao dịch (menu con) [Chỉ Admin]

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
    - **Breadcrumb Navigation:** Hiển thị đường dẫn phân cấp (ví dụ: `Khóa học video > Khóa học ABC > Chương 1`). Mỗi cấp là link để quay lại.
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
    - Ví dụ: "Bạn chắc chắn muốn xóa khóa học video này?"

- **Phân quyền**
  - **Admin (Quản trị hệ thống):**
    - Truy cập tất cả menu: Dashboard, Khóa học video, Tương tác & Dịch vụ (Hỏi & Đáp), Quản lý Người dùng, Quản lý Tài chính.
    - Có quyền thực hiện tất cả hành động trên hệ thống.
  - **QA (Chất lượng/Kiểm định):**
    - Chỉ truy cập: Dashboard, Khóa học video, Quản lý Người dùng.
    - Không nhìn thấy menu: Tương tác & Dịch vụ, Quản lý Tài chính.
    - Sidebar chỉ hiển thị các menu mà QA có quyền truy cập.

### Phi chức năng

- Sidebar cần tải <200 ms.
- Toast notification phải hiển thị < 100 ms.
- UI tuân WCAG AA (accessibility).
- Hỗ trợ các trình duyệt: Chrome, Firefox, Safari, Edge (phiên bản mới nhất).
- Consistent styling across tất cả trang.
- Responsive cho tablet và desktop.

## 7. Tiêu chí chấp nhận

### Sidebar Navigation
- **Given** admin đang xem bất kỳ trang nào  
  **When** nhìn vào thanh Sidebar  
  **Then** nhìn thấy menu điều hướng với tất cả các mục chính và mục con được tổ chức

- **Given** admin nhấp vào menu đơn (không có menu con) như "Dashboard"  
  **When** click  
  **Then** điều hướng đến trang tương ứng ngay lập tức

- **Given** admin nhấp vào menu cha (có menu con) như "Tương tác & Dịch vụ"  
  **When** click lần đầu (đang mở)  
  **Then** menu thu gọn và ẩn các menu con đi một cách mượt mà

- **Given** admin nhấp vào menu cha đang đóng  
  **When** click lần nữa  
  **Then** menu mở rộng và hiển thị các menu con, không điều hướng

- **Given** admin nhấp vào menu con như "Hỏi & Đáp"  
  **When** click  
  **Then** điều hướng đến trang Hỏi & Đáp

- **Given** admin đang xem trang "Hỏi & Đáp"  
  **When** observe menu  
  **Then** mục "Hỏi & Đáp" được làm nổi bật/active và menu cha "Tương tác & Dịch vụ" đang mở

- **Given** admin load trang lần đầu  
  **When** trang tải xong  
  **Then** tất cả menu cha (Tương tác & Dịch vụ, Quản lý Tài chính) ở trạng thái mở

- **Given** admin nhấp vào logo LetDiv  
  **When** trang tải  
  **Then** điều hướng về Dashboard

- **Given** QA đăng nhập vào hệ thống  
  **When** xem Sidebar  
  **Then** chỉ thấy menu: Dashboard, Khóa học video, Quản lý Người dùng (không thấy Tương tác & Dịch vụ, Quản lý Tài chính)

- **Given** Admin đăng nhập vào hệ thống  
  **When** xem Sidebar  
  **Then** thấy tất cả menu: Dashboard, Khóa học video, Tương tác & Dịch vụ, Quản lý Người dùng, Quản lý Tài chính

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
