# PRD – Quản lý Bài học

## 1. Tên Tính năng  
**Quản lý Bài học** (Lesson Management Module)

## 2. Epic  
**Admin Operations**

## 3. Mục tiêu

- **Vấn đề:**  
  Sau khi đã cấu trúc khóa học bằng các chương, đội ngũ quản trị cần một công cụ chi tiết để đưa nội dung thực tế vào từng chương. Nội dung này rất đa dạng, bao gồm video bài giảng, bài viết lý thuyết, bài trắc nghiệm kiểm tra và bài tập thực hành code. Cần một giao diện đủ linh hoạt để xử lý tất cả các loại hình nội dung này.

- **Giải pháp:**  
  Xây dựng một trang quản lý bài học chuyên biệt, được truy cập từ một chương cụ thể. Trang này sẽ có một form "thông minh" có khả năng thay đổi các trường nhập liệu dựa trên loại bài học được chọn, cho phép quản trị viên tạo và sắp xếp mọi loại nội dung một cách trực quan và chính xác.

- **Ảnh hưởng dự kiến:**  
  - Cho phép đội ngũ tạo/chỉnh sửa tất cả các loại bài học một cách nhất quán.
  - Đảm bảo dữ liệu nhập vào (video, câu hỏi quiz, code exercise...) được lưu trữ chính xác.
  - Hoàn thiện luồng tạo nội dung từ cấp cao nhất (Khóa học) đến cấp chi tiết nhất (Bài học).

## 4. Personas người dùng

- **Quản trị hệ thống (System Administrator / Admin)** – người quản lý toàn bộ hệ thống, có quyền tạo, sửa, xóa bài học và sắp xếp thứ tự.
- **QA (Chất lượng/Kiểm định)** – người kiểm tra chất lượng nội dung, cần xem và kiểm tra thông tin bài học để giám sát chất lượng.

## 5. User Stories

### Điều hướng và Truy cập
1. Với tư cách **admin**, tôi muốn nhấn nút "Quản lý Bài học" từ danh sách chương để vào trang quản lý bài học của chương đó.
2. Với tư cách **admin/QA**, tôi muốn thấy breadcrumb navigation để biết mình đang ở đâu và có thể quay lại dễ dàng.

### Quản lý Danh sách Bài học
3. Với tư cách **admin/QA**, tôi muốn xem tất cả các bài học của một chương trong một bảng tổng quan để dễ dàng theo dõi và quản lý.
4. Với tư cách **admin/QA**, tôi muốn kéo-thả các bài học để thay đổi thứ tự hiển thị mà không cần can thiệp kỹ thuật.
5. Với tư cách **admin**, tôi muốn nhấn nút "Thêm Bài học" để tạo một bài học mới một cách nhanh chóng.

### Tạo và Chỉnh sửa Bài học
6. Với tư cách **admin/QA**, tôi muốn chọn loại bài học (Video, Bài viết, Quiz, Exercise) để form tự động hiển thị đúng trường nhập liệu.
7. Với tư cách **admin/QA**, tôi muốn nhập URL YouTube và upload tài liệu đính kèm cho bài học Video.
8. Với tư cách **admin/QA**, tôi muốn soạn thảo bài viết với Rich Text Editor hỗ trợ code syntax highlighting.
9. Với tư cách **admin/QA**, tôi muốn tạo và quản lý câu hỏi trắc nghiệm cho Quiz.
10. Với tư cách **admin/QA**, tôi muốn tạo và quản lý nhiều bài tập coding trong một lesson Exercise để chia nhỏ bài tập phức tạp thành các bước thực hành nhỏ hơn.
11. Với tư cách **admin**, tôi muốn sửa thông tin bài học đã tạo để cập nhật nội dung.

### Xóa Bài học
12. Với tư cách **admin**, tôi muốn xóa bài học để dọn dẹp nội dung không cần thiết.

## 6. Yêu cầu

### Chức năng

