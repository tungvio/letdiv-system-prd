# PRD – Quản lý Học viên

## 1. Tên Tính năng  
**Quản lý Học viên** (Student Management Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Khi nền tảng có nhiều học viên, đội admin và QA gặp khó khăn trong việc
  tra cứu thông tin học viên, xử lý thắc mắc tài khoản và xem lịch sử học tập.  
  Họ phải dùng nhiều công cụ rời rạc hoặc nhờ dev, dẫn đến phản hồi chậm và hiệu suất thấp.

- **Giải pháp:**  
  Xây dựng một module quản trị tập trung cho phép
  admin và QA tìm kiếm học viên, xem hồ sơ chi tiết và ghi chú/ticket
  liên quan. Giao diện phải nhanh, dễ dùng, và hỗ trợ bộ lọc cơ bản.

- **Ảnh hưởng dự kiến:**  
  - Giảm thời gian phản hồi support ticket xuống < 1 phút/học viên.  
  - Giảm tải cho dev team với các yêu cầu “xem giúp”.  
  - Cải thiện độ chính xác khi xử lý sự cố tài khoản.

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý hệ thống hiện tại, cần truy cập danh sách học viên, báo cáo, ghi chú và thực hiện các thao tác quản lý toàn nền tảng.  
- **QA (Chất lượng/Kiểm định lớp học)** – người kiểm định và quản lý chất lượng lớp học, cần xem thông tin học viên, tiến độ học tập và ghi chú để giám sát lớp học.

## 5. User Stories

1. Với tư cách **admin**, tôi muốn tìm kiếm học viên theo tên hoặc email để
   nhanh chóng xác định họ.
2. Với tư cách **admin**, tôi muốn xem hồ sơ học viên bao gồm ngày
   đăng ký và tiến độ học để hiểu rõ trạng thái của họ.
3. Với tư cách **admin**, tôi muốn thêm ghi chú nội bộ trên trang học viên để
   ghi lại lịch sử tương tác.
4. Với tư cách **admin**, tôi muốn lọc danh sách học viên theo trạng thái (active/disabled) và khoảng ngày đăng ký để dễ dàng tìm kiếm nhóm học viên cụ thể.
5. Với tư cách **admin**, tôi muốn xem danh sách học viên được phân trang (mỗi trang 20 bản ghi) để hệ thống tải nhanh khi có hàng nghìn học viên.
6. Với tư cách **admin**, tôi muốn khóa hoặc tạm ngưng tài khoản học viên khi cần thiết để ngăn họ đăng nhập.
7. Với tư cách **admin**, tôi muốn xem lịch sử giao dịch/mua hàng của học viên để
   theo dõi các đơn mua sản phẩm đơn lẻ và khóa học.
8. Với tư cách **QA**, tôi muốn xem danh sách học viên và tiến độ của họ để hỗ trợ quản lý học viên.
9. Với tư cách **admin**, tôi muốn xem tất cả khóa học mà học viên đã đăng ký kèm theo tiến độ hoàn thành để đánh giá mức độ tham gia.
10. Với tư cách **admin/QA**, tôi muốn xem thông báo khi không tìm thấy học viên nào khớp với tiêu chí tìm kiếm để biết cần điều chỉnh tìm kiếm.
11. Với tư cách **admin/QA**, tôi muốn xem danh sách ghi chú đã tạo trên hồ sơ học viên để theo dõi lịch sử tương tác.

## 6. Yêu cầu

### Chức năng

- **Trang danh sách học viên**
  - Mục menu “Quản lý Học viên” trong thanh điều hướng.
  - Bảng hiển thị: Avatar, Tên hiển thị, Email, Ngày đăng ký.
  - Thanh tìm kiếm (theo tên/email, không phân biệt hoa thường, tìm kiếm con chuỗi).
  - Phân trang khi >20 bản ghi.
  - Bộ lọc: trạng thái (active/disabled), khoảng ngày đăng ký.
  - Nút `[Xem chi tiết]` cho mỗi hàng.
  - **Hành động khóa tài khoản** (chỉ admin): nút khóa/tạm ngưng hiển thị cho mỗi học viên.
- **Trang chi tiết học viên**
  - Breadcrumb: `Quản lý Học viên > Chi tiết: [Tên]`.
  - Phần header với avatar, tên, email, ngày đăng ký (chỉ đọc).
  - **Nút hành động**: admin có thể khóa/tạm ngưng từ trang chi tiết.
  - Giao diện tab:
    - **Lịch sử Học tập:** danh sách tất cả khóa học, mỗi khóa kèm thanh tiến độ.
    - **Ghi chú:** khu vực nhập text + danh sách ghi chú đã tạo (hiển thị người tạo, thời gian). Admin và QA đều có thể thêm ghi chú.
    - **Giao dịch (Chỉ Admin):** danh sách các đơn mua (ngày mua, tên sản phẩm/khóa học, giá, trạng thái: Đang xử lý/Hoàn thành/Thất bại). Sắp xếp theo ngày (mới nhất trước). Có bộ lọc theo trạng thái và khoảng thời gian. Tab này chỉ hiển thị khi đăng nhập với vai trò admin, QA không nhìn thấy tab này vì đó là thông tin tài chính.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập khu vực quản lý học viên.
  - Admin có quyền thực hiện tất cả hành động bao gồm khóa/tạm ngưng tài khoản và xem tab giao dịch.
  - QA có toàn quyền xem (tìm kiếm, lọc, thêm ghi chú) NGOẠI TRỪ tab "Giao dịch" (ẩn hoàn toàn với QA) và không thể khóa tài khoản.


### Phi chức năng

- Trang danh sách phải tải <500 ms với 1000 học viên.
- Mọi hành động đều được log (ai xem, ai thêm ghi chú, ai khóa tài khoản).
- UI tuân WCAG AA (accessibility).
- Hỗ trợ các trình duyệt: Chrome, Firefox, Safari, Edge (phiên bản mới nhất).
- Responsive cho tablet và desktop.

## 7. Tiêu chí chấp nhận

### Tìm kiếm và Lọc
- **Given** admin/QA nhập từ khóa vào thanh tìm kiếm  
  **When** từ khóa khớp với tên hoặc email học viên (không phân biệt hoa thường)  
  **Then** hiển thị danh sách học viên khớp với kết quả

- **Given** admin/QA chọn bộ lọc trạng thái "Đang hoạt động" hoặc "Đã vô hiệu hóa"  
  **When** áp dụng bộ lọc  
  **Then** chỉ hiển thị học viên có trạng thái tương ứng

- **Given** không có học viên nào khớp với tiêu chí tìm kiếm  
  **When** thực hiện tìm kiếm  
  **Then** hiển thị thông báo "Không tìm thấy học viên nào"

### Phân trang
- **Given** có hơn 20 học viên trong danh sách  
  **When** tải trang danh sách  
  **Then** hiển thị 20 học viên đầu tiên và các nút điều hướng phân trang

### Chi tiết học viên
- **Given** admin/QA nhấn nút `[Xem chi tiết]`  
  **When** trang chi tiết tải  
  **Then** hiển thị đúng thông tin học viên (avatar, tên, email, ngày đăng ký)

- **Given** admin xem trang chi tiết học viên  
  **When** chọn tab "Lịch sử Học tập"  
  **Then** hiển thị danh sách khóa học đã đăng ký với thanh tiến độ cho mỗi khóa

### Ghi chú
- **Given** admin/QA thêm ghi chú mới  
  **When** lưu ghi chú  
  **Then** ghi chú hiển thị ngay trong danh sách kèm tên người tạo và thời gian

### Khóa tài khoản
- **Given** admin nhấn nút khóa/tạm ngưng tài khoản  
  **When** xác nhận hành động  
  **Then** tài khoản học viên bị khóa và học viên không thể đăng nhập

### Phân quyền
- **Given** QA đăng nhập và xem trang chi tiết học viên  
  **When** kiểm tra các tab hiển thị  
  **Then** chỉ thấy tab "Lịch sử Học tập" và "Ghi chú", không thấy tab "Giao dịch"

- **Given** admin đăng nhập và xem trang chi tiết học viên  
  **When** kiểm tra các tab hiển thị  
  **Then** thấy đầy đủ 3 tab: "Lịch sử Học tập", "Ghi chú" và "Giao dịch"

- **Given** admin chọn tab "Giao dịch"  
  **When** tab tải  
  **Then** hiển thị danh sách giao dịch đầy đủ

- **Given** người dùng không phải admin/QA truy cập module  
  **When** cố gắng truy cập  
  **Then** hệ thống trả về lỗi 403

## 8. Ngoài phạm vi

- Đặt lại mật khẩu (hệ thống dùng Google OAuth).
- Bulk import/export học viên.
- Gửi email thông báo tự động cho học viên.