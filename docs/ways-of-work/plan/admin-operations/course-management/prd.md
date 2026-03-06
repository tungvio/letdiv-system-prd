# PRD – Quản lý Khóa học video

## 1. Tên Tính năng  
**Quản lý Khóa học video** (Video Course Management Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Để nền tảng có sản phẩm để bán, đội ngũ quản trị cần một công cụ chuyên biệt để tạo ra các "vỏ" khóa học. Họ cần định nghĩa các thông tin cốt lõi như tên, mô tả, hình ảnh, giảng viên, giá bán, và quan trọng nhất là phải kiểm soát được thứ tự xuất hiện của các khóa học này trên trang web để phục vụ cho các chiến dịch marketing.

- **Giải pháp:**  
  Xây dựng một giao diện quản trị dành riêng cho Khóa học, bao gồm một danh sách tổng quan hỗ trợ sắp xếp bằng kéo-thả và một form nhập liệu chi tiết. Giao diện này sẽ là điểm khởi đầu, là cấp quản lý cao nhất, từ đó mới có thể đi sâu vào quản lý nội dung bên trong (chương và bài học).

- **Ảnh hưởng dự kiến:**  
  - Cung cấp một công cụ độc lập, dễ sử dụng để tạo và cấu hình các khóa học mới.
  - Trao quyền cho đội ngũ kinh doanh/marketing chủ động sắp xếp, làm nổi bật các khóa học chiến lược mà không cần sự can thiệp của kỹ thuật.
  - Tạo ra một luồng quản trị có cấu trúc, nơi việc quản lý Khóa học là bước đầu tiên và tiên quyết trước khi thêm nội dung chi tiết.

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý toàn bộ hệ thống, có quyền tạo, sửa, xóa khóa học video và sắp xếp thứ tự hiển thị để phục vụ chiến lược kinh doanh.
- **QA (Chất lượng/Kiểm định)** – người kiểm tra chất lượng khóa học, cần xem và kiểm tra thông tin khóa học để giám sát chất lượng nội dung.

## 5. User Stories

### Quản lý Danh sách Khóa học video
1. Với tư cách **admin**, tôi muốn xem tất cả các khóa học video trong một bảng tổng quan để dễ dàng theo dõi và quản lý.
2. Với tư cách **admin**, tôi muốn kéo-thả các khóa học video để thay đổi thứ tự hiển thị trên trang web mà không cần can thiệp kỹ thuật.
3. Với tư cách **admin**, tôi muốn thấy trạng thái của mỗi khóa học video (Công khai/Bản nháp) để biết khóa học nào đang hiển thị cho người dùng.
4. Với tư cách **admin**, tôi muốn nhấn nút "Thêm" để tạo một khóa học video mới một cách nhanh chóng.

### Tạo và Chỉnh sửa Khóa học video
5. Với tư cách **admin/QA**, tôi muốn điền đầy đủ thông tin khóa học video (tên, mô tả, ảnh bìa, giảng viên, giá) trong một form rõ ràng.
6. Với tư cách **admin/QA**, tôi muốn upload ảnh bìa (thumbnail) bắt buộc để phục vụ SEO và hiển thị nhất quán.
7. Với tư cách **admin/QA**, tôi muốn thêm danh sách mục tiêu học tập để người học biết họ sẽ học được gì.
8. Với tư cách **admin/QA**, tôi muốn thêm danh sách yêu cầu tiên quyết để người học chuẩn bị trước khi tham gia.
9. Với tư cách **admin/QA**, tôi muốn chọn trạng thái "Bản nháp" khi khóa học chưa sẵn sàng để nó không hiển thị cho người dùng.
10. Với tư cách **admin**, tôi muốn sửa thông tin khóa học đã tạo để cập nhật nội dung hoặc điều chỉnh giá.

### Quản lý Nội dung
11. Với tư cách **admin**, tôi muốn nhấn "Quản lý Chương" để đi vào trang quản lý chương và bài học của khóa học đó.

### Xóa Khóa học video
12. Với tư cách **admin**, tôi muốn xóa khóa học video rỗng (không có chương) để dọn dẹp hệ thống.
13. Với tư cách **admin**, tôi muốn thấy nút Xóa bị vô hiệu hóa khi khóa học video có chứa chương để tránh xóa nhầm dữ liệu quan trọng.
14. Với tư cách **admin**, tôi muốn thấy tooltip giải thích khi di chuột qua nút Xóa bị vô hiệu hóa để hiểu lý do không thể xóa.

### Thống kê & Báo cáo
15. Với tư cách **admin/QA**, tôi muốn xem số lượng học viên đang học mỗi khóa học để đánh giá mức độ phổ biến.
16. Với tư cách **admin/QA**, tôi muốn nhấn vào chỉ số đánh giá để mở module Review tương ứng theo từng khóa học.

## 6. Yêu cầu

### Chức năng

- **Trang Danh sách Khóa học video**
  - Hiển thị dưới dạng bảng (table) với các cột:
    - **Handle (⠿):** Icon để kéo-thả sắp xếp thứ tự (chỉ Admin thấy).
    - **Tên khóa học:** Hiển thị tên và ảnh bìa thumbnail (dùng cho SEO và preview danh sách).
    - **Giảng viên:** Tên giảng viên phụ trách.
    - **Số học viên:** Số lượng học viên đang học (đã mua). Click vào mở trang Chi tiết Thống kê.
    - **Đánh giá:** Số sao trung bình và tổng review (VD: ⭐ 4.5 (128)). Click vào mở module Review với bộ lọc theo khóa học hiện tại.
    - **Giá:** Giá mua toàn bộ khóa học (VND).
    - **Trạng thái:** Nhãn màu (`Công khai` hoặc `Bản nháp`).
    - **Hành động:** Các nút `[Sửa]`, `[Quản lý Chương]`, `[Xóa]` (QA không thấy nút Xóa).
  - Nút `[+ Thêm]` nổi bật ở góc trên cùng bên phải.
  - **Chức năng Kéo-thả (Drag-and-Drop):**
    - Nhấn giữ icon handle (⠿) và kéo khóa học lên/xuống để thay đổi thứ tự.
    - Tự động lưu thứ tự mới sau khi thả chuột (không cần nút Lưu riêng).
    - Thứ tự này quyết định vị trí hiển thị trên trang chủ và danh sách khóa học của người dùng.

- **Form Tạo/Chỉnh sửa Khóa học video**
  - **Tên Khóa học video:** (Text input, Bắt buộc)
  - **Mô tả ngắn (Subtitle):** (Text input) - Tagline hiển thị dưới tên khóa học.
  - **Mô tả chi tiết:** (Rich Text Editor) - Hỗ trợ định dạng văn bản, chèn ảnh, video.
  - **Ảnh bìa (Thumbnail):** (Bắt buộc)
    - File Upload
    - Định dạng: JPG, PNG, WEBP
    - Giới hạn dung lượng: < 2MB
    - Hiển thị preview sau khi upload
    - Mục đích: dùng cho SEO (Open Graph, Twitter Cards), hiển thị trong danh sách và fallback khi video lỗi
  - **Video giới thiệu:** (Tùy chọn)
    - Text input: URL từ YouTube hoặc Vimeo
    - Tự động embed và hiển thị preview video
    - Nếu có video, video hiển thị ở trang chi tiết khóa học; ảnh bìa vẫn được giữ để SEO/preview
  - **Giảng viên:** (Dropdown) - Chọn một hoặc nhiều giảng viên từ danh sách có sẵn.
  - **Mục tiêu khóa học ("Bạn sẽ học được gì?"):** 
    - List động với nút `[+ Thêm mục tiêu]`
    - Mỗi dòng có nút `[Sửa]` và `[Xóa]`
  - **Yêu cầu của khóa học:** 
    - List động với nút `[+ Thêm yêu cầu]`
    - Mỗi dòng có nút `[Sửa]` và `[Xóa]`
  - **Giá:** (Number input, Bắt buộc) - Số tiền (VND) để mua toàn bộ khóa học.
  - **Trạng thái:** (Dropdown)
    - `Bản nháp` - Không hiển thị cho người dùng
    - `Công khai` - Hiển thị trên toàn trang web
  - **Nút hành động:**
    - `[Lưu]` - Lưu và quay lại trang Danh sách
    - `[Hủy]` - Hủy bỏ và quay lại trang Danh sách

- **Hành động trên Khóa học video**
  - **Sửa:** Mở form Chỉnh sửa với thông tin đã điền sẵn.
  - **Quản lý Chương:** Điều hướng đến trang "Quản lý Chương" của khóa học video (module riêng).
  - **Xóa:**
    - **Nếu khóa học CÓ chương:**
      - Nút `[Xóa]` ở trạng thái **disabled** (màu xám, không thể click).
      - Hiển thị tooltip khi hover: "Không thể xóa. Vui lòng xóa hết các chương bên trong trước."
    - **Nếu khóa học RỖNG (không có chương):**
      - Nút `[Xóa]` ở trạng thái **enabled**.
      - Khi click, hiển thị modal xác nhận: "Bạn có chắc chắn muốn xóa khóa học [Tên khóa học]? Hành động này không thể hoàn tác."
      - Nếu xác nhận, xóa khóa học vĩnh viễn.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập module này.
  - **Admin:** Có toàn quyền Tạo, Xem, Sửa, Xóa khóa học video và sắp xếp thứ tự.
  - **QA:** Có quyền Xem và Sửa thông tin khóa học, xem thống kê số lượng học viên và chỉ số đánh giá. Không có quyền Xóa khóa học và sắp xếp thứ tự.

- **Thống kê & Báo cáo**
  - **Hiển thị trong bảng Danh sách:**
    - Thêm 2 cột thống kê:
      - **Số học viên:** Hiển thị số lượng học viên đang học (đã mua khóa học).
      - **Đánh giá:** Hiển thị số sao trung bình (VD: ⭐ 4.5) và tổng số review trong ngoặc (VD: ⭐ 4.5 (128)); click để điều hướng sang module Review theo đúng khóa học.
  - **Trang Chi tiết Thống kê:**
    - Khi nhấn vào cột **Số học viên** trong bảng, mở trang chi tiết thống kê của khóa học.
    - **Tab Tổng quan:**
      - Số học viên đang học
      - Tỷ lệ hoàn thành khóa học (%)
      - Đánh giá trung bình (số sao)
      - Tổng số review
    - **Tab Học viên:** Danh sách học viên đã mua (tên, email, ngày mua, tiến độ %).
    - Từ các chỉ số đánh giá, có link điều hướng sang module Review (module riêng) với filter theo khóa học.

### Phi chức năng

- Trang danh sách phải tải < 500 ms với 100 khóa học.
- Chức năng drag-and-drop phải mượt mà, không lag (< 16ms/frame).
- Upload ảnh phải có progress bar và validation ngay lập tức.
- Mọi hành động thay đổi dữ liệu (tạo, sửa, xóa, sắp xếp) đều được log.
- Tuân thủ các yêu cầu phi chức năng chung trong Global UI Components PRD (WCAG AA, browser support, responsive).

## 7. Tiêu chí chấp nhận

### Danh sách Khóa học video
- **Given** admin truy cập trang Quản lý Khóa học video  
  **When** trang tải  
  **Then** hiển thị bảng danh sách tất cả khóa học video với đầy đủ thông tin: ảnh, tên, giảng viên, số học viên, đánh giá, giá, trạng thái

- **Given** admin nhìn thấy danh sách khóa học  
  **When** kiểm tra các cột  
  **Then** thấy icon handle (⠿), tên, giảng viên, số học viên, đánh giá, giá, trạng thái và các nút hành động

- **Given** QA nhìn thấy danh sách khóa học  
  **When** kiểm tra các cột  
  **Then** thấy tên, giảng viên, số học viên, đánh giá, giá, trạng thái và nút Sửa, Quản lý Chương (không có handle và nút Xóa)

- **Given** có nhiều khóa học trong danh sách  
  **When** admin nhấn giữ icon handle và kéo một khóa học  
  **Then** khóa học di chuyển theo con trỏ chuột

- **Given** admin kéo khóa học đến vị trí mới  
  **When** thả chuột  
  **Then** khóa học được đặt ở vị trí mới và thứ tự được lưu tự động

- **Given** admin sắp xếp lại khóa học  
  **When** reload lại trang  
  **Then** thứ tự mới vẫn được giữ nguyên

### Tạo Khóa học video mới
- **Given** admin nhấn nút `[+ Thêm]`  
  **When** form mở ra  
  **Then** hiển thị form trống với tất cả các trường cần nhập

- **Given** admin điền đầy đủ thông tin bắt buộc (Tên, Giá, Trạng thái)  
  **When** nhấn `[Lưu]`  
  **Then** khóa học mới được tạo và hiển thị trong danh sách

- **Given** admin chưa điền đủ thông tin bắt buộc  
  **When** nhấn `[Lưu]`  
  **Then** hiển thị thông báo lỗi validation cho các trường thiếu

- **Given** admin upload ảnh bìa > 2MB  
  **When** chọn file  
  **Then** hiển thị thông báo lỗi "Ảnh không được vượt quá 2MB"

- **Given** admin upload ảnh bìa đúng định dạng (< 2MB)  
  **When** file được chọn  
  **Then** hiển thị preview ảnh và progress bar upload

- **Given** admin chưa upload ảnh bìa  
  **When** nhấn `[Lưu]`  
  **Then** hiển thị lỗi "Ảnh bìa là bắt buộc"

- **Given** admin nhập URL YouTube hợp lệ vào trường Video giới thiệu  
  **When** nhập xong  
  **Then** hiển thị preview video embed

- **Given** admin tạo khóa học chỉ có ảnh bìa (không có video)  
  **When** nhấn `[Lưu]`  
  **Then** khóa học được tạo thành công

- **Given** admin tạo khóa học có cả ảnh bìa và video giới thiệu  
  **When** nhấn `[Lưu]`  
  **Then** khóa học được tạo thành công, ảnh bìa dùng cho SEO/danh sách và video hiển thị ở trang chi tiết

### Chỉnh sửa Khóa học video
- **Given** admin nhấn nút `[Sửa]` ở một khóa học video  
  **When** form mở ra  
  **Then** tất cả thông tin của khóa học video đã được điền sẵn

- **Given** admin thay đổi thông tin và nhấn `[Lưu]`  
  **When** lưu thành công  
  **Then** thông tin cập nhật hiển thị trong danh sách và có toast "Cập nhật thành công!"

- **Given** admin nhấn `[Hủy]` trong form  
  **When** hủy  
  **Then** không lưu thay đổi và quay lại danh sách

### Quản lý Mục tiêu và Yêu cầu
- **Given** admin nhấn `[+ Thêm mục tiêu]`  
  **When** thêm  
  **Then** hiển thị thêm một trường input mới trong danh sách

- **Given** admin nhấn `[Xóa]` trên một mục tiêu  
  **When** xóa  
  **Then** mục tiêu đó biến mất khỏi danh sách

### Xóa Khóa học video
- **Given** khóa học video có ít nhất 1 chương  
  **When** admin xem nút `[Xóa]`  
  **Then** nút bị disabled (màu xám, không click được)

- **Given** admin hover chuột vào nút `[Xóa]` bị disabled  
  **When** hover  
  **Then** hiển thị tooltip "Không thể xóa. Vui lòng xóa hết các chương bên trong trước."

- **Given** khóa học video rỗng (không có chương)  
  **When** admin xem nút `[Xóa]`  
  **Then** nút ở trạng thái enabled (có thể click)

- **Given** admin nhấn `[Xóa]` trên khóa học video rỗng  
  **When** click  
  **Then** hiển thị modal xác nhận với tên khóa học video

- **Given** admin xác nhận xóa trong modal  
  **When** xác nhận  
  **Then** khóa học video bị xóa khỏi danh sách và hiển thị toast "Đã xóa khóa học video thành công"

- **Given** admin hủy xóa trong modal  
  **When** hủy  
  **Then** modal đóng, khóa học video vẫn còn trong danh sách

### Quản lý Chương
- **Given** admin nhấn nút `[Quản lý Chương]`  
  **When** click  
  **Then** điều hướng đến trang "Quản lý Chương" của khóa học video đó

### Phân quyền
- **Given** người dùng không phải admin/QA cố gắng truy cập module Quản lý Khóa học video  
  **When** truy cập  
  **Then** hệ thống trả về lỗi 403 hoặc chuyển về trang khác

- **Given** Admin truy cập  
  **When** truy cập  
  **Then** hiển thị trang Quản lý Khóa học video với đầy đủ chức năng (icon handle, nút Xóa)

- **Given** QA truy cập  
  **When** truy cập  
  **Then** hiển thị trang Quản lý Khóa học video nhưng không có icon handle và nút Xóa (chỉ có nút Sửa và Quản lý Chương)

### Thống kê & Báo cáo
- **Given** admin/QA xem bảng danh sách khóa học  
  **When** kiểm tra các cột  
  **Then** thấy cột "Số học viên" và "Đánh giá" hiển thị số liệu của từng khóa học

- **Given** admin/QA nhấn vào số học viên của một khóa học  
  **When** click  
  **Then** mở trang Chi tiết Thống kê với tab "Học viên" được chọn

- **Given** admin/QA xem trang Chi tiết Thống kê  
  **When** chọn tab "Tổng quan"  
  **Then** hiển thị số học viên, tỷ lệ hoàn thành, điểm trung bình, tổng review

- **Given** admin/QA xem tab "Học viên"  
  **When** trang tải  
  **Then** hiển thị danh sách học viên với tên, email, ngày mua, tiến độ %

- **Given** admin/QA nhấn vào chỉ số đánh giá của một khóa học trong danh sách  
  **When** click  
  **Then** hệ thống điều hướng sang module Review và tự động filter theo đúng khóa học đó

- **Given** admin/QA nhấn vào chỉ số đánh giá trong trang Chi tiết Thống kê  
  **When** click  
  **Then** hệ thống điều hướng sang module Review và giữ ngữ cảnh khóa học hiện tại

## 8. Ngoài phạm vi

- Quản lý Chương và Bài học (thuộc PRD riêng).
- Quản lý Giảng viên (thuộc module riêng, module này chỉ sử dụng danh sách có sẵn).
- **Thống kê & Báo cáo Doanh thu** (thuộc module Quản lý Tài chính).
- **Quản lý Review chi tiết và xóa review** (thuộc module Review riêng).
- Quản lý danh mục (category/tag) cho khóa học.
- Tính năng nhân bản (duplicate) khóa học.
- Export/Import dữ liệu khóa học.
- Biểu đồ thống kê nâng cao (xu hướng, dự đoán).
