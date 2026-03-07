# PRD – Quản lý Chương

## 1. Tên Tính năng  
**Quản lý Chương** (Chapter Management Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Sau khi đã tạo ra thông tin cơ bản của khóa học, đội ngũ quản trị cần công cụ để cấu trúc nội dung bên trong thành các phần học logic (chương). Họ phải có khả năng tạo, sắp xếp các chương này để tổ chức nội dung một cách khoa học và dễ theo dõi. Một khóa học có thể có nhiều chương, hoặc chỉ có một chương duy nhất (trong trường hợp khóa học đơn giản không cần phân chia).

- **Giải pháp:**  
  Xây dựng một giao diện quản lý dành riêng cho các chương, được truy cập từ một khóa học cụ thể. Giao diện này sẽ cho phép thực hiện đầy đủ các thao tác (Tạo, Xem, Sửa, Xóa) với chương, hỗ trợ sắp xếp bằng kéo-thả, và có cơ chế xóa an toàn để bảo vệ các bài học bên trong.

- **Ảnh hưởng dự kiến:**  
  - Cung cấp một công cụ trực quan để quản trị viên có thể phân chia nội dung khóa học thành các chương có cấu trúc.
  - Đảm bảo luồng tạo nội dung diễn ra liền mạch: từ Khóa học → Chương → Bài học.
  - Hỗ trợ cả khóa học có nhiều chương lẫn khóa học đơn giản (chỉ 1 chương, hệ thống người dùng sẽ ẩn tên chương).

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý toàn bộ hệ thống, có quyền tạo, sửa, xóa chương và sắp xếp thứ tự.
- **QA (Chất lượng/Kiểm định)** – người kiểm tra chất lượng nội dung, cần xem và kiểm tra thông tin chương để giám sát cấu trúc nội dung.

## 5. User Stories

### Điều hướng và Truy cập
1. Với tư cách **admin**, tôi muốn nhấn nút "Quản lý Chương" từ danh sách khóa học để vào trang quản lý chương của khóa học đó.
2. Với tư cách **admin/QA**, tôi muốn thấy breadcrumb navigation để biết mình đang ở đâu và có thể quay lại dễ dàng.

### Quản lý Danh sách Chương
3. Với tư cách **admin/QA**, tôi muốn xem tất cả các chương của một khóa học trong một bảng tổng quan để dễ dàng theo dõi và quản lý.
4. Với tư cách **admin/QA**, tôi muốn kéo-thả các chương để thay đổi thứ tự hiển thị mà không cần can thiệp kỹ thuật.
5. Với tư cách **admin**, tôi muốn nhấn nút "Thêm Chương" để tạo một chương mới một cách nhanh chóng.

### Tạo và Chỉnh sửa Chương
6. Với tư cách **admin/QA**, tôi muốn điền thông tin chương (tên) trong một form rõ ràng.
7. Với tư cách **admin**, tôi muốn sửa thông tin chương đã tạo để cập nhật nội dung.

### Quản lý Bài học
8. Với tư cách **admin/QA**, tôi muốn nhấn "Quản lý Bài học" để đi vào trang quản lý bài học của chương đó.

### Xóa Chương
9. Với tư cách **admin**, tôi muốn xóa chương rỗng (không có bài học) để dọn dẹp hệ thống.
10. Với tư cách **admin**, tôi muốn thấy nút Xóa bị vô hiệu hóa khi chương có chứa bài học để tránh xóa nhầm dữ liệu quan trọng.
11. Với tư cách **admin**, tôi muốn thấy tooltip giải thích khi di chuột qua nút Xóa bị vô hiệu hóa để hiểu lý do không thể xóa.

## 6. Yêu cầu

### Chức năng

- **Điểm truy cập và Điều hướng**
  - Người dùng truy cập trang này bằng cách nhấn nút `[Quản lý Chương]` từ trang danh sách Khóa học.
  - **Breadcrumb Navigation:** Luôn hiển thị để người dùng biết vị trí hiện tại.
    - Ví dụ: `Quản lý Khóa học > [Tên khóa học] > Quản lý Chương`
    - Có thể click vào từng cấp để quay lại.

- **Trang Danh sách Chương**
  - Hiển thị dưới dạng bảng (table) với các cột:
    - **Handle (⠿):** Icon kéo-thả (drag handle) - biểu tượng 6 chấm `⠿` để nhấn giữ và kéo lên/xuống sắp xếp thứ tự.
    - **Tên chương:** Hiển thị tên của chương.
    - **Số bài học:** Số lượng bài học trong chương. Cột này quan trọng cho logic xóa an toàn.
    - **Hành động:** Các nút `[Sửa]`, `[Quản lý Bài học]`, `[Xóa]` (QA không thấy nút Xóa).
  - Nút `[+ Thêm Chương]` nổi bật ở góc trên cùng bên phải.
  - **Chức năng Kéo-thả (Drag-and-Drop):**
    - Nhấn giữ icon handle (⠿) và kéo chương lên/xuống để thay đổi thứ tự.
    - Tự động lưu thứ tự mới sau khi thả chuột (không cần nút Lưu riêng).
    - Thứ tự này quyết định vị trí hiển thị chương trong khóa học ở phía người dùng.

- **Form Tạo/Chỉnh sửa Chương**
  - **Tên Chương:** (Text input, Bắt buộc)
  - **Lưu ý nghiệp vụ:** Để tạo một khóa học không có chương (chỉ có danh sách bài học), chỉ cần tạo **một chương duy nhất**. Hệ thống phía người dùng sẽ tự động ẩn tên chương này.
  - **Nút hành động:**
    - `[Lưu]` - Lưu và quay lại trang Danh sách
    - `[Hủy]` - Hủy bỏ và quay lại trang Danh sách

- **Hành động trên Chương**
  - **Sửa:** Mở form Chỉnh sửa với thông tin đã điền sẵn.
  - **Quản lý Bài học:** Điều hướng đến trang "Quản lý Bài học" của chương này (module riêng).
  - **Xóa:**
    - **Nếu chương CÓ bài học:**
      - Nút `[Xóa]` ở trạng thái **disabled** (màu xám, không thể click).
      - Hiển thị tooltip khi hover: "Không thể xóa. Vui lòng xóa hết các bài học bên trong trước."
    - **Nếu chương RỖNG (không có bài học):**
      - Nút `[Xóa]` ở trạng thái **enabled**.
      - Khi click, hiển thị modal xác nhận: "Bạn có chắc chắn muốn xóa chương [Tên chương]? Hành động này không thể hoàn tác."
      - Nếu xác nhận, xóa chương vĩnh viễn.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập module này.
  - **Admin:** Có toàn quyền Tạo, Xem, Sửa, Xóa chương và sắp xếp thứ tự.
  - **QA:** Có quyền Xem, Sửa thông tin chương (tên) và sắp xếp thứ tự chương. Không có quyền Xóa chương.

### Phi chức năng

- Trang danh sách phải tải < 300 ms với 50 chương.
- Chức năng drag-and-drop phải mượt mà, không lag (< 16ms/frame).
- Mọi hành động thay đổi dữ liệu (tạo, sửa, xóa, sắp xếp) đều được log.
- Tuân thủ các yêu cầu phi chức năng chung trong Global UI Components PRD (WCAG AA, browser support, responsive).

## 7. Tiêu chí chấp nhận

### Điều hướng và Breadcrumb
- **Given** admin/QA nhấn `[Quản lý Chương]` từ một khóa học  
  **When** trang tải  
  **Then** hiển thị trang Quản lý Chương của khóa học đó với breadcrumb đầy đủ

- **Given** admin/QA xem breadcrumb  
  **When** kiểm tra  
  **Then** thấy đường dẫn dạng `Quản lý Khóa học > [Tên khóa học] > Quản lý Chương`

- **Given** admin/QA nhấn vào `Quản lý Khóa học` trong breadcrumb  
  **When** click  
  **Then** quay lại trang danh sách Khóa học

### Danh sách Chương
- **Given** admin truy cập trang Quản lý Chương  
  **When** trang tải  
  **Then** hiển thị bảng danh sách tất cả chương với đầy đủ thông tin: handle, tên, số bài học, các nút hành động

- **Given** admin nhìn thấy danh sách chương  
  **When** kiểm tra các cột  
  **Then** thấy icon handle (⠿), tên chương, số bài học và các nút hành động

- **Given** QA nhìn thấy danh sách chương  
  **When** kiểm tra các cột  
  **Then** thấy icon handle (⠿), tên chương, số bài học và nút Sửa, Quản lý Bài học (không có nút Xóa)

- **Given** có nhiều chương trong danh sách  
  **When** admin/QA nhấn giữ icon handle và kéo một chương  
  **Then** chương di chuyển theo con trỏ chuột

- **Given** admin/QA kéo chương đến vị trí mới  
  **When** thả chuột  
  **Then** chương được đặt ở vị trí mới và thứ tự được lưu tự động

- **Given** admin/QA sắp xếp lại chương  
  **When** reload lại trang  
  **Then** thứ tự mới vẫn được giữ nguyên

### Tạo Chương mới
- **Given** admin nhấn nút `[+ Thêm Chương]`  
  **When** form mở ra  
  **Then** hiển thị form trống với trường Tên chương

- **Given** admin điền đầy đủ thông tin bắt buộc (Tên)  
  **When** nhấn `[Lưu]`  
  **Then** chương mới được tạo và hiển thị trong danh sách

- **Given** admin chưa điền tên chương  
  **When** nhấn `[Lưu]`  
  **Then** hiển thị thông báo lỗi validation "Tên chương là bắt buộc"

### Chỉnh sửa Chương
- **Given** admin nhấn nút `[Sửa]` ở một chương  
  **When** form mở ra  
  **Then** tên chương đã được điền sẵn

- **Given** admin thay đổi thông tin và nhấn `[Lưu]`  
  **When** lưu thành công  
  **Then** thông tin cập nhật hiển thị trong danh sách và có toast "Cập nhật thành công!"

- **Given** admin nhấn `[Hủy]` trong form  
  **When** hủy  
  **Then** không lưu thay đổi và quay lại danh sách

### Xóa Chương
- **Given** chương có ít nhất 1 bài học  
  **When** admin xem nút `[Xóa]`  
  **Then** nút bị disabled (màu xám, không click được)

- **Given** admin hover chuột vào nút `[Xóa]` bị disabled  
  **When** hover  
  **Then** hiển thị tooltip "Không thể xóa. Vui lòng xóa hết các bài học bên trong trước."

- **Given** chương rỗng (không có bài học)  
  **When** admin xem nút `[Xóa]`  
  **Then** nút ở trạng thái enabled (có thể click)

- **Given** admin nhấn `[Xóa]` trên chương rỗng  
  **When** click  
  **Then** hiển thị modal xác nhận với tên chương

- **Given** admin xác nhận xóa trong modal  
  **When** xác nhận  
  **Then** chương bị xóa khỏi danh sách và hiển thị toast "Đã xóa chương thành công"

- **Given** admin hủy xóa trong modal  
  **When** hủy  
  **Then** modal đóng, chương vẫn còn trong danh sách

### Quản lý Bài học
- **Given** admin/QA nhấn nút `[Quản lý Bài học]`  
  **When** click  
  **Then** điều hướng đến trang "Quản lý Bài học" của chương đó

### Phân quyền
- **Given** người dùng không phải admin/QA cố gắng truy cập module Quản lý Chương  
  **When** truy cập  
  **Then** hệ thống trả về lỗi 403 hoặc chuyển về trang khác

- **Given** Admin truy cập  
  **When** truy cập  
  **Then** hiển thị trang Quản lý Chương với đầy đủ chức năng (nút Xóa)

- **Given** QA truy cập  
  **When** truy cập  
  **Then** hiển thị trang Quản lý Chương nhưng không có nút Xóa (chỉ có nút Sửa và Quản lý Bài học)

## 8. Ngoài phạm vi

- Quản lý Bài học (thuộc PRD riêng).
- Quản lý Khóa học (thuộc PRD "Quản lý Khóa học").
- Tính năng nhân bản (duplicate) chương.
- Export/Import dữ liệu chương.