- **Điểm truy cập và Điều hướng**
  - Người dùng truy cập trang này bằng cách nhấn nút `[Quản lý Bài học]` từ trang danh sách Chương.
  - **Breadcrumb Navigation:** Luôn hiển thị để người dùng biết vị trí hiện tại.
    - Ví dụ: `Quản lý Khóa học > [Tên khóa học] > Quản lý Chương > [Tên chương] > Quản lý Bài học`
    - Có thể click vào từng cấp để quay lại.

- **Trang Danh sách Bài học**
  - Hiển thị dưới dạng bảng (table) với các cột:
    - **Handle (⠿):** Icon kéo-thả (drag handle) - biểu tượng 6 chấm `⠿` để nhấn giữ và kéo lên/xuống sắp xếp thứ tự.
    - **Tên bài học:** Hiển thị tên của bài học.
    - **Loại bài học:** Hiển thị loại với icon nhận dạng nhanh:
      - 📹 Video
      - 📄 Bài viết
      - ❓ Quiz
      - 💻 Exercise
    - **Hành động:** Các nút `[Sửa]`, `[Xóa]` (QA không thấy nút Xóa).
  - Nút `[+ Thêm Bài học]` nổi bật ở góc trên cùng bên phải.
  - **Chức năng Kéo-thả (Drag-and-Drop):**
    - Nhấn giữ icon handle (⠿) và kéo bài học lên/xuống để thay đổi thứ tự.
    - Tự động lưu thứ tự mới sau khi thả chuột (không cần nút Lưu riêng).
    - Thứ tự này quyết định vị trí hiển thị bài học trong chương ở phía người dùng.

