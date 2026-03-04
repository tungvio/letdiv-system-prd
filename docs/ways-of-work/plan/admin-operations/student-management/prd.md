# PRD – Bảng điều khiển Quản lý Học viên

## 1. Tên Tính năng  
**Khu vực Quản lý Học viên** (Student Management Page)

## 2. Epic  
Thuộc epic **Công cụ vận hành/admin**  
(xem PRD/kiến trúc gốc của Epic "Operational Tools for Admin & QA Team").

## 3. Mục tiêu

- **Vấn đề:**  
  Khi nền tảng có nhiều học viên, đội admin và QA gặp khó khăn trong việc
  tra cứu thông tin học viên, xử lý thắc mắc tài khoản và xem lịch sử học tập.  
  Họ phải dùng nhiều công cụ rời rạc hoặc nhờ dev, dẫn đến phản hồi chậm và hiệu suất thấp.

- **Giải pháp:**  
  Xây dựng một khu vực quản trị tập trung (Khu vực Quản lý Học viên) cho phép
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
4. Với tư cách **admin**, tôi muốn lọc và phân trang danh sách học viên để duyệt
   bộ tài khoản lớn.
5. Với tư cách **admin**, tôi muốn khóa hoặc tạm ngưng tài khoản học viên khi cần thiết để ngăn họ đăng nhập.
6. Với tư cách **admin**, tôi muốn xem lịch sử giao dịch/mua hàng của học viên để
   theo dõi các đơn mua sản phẩm đơn lẻ và khóa học.
7. Với tư cách **QA**, tôi muốn xem danh sách học viên trong lớp học và tiến độ của họ để hỗ trợ quản lý hoc viên.
8. Với tư cách **admin**, tôi muốn xem tất cả khóa học mà học viên đã đăng ký kèm theo tiến độ.

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
    - **Ghi chú:** khu vực text + danh sách ghi chú.
    - **Giao dịch:** danh sách các đơn mua sản phẩm/khóa học đơn lẻ (ngày, sản phẩm, giá, trạng thái).
  - Admin và QA có thể thêm ghi chú; mỗi ghi chú lưu kèm người tạo và thời gian.

- **Tab Giao dịch (Chỉ Admin)**
  - Hiển thị danh sách các đơn mua (transactions): ngày mua, tên sản phẩm/khóa học, giá, trạng thái (pending/completed/failed).
  - Sắp xếp theo ngày (mới nhất trước).
  - (Tùy chọn) bộ lọc: trạng thái, khoảng thời gian.
  - **Lưu ý:** QA không có quyền truy cập tab này vì đó là thông tin tài chính.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập khu vực quản lý học viên.
  - Admin có quyền thực hiện tất cả hành động bao gồm khóa/tạm ngưng tài khoản và xem tab giao dịch.
  - QA có toàn quyền xem (tìm kiếm, lọc, thêm ghi chú) NGOẠI TRỪ tab "Giao dịch" (chỉ admin được xem) và không thể khóa tài khoản.
  - Sử dụng guards dựa trên vai trò (`@Roles('admin','qa')`).


### Phi chức năng

- Trang danh sách phải tải <500 ms với 1000 học viên.
- Các truy vấn tìm kiếm phải được index hoá.
- Mọi hành động đều được log (ai xem, ai thêm ghi chú).
- UI tuân WCAG AA.

## 7. Tiêu chí chấp nhận

- [ ] Tìm kiếm bằng tên/email trả đúng kết quả.
- [ ] Nhấn `[Xem chi tiết]` dẫn tới trang chi tiết đúng học viên.
- [ ] Admin có thể khóa/tạm ngưng tài khoản từ danh sách hoặc trang chi tiết; học viên sau đó không thể đăng nhập.
- [ ] Trang chi tiết hiển thị danh sách khóa học với tiến độ.
- [ ] Tab "Giao dịch" chỉ hiển thị cho admin (QA bị 403 nếu truy cập).
- [ ] Admin/QA thêm ghi chú được; ghi chú hiển thị ngay.
- [ ] Người dùng không có quyền bị 403.

## 8. Ngoài phạm vi

- Đặt lại mật khẩu (Google only auth).  
- Impersonate user.