- **Form Tạo/Chỉnh sửa Bài học (Form Động)**
  
  **Các trường chung (Luôn hiển thị):**
  - **Tên Bài học:** (Text input, Bắt buộc)
  - **Loại bài học:** (Dropdown, Bắt buộc) - Lựa chọn trong dropdown này sẽ quyết định các trường nhập liệu nào sẽ xuất hiện bên dưới.
    - `Video`
    - `Bài viết`
    - `Quiz`
    - `Exercise`

  **Các trường riêng theo từng Loại bài học:**

  ### **1. Loại = Video**
  - **Nguồn Video:** (Text input URL, Bắt buộc)
    - Chỉ hỗ trợ URL từ YouTube
    - Tự động embed và hiển thị preview video sau khi nhập URL hợp lệ
    - Validation: Phải là URL YouTube hợp lệ (ví dụ: https://www.youtube.com/watch?v=..., https://youtu.be/...)
  - **Tài liệu đính kèm:** (Multiple File Upload, Tùy chọn)
    - Cho phép tải lên nhiều file (PDF, ZIP, source code...)
    - Định dạng: PDF, ZIP, RAR, TXT, MD
    - Giới hạn mỗi file: < 50MB
    - Hiển thị danh sách file đã upload với nút xóa từng file

  ### **2. Loại = Bài viết**
  - **Nội dung bài viết:** (Rich Text Editor, Bắt buộc)
    - **Yêu cầu quan trọng đối với Rich Text Editor:** Trình soạn thảo này phải hỗ trợ đầy đủ các tính năng:
      - Định dạng cơ bản: **In đậm**, *In nghiêng*, Gạch chân, ~~Gạch ngang~~
      - Danh sách: Bullet list, Numbered list
      - Tiêu đề: H1, H2, H3, H4
      - Chèn hình ảnh (upload hoặc URL)
      - Chèn đường link
      - Chèn bảng (table)
      - **Quan trọng nhất:** Chức năng chèn **Khối Mã nguồn (Code Block)** với:
        - Syntax highlighting cho các ngôn ngữ: JavaScript, Python, Java, C++, HTML, CSS, SQL, PHP, Ruby, Go
        - Hiển thị số dòng
        - Nút copy code

  ### **3. Loại = Quiz**
  - **Khu vực Quản lý Câu hỏi:**
    - Hiển thị danh sách câu hỏi đã tạo
    - Mỗi câu hỏi có 2 trạng thái: **View Mode** (xem) và **Edit Mode** (sửa)
    
  - **Luồng Thêm câu hỏi mới:**
    - Nút `[+ Thêm câu hỏi]` ở cuối danh sách
    - Khi nhấn, hiển thị form mới ở **Edit Mode** với các trường:
      - **Nội dung câu hỏi:** (Rich Text Area, Bắt buộc)
        - Hỗ trợ định dạng text cơ bản và chèn code block với syntax highlighting
        - Cần thiết vì câu hỏi có thể chứa code snippet (ví dụ: "Đoạn code sau in ra kết quả gì?")
      - **Loại câu trả lời:** (Radio Buttons)
        - ◎ Một đáp án đúng (Single choice)
        - ◎ Nhiều đáp án đúng (Multiple choice)
      - **Danh sách lựa chọn trả lời:**
        - Mỗi dòng có: Checkbox/Radio (đánh dấu đáp án đúng), Rich Text Area (nội dung), nút `[Xóa]`
        - Rich Text Area cho mỗi lựa chọn hỗ trợ định dạng và code block (vì đáp án có thể là code)
        - Nút `[+ Thêm lựa chọn]` để thêm đáp án mới
        - Tối thiểu 2 lựa chọn, tối đa 10 lựa chọn
      - Nút `[Lưu câu hỏi]` và `[Hủy]` ở cuối form
    - **Khi nhấn `[Lưu câu hỏi]`:**
      - Validate: Phải có ít nhất 1 đáp án được đánh dấu đúng
      - Gửi dữ liệu lên server
      - Sau khi lưu thành công, chuyển sang **View Mode**
    - **Khi nhấn `[Hủy]`:** Xóa form khỏi giao diện

  - **Luồng Xem và Sửa câu hỏi đã có:**
    - **View Mode:** Hiển thị câu hỏi và đáp án (đánh dấu đáp án đúng bằng ✓), có nút `[Sửa]` và `[Xóa]`
    - **Khi nhấn `[Sửa]`:** Chuyển sang Edit Mode với dữ liệu đã điền sẵn
    - **Khi nhấn `[Xóa]`:** Hiển thị modal xác nhận "Bạn có chắc chắn muốn xóa câu hỏi này?"
  
  - **Chức năng Sắp xếp:**
    - Mỗi câu hỏi có icon handle (⠿) để kéo-thả
    - Sau khi thả, tự động lưu thứ tự mới

  ### **4. Loại = Exercise**
  - **Khu vực Quản lý Bài tập:**
    - Hiển thị danh sách các bài tập thực hành đã tạo
    - Mỗi bài tập có 2 trạng thái: **View Mode** (xem) và **Edit Mode** (sửa)
    
  - **Luồng Thêm bài tập mới:**
    - Nút `[+ Thêm bài tập]` ở cuối danh sách
    - Khi nhấn, hiển thị form mới ở **Edit Mode** với các trường:
      - **Tên bài tập:** (Text input, Bắt buộc)
        - Ví dụ: "Bài tập 1: Khởi tạo mảng", "Bài tập 2: Lọc phần tử"
      - **Nội dung đề bài:** (Rich Text Editor, Bắt buộc)
        - Hỗ trợ đầy đủ tính năng như Rich Text Editor của Bài viết (có thể chèn code block với syntax highlighting)
        - Admin viết đề bài, yêu cầu, starter code (nếu có), ghi chú/hướng dẫn
      - **Đáp án tham khảo:** (Rich Text Editor, Bắt buộc)
        - Hỗ trợ đầy đủ tính năng như Rich Text Editor của Bài viết
        - Admin viết code đáp án mẫu và giải thích cách làm
      - **Tài liệu đính kèm:** (Multiple File Upload, Tùy chọn)
        - Cho phép tải lên nhiều file (source code, test cases, tài liệu hướng dẫn...)
        - Định dạng: ZIP, RAR, PDF, MD
        - Giới hạn mỗi file: < 50MB
        - Hiển thị danh sách file đã upload với nút xóa từng file
      - Nút `[Lưu bài tập]` và `[Hủy]` ở cuối form
    - **Khi nhấn `[Lưu bài tập]`:**
      - Validate: Tất cả trường bắt buộc phải được điền
      - Gửi dữ liệu lên server
      - Sau khi lưu thành công, chuyển sang **View Mode**
    - **Khi nhấn `[Hủy]`:** Xóa form khỏi giao diện

  - **Luồng Xem và Sửa bài tập đã có:**
    - **View Mode:** Hiển thị tên bài tập, một phần nội dung đề bài (truncate), có nút `[Sửa]` và `[Xóa]`
    - **Khi nhấn `[Sửa]`:** Chuyển sang Edit Mode với dữ liệu đã điền sẵn
    - **Khi nhấn `[Xóa]`:** Hiển thị modal xác nhận "Bạn có chắc chắn muốn xóa bài tập này?"
  
  - **Chức năng Sắp xếp:**
    - Mỗi bài tập có icon handle (⠿) để kéo-thả
    - Sau khi thả, tự động lưu thứ tự mới

  **Nút hành động của Form:**
  - `[Lưu]` - Lưu và quay lại trang Danh sách
  - `[Hủy]` - Hủy bỏ và quay lại trang Danh sách

- **Hành động trên Bài học**
  - **Sửa:** Mở form Chỉnh sửa với loại bài học đã được chọn và thông tin đã điền sẵn.
  - **Xóa:**
    - Khi click, hiển thị modal xác nhận: "Bạn có chắc chắn muốn xóa bài học [Tên bài học]? Hành động này không thể hoàn tác."
    - Nếu xác nhận, xóa bài học vĩnh viễn.
    - Lưu ý: Bài học là đơn vị nội dung nhỏ nhất, việc xóa không cần kiểm tra điều kiện phức tạp.

- **Phân quyền**
  - Chỉ các vai trò `admin` và `qa` được truy cập module này.
  - **Admin:** Có toàn quyền Tạo, Xem, Sửa, Xóa bài học và sắp xếp thứ tự.
  - **QA:** Có quyền Xem, Sửa thông tin bài học và sắp xếp thứ tự bài học. Không có quyền Xóa bài học.

### Phi chức năng

- Trang danh sách phải tải < 200 ms với 100 bài học.

- Chức năng drag-and-drop phải mượt mà, không lag (< 16ms/frame).
- Rich Text Editor phải tương thích với các trình duyệt chính (Chrome, Firefox, Safari, Edge).
- Code Editor phải hỗ trợ syntax highlighting real-time.
- Tuân thủ các yêu cầu phi chức năng chung trong Global UI Components PRD (WCAG AA, browser support, responsive).

## 7. Tiêu chí chấp nhận

### Điều hướng và Breadcrumb
- **Given** admin/QA nhấn `[Quản lý Bài học]` từ một chương  
  **When** trang tải  
  **Then** hiển thị trang Quản lý Bài học của chương đó với breadcrumb đầy đủ

- **Given** admin/QA xem breadcrumb  
  **When** kiểm tra  
  **Then** thấy đường dẫn dạng `Quản lý Khóa học > [Tên khóa học] > Quản lý Chương > [Tên chương] > Quản lý Bài học`

- **Given** admin/QA nhấn vào `Quản lý Chương` trong breadcrumb  
  **When** click  
  **Then** quay lại trang danh sách Chương

### Danh sách Bài học
- **Given** admin truy cập trang Quản lý Bài học  
  **When** trang tải  
  **Then** hiển thị bảng danh sách tất cả bài học với đầy đủ thông tin: handle, tên, loại (với icon), các nút hành động

- **Given** admin nhìn thấy danh sách bài học  
  **When** kiểm tra các cột  
  **Then** thấy icon handle (⠿), tên bài học, loại bài học (với icon) và các nút hành động

- **Given** QA nhìn thấy danh sách bài học  
  **When** kiểm tra các cột  
  **Then** thấy icon handle (⠿), tên bài học, loại bài học và nút Sửa (không có nút Xóa)

- **Given** có nhiều bài học trong danh sách  
  **When** admin/QA nhấn giữ icon handle và kéo một bài học  
  **Then** bài học di chuyển theo con trỏ chuột

- **Given** admin/QA kéo bài học đến vị trí mới  
  **When** thả chuột  
  **Then** bài học được đặt ở vị trí mới và thứ tự được lưu tự động

- **Given** admin/QA sắp xếp lại bài học  
  **When** reload lại trang  
  **Then** thứ tự mới vẫn được giữ nguyên

### Tạo Bài học - Video
- **Given** admin nhấn nút `[+ Thêm Bài học]`  
  **When** form mở ra  
  **Then** hiển thị form với trường Tên và dropdown Loại bài học

- **Given** admin chọn loại `Video`  
  **When** chọn xong  
  **Then** form tự động hiển thị thêm trường nhập URL YouTube và Tài liệu đính kèm

- **Given** admin điền tên và nhập URL YouTube hợp lệ  
  **When** nhấn `[Lưu]`  
  **Then** bài học Video được tạo và hiển thị trong danh sách với icon 📹

- **Given** admin nhập URL không phải YouTube  
  **When** nhập xong  
  **Then** hiển thị lỗi "Vui lòng nhập URL YouTube hợp lệ"

- **Given** admin nhập URL YouTube hợp lệ  
  **When** nhập xong  
  **Then** hiển thị preview video embed

### Tạo Bài học - Bài viết
- **Given** admin chọn loại `Bài viết`  
  **When** chọn xong  
  **Then** form hiển thị Rich Text Editor

- **Given** admin soạn nội dung bài viết  
  **When** sử dụng Rich Text Editor  
  **Then** có thể định dạng text, chèn ảnh, link, và code block với syntax highlighting

- **Given** admin chèn code block JavaScript  
  **When** nhập code  
  **Then** code được hiển thị với syntax highlighting đúng ngôn ngữ

### Tạo Bài học - Quiz
- **Given** admin chọn loại `Quiz`  
  **When** chọn xong  
  **Then** form hiển thị khu vực quản lý câu hỏi với nút `[+ Thêm câu hỏi]`

- **Given** admin nhấn `[+ Thêm câu hỏi]`  
  **When** click  
  **Then** hiển thị form câu hỏi mới ở Edit Mode

- **Given** admin điền câu hỏi và thêm 2 lựa chọn, đánh dấu 1 đáp án đúng  
  **When** nhấn `[Lưu câu hỏi]`  
  **Then** câu hỏi chuyển sang View Mode và hiển thị trong danh sách

- **Given** admin thêm câu hỏi nhưng không đánh dấu đáp án đúng  
  **When** nhấn `[Lưu câu hỏi]`  
  **Then** hiển thị lỗi "Phải có ít nhất 1 đáp án đúng"

- **Given** câu hỏi đã lưu ở View Mode  
  **When** admin nhấn `[Sửa]`  
  **Then** câu hỏi chuyển sang Edit Mode với dữ liệu đã điền sẵn

- **Given** câu hỏi đã lưu  
  **When** admin nhấn `[Xóa]`  
  **Then** hiển thị modal xác nhận xóa câu hỏi

- **Given** admin kéo-thả câu hỏi trong Quiz  
  **When** thả chuột  
  **Then** thứ tự câu hỏi được lưu tự động

### Tạo Bài học - Exercise
- **Given** admin chọn loại `Exercise`  
  **When** chọn xong  
  **Then** form hiển thị khu vực quản lý bài tập với nút `[+ Thêm bài tập]`

- **Given** admin nhấn `[+ Thêm bài tập]`  
  **When** click  
  **Then** hiển thị form bài tập mới ở Edit Mode với các trường: Tên bài tập, Nội dung đề bài (RTE), Đáp án tham khảo (RTE), Tài liệu đính kèm

- **Given** admin điền tên bài tập, nội dung đề bài và đáp án tham khảo  
  **When** nhấn `[Lưu bài tập]`  
  **Then** bài tập chuyển sang View Mode và hiển thị trong danh sách

- **Given** admin thêm bài tập nhưng không điền đáp án tham khảo  
  **When** nhấn `[Lưu bài tập]`  
  **Then** hiển thị lỗi "Đáp án tham khảo là bắt buộc"

- **Given** bài tập đã lưu ở View Mode  
  **When** admin nhấn `[Sửa]`  
  **Then** bài tập chuyển sang Edit Mode với dữ liệu đã điền sẵn

- **Given** bài tập đã lưu  
  **When** admin nhấn `[Xóa]`  
  **Then** hiển thị modal xác nhận xóa bài tập

- **Given** admin kéo-thả bài tập trong Exercise  
  **When** thả chuột  
  **Then** thứ tự bài tập được lưu tự động

- **Given** admin soạn nội dung đề bài với code block  
  **When** sử dụng Rich Text Editor  
  **Then** code được hiển thị với syntax highlighting đúng ngôn ngữ đã chọn trong code block

- **Given** admin upload file ZIP chứa test cases  
  **When** upload thành công  
  **Then** file hiển thị trong danh sách file đính kèm của bài tập đó với nút xóa

- **Given** admin đã tạo lesson Exercise với 3 bài tập  
  **When** nhấn `[Lưu]` ở form lesson  
  **Then** bài học Exercise được tạo với icon 💻 và chứa 3 bài tập thực hành

### Chỉnh sửa Bài học
- **Given** admin nhấn `[Sửa]` ở một bài học Video  
  **When** form mở ra  
  **Then** loại bài học auto-select là Video, URL YouTube và file đã upload hiển thị

- **Given** admin sửa thông tin và nhấn `[Lưu]`  
  **When** lưu thành công  
  **Then** thông tin cập nhật hiển thị trong danh sách và có toast "Cập nhật thành công!"

### Xóa Bài học
- **Given** admin nhấn `[Xóa]` trên một bài học  
  **When** click  
  **Then** hiển thị modal xác nhận với tên bài học

- **Given** admin xác nhận xóa  
  **When** xác nhận  
  **Then** bài học bị xóa khỏi danh sách và hiển thị toast "Đã xóa bài học thành công"

- **Given** admin hủy xóa  
  **When** hủy  
  **Then** modal đóng, bài học vẫn còn trong danh sách

### Phân quyền
- **Given** người dùng không phải admin/QA cố gắng truy cập module Quản lý Bài học  
  **When** truy cập  
  **Then** hệ thống trả về lỗi 403 hoặc chuyển về trang khác

- **Given** Admin truy cập  
  **When** truy cập  
  **Then** hiển thị trang Quản lý Bài học với đầy đủ chức năng (nút Xóa)

- **Given** QA truy cập  
  **When** truy cập  
  **Then** hiển thị trang Quản lý Bài học nhưng không có nút Xóa (chỉ có nút Sửa)

## 8. Ngoài phạm vi

- Quản lý Chương (thuộc PRD "Quản lý Chương").
- Quản lý Khóa học (thuộc PRD "Quản lý Khóa học").
- Xem trước nội dung (Admin Preview) - Chức năng cho phép admin xem trước bài học sẽ hiển thị với học viên như thế nào.
- Ngân hàng câu hỏi (Question Bank) - Kho câu hỏi tái sử dụng cho nhiều quiz.
- Tính năng nhân bản (duplicate) bài học.
- Import/Export bài học.
- Auto-grading cho Exercise (chấm tự động bằng test cases).
