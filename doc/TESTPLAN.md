# KẾ HOẠCH KIỂM THỬ (TEST PLAN) - GIAI ĐOẠN v0.1
Dự án: Hồ sơ năng lực nhóm sinh viên Sư phạm Tin Học (Nhóm 15)
Người lập: Tester(Ngô Thùy Ngân)

## 1. Chuẩn hóa dữ liệu tĩnh đầu vào
- **Tài nguyên ảnh đại diện:** 4 ảnh chân dung tỉ lệ vuông 1:1, lưu tại thư mục "images".
- **Trích ngang kỹ năng:** Đã chuẩn hóa danh sách kỹ năng chuyên môn và vai trò 4 thành viên để nạp vào "data.js" và "thanh-vien.html".

## 2. Danh mục các trường dữ liệu Form tạo hồ sơ cá nhân (cong-cu.html)
| STT | Tên trường | Thuộc tính ID | Kiểu dữ liệu | Bắt buộc | Tiêu chí hợp lệ |
| :---: | :--- | :--- | :---: | :---: | :--- |
| 1 | Họ và tên | "input-hoten" | Text | Có | Độ dài 2 - 50 ký tự, không chứa số hoặc ký tự lạ |
| 2 | Vị trí / Chức danh | "input-chucdanh" | Text | Có | Độ dài 5 - 50 ký tự (Gợi ý: Sinh viên Sư phạm Tin Học) |
| 3 | Email | "input-email" | Email | Có | Định dạng chuẩn abc@gmail.com |
| 4 | Số điện thoại | "input-sdt" | Tel | Có | 10 số, bắt đầu bằng chữ số 0 |
| 5 | Quê quán / Địa chỉ | "input-diachi" | Text | Không | Cho phép để trống |
| 6 | Mục tiêu nghề nghiệp | "input-muctieu" | Textarea | Có | Đoạn văn ngắn 20 - 200 từ |
| 7 | Kỹ năng nổi bật | "input-kynang" | Textarea | Có | Ngăn cách bằng dấu phẩy |
| 8 | Quá trình học tập | "input-hocvan" | Textarea | Có | Tối thiểu ghi thông tin lớp, ngành, trường |

## 3. Bộ ca kiểm thử (Test Cases) cho giai đoạn nhập liệu Form
### Nhóm 1: Kiểm thử các nút tính năng tương tác
**1 (Nút "Dùng thử"):**
  - Thao tác: Bấm nút "Dùng thử" khi form đang rỗng.
  - Kết quả mong đợi: Toàn bộ 8 trường dữ liệu được tự động điền giá trị mẫu từ "data.js"; khung xem trước cập nhật ngay lập tức; Console không báo lỗi.
**2 (Nút "Đặt lại"):**
  - Thao tác: Bấm nút "Đặt lại" khi form đang có dữ liệu.
  - Kết quả mong đợi: Toàn bộ ô nhập liệu xóa sạch về chuỗi rỗng; khung xem trước trở về trạng thái placeholder ban đầu; Console không báo lỗi.
**3 (Nút "In / Xuất PDF"):**
  - Thao tác: Bấm nút "In hồ sơ".
  - Kết quả mong đợi: Cửa sổ "window.print()" mở ra; CSS "@media print" ẩn menu, chân trang và form nhập liệu; chỉ hiển thị vùng hồ sơ.

### Nhóm 2: Kiểm thử các trường hợp biên & Ràng buộc dữ liệu
**4 (Biên 1 - Bỏ trống trường bắt buộc):**
  - Thao tác: Để trống các trường bắt buộc (Họ tên hoặc Email) và bấm tạo hồ sơ.
  - Kết quả mong đợi: Trình duyệt kích hoạt cảnh báo hợp lệ HTML5/JS (báo đỏ ô trống), không cho phép sinh hồ sơ rỗng.
**5 (Biên 2 - Định dạng Email sai):**
  - Thao tác: Nhập email không chứa ký tự "@" hoặc không có tên miền.
  - Kết quả mong đợi: Hiển thị thông báo yêu cầu nhập đúng định dạng email.
**6 (Biên 3 - Số điện thoại không hợp lệ):**
  - Thao tác: Nhập số điện thoại chứa ký tự chữ cái hoặc độ dài khác 10 số.
  - Kết quả mong đợi: Hệ thống cảnh báo không hợp lệ.
**7 (Biên 4 - Chuỗi văn bản cực dài):**
  - Thao tác: Dán đoạn văn bản hơn 1.000 ký tự vào ô Kỹ năng hoặc Mục tiêu.
  - Kết quả mong đợi: Khung hiển thị hồ sơ tự động xuống dòng, không làm vỡ bố cục giao diện hay tràn viền trang web.

## 4. Kết quả kiểm thử giao diện & Tiêu chuẩn mã (Accessibility & W3C)
- **Điều hướng bằng bàn phím (Keyboard Navigation):**
  - Thực hiện kiểm thử điều hướng bằng phím `Tab` và `Shift + Tab` trên các trang tĩnh (`skills.html`, `index.html`).
  - Toàn bộ các thành phần tương tác (menu Navbar, liên kết chuyển trang, nút bấm) nhận tiêu điểm (`:focus`) tuần tự, hiển thị rõ ràng, không bị bẫy/kẹt phím.
  - Phím `Enter` kích hoạt chính xác các liên kết điều hướng nội bộ.
- **Kiểm tra chuẩn HTML (W3C HTML Validator):**
  - Kiểm tra mã nguồn tệp `skills.html` qua công cụ `validator.w3.org`.
  - Kết quả: Không có lỗi cấu trúc (0 Errors), tài nguyên ảnh đảm bảo có thuộc tính `alt`, phân cấp tiêu đề `<h1>` đến `<h3>` hợp lệ theo chuẩn ngữ nghĩa HTML5.

## 5. Báo cáo kiểm thử Responsive & Bố cục giao diện (F12 Device Toolbar)
- **Thiết bị & Kích thước kiểm thử:**
  - Mobile: 375px (iPhone 11/14 Promax/Xiaomi)
  - Tablet: 768px (iPad Mini/Air)
  - Desktop: >= 1200px
- **Kết quả rà soát:**
  - Đã kiểm tra tính co giãn của thanh điều hướng (Navbar Toggle), hệ thống lưới Bootstrap (Grid System) và thanh cuộn ngang.
  - Danh sách điểm cần tinh chỉnh đã được bàn giao cho Navigator xử lý theo bảng ghi nhận.

## 6. Báo cáo kiểm thử tương thích trình duyệt & Tính khả đọc CSS
- **Môi trường thử nghiệm:**
  - Trình duyệt: Google Chrome, Microsoft Edge, Cốc Cốc.
  - Chế độ: Đã kiểm tra trên Chế độ ẩn danh (Incognito/InPrivate) để loại trừ cache và tiện ích mở rộng.
- **Kết quả kiểm tra CSS & Khả năng đọc (Readability):**
  - **Độ tương phản:** Màu chữ và nền đạt yêu cầu thị giác, không có hiện tượng chữ chìm vào nền.
  - **Bố cục văn bản:** Kích thước font chữ rõ ràng, khoảng cách dòng hợp lý, văn bản tự động xuống dòng không bị tràn khung viền thẻ card.
  - **Tương thích:** Toàn bộ thành phần Bootstrap và CSS tùy biến hiển thị đồng nhất, không phát sinh lỗi lệch giao diện giữa các trình duyệt.


## 7. Thiết kế bộ ca kiểm thử đặc biệt cho Form (Edge Cases)
| STT | Tên ca kiểm thử | Loại dữ liệu | Dữ liệu thử nghiệm (Input) | Kết quả mong đợi (Expected Output) |
| :---: | :--- | :--- | :--- | :--- |
| **TC-EDGE-01** | Bỏ trống bắt buộc | Dữ liệu rỗng | Không nhập Họ tên, Email | Báo lỗi cảnh báo trường bắt buộc, không cho phép gửi dữ liệu. |
| **TC-EDGE-02** | Chuỗi ký tự cực dài | Độ dài biên (Boundary) | Nhập chuỗi 500 ký tự vào ô Tóm tắt bản thân / Mục tiêu | Khung preview tự động xuống dòng (word-wrap), không tràn vỡ thẻ card. |
| **TC-EDGE-03** | Chống mã độc XSS | Ký tự đặc biệt (Security) | `<script>alert('XSS')</script>`, `<b>Test</b>`, `@#$%^&*()` | Hiển thị dưới dạng chuỗi văn bản an toàn (escaped text), không thực thi mã lệnh HTML/JS. |
| **TC-EDGE-04** | Sai định dạng Email | Giá trị không hợp lệ | `ngantk@`, `ngantk.com`, `ngan@gmail` (thiếu phần mở rộng domain) | Trình duyệt kích hoạt cảnh báo sai chuẩn email. |
| **TC-EDGE-05** | Số điện thoại chứa ký tự | Định dạng số | `0987abc123`, `098-765-432` | Báo lỗi định dạng chỉ chấp nhận đúng 10 chữ số tiêu chuẩn. |

## 8. Bảng ca kiểm thử chi tiết (Test Matrix) & Minh chứng xử lý lỗi.

### 8.1. Ma trận ca kiểm thử (Test Matrix)[cite: 15]
| Mã ca (ID) | Chức năng kiểm thử | Loại kiểm thử | Dữ liệu đầu vào (Input) | Các bước thực hiện | Kết quả mong đợi (Expected Output) | Trạng thái |
| :---: | :--- | :--- | :--- | :--- | :--- | :---: |
| **TM-01** | Điền mẫu tự động | Chức năng chính | Bấm nút "Dùng thử" | 1. Mở trang tạo hồ sơ.<br>2. Bấm nút "Dùng thử". | Các ô nhập liệu tự động điền giá trị chuẩn; thanh tiến độ nhảy % tương ứng[cite: 10]. | **Pass** |
| **TM-02** | Xóa sạch form | Chức năng chính | Bấm nút "Đặt lại" | 1. Form đang có thông tin.<br>2. Bấm nút "Đặt lại". | Toàn bộ các ô nhập liệu xóa trắng, khung xem trước quay về trạng thái rỗng ban đầu[cite: 10]. | **Pass** |
| **TM-03** | In hồ sơ dạng in | Chức năng chính | Bấm nút "In hồ sơ" | 1. Điền đủ hồ sơ hợp lệ.<br>2. Bấm nút "In hồ sơ". | Hộp thoại in trình duyệt kích hoạt; ẩn thanh điều hướng, footer và cột nhập liệu (`no-print`)[cite: 10]. | **Pass** |
| **TM-EDGE-01** | Để trống trường bắt buộc | **Trường hợp biên 1** | Bỏ trống ô Họ tên hoặc Email | 1. Để trống thông tin.<br>2. Bấm "Tạo hồ sơ". | Hiển thị cảnh báo viền đỏ, chặn không cho tạo hồ sơ rỗng[cite: 10, 15]. | **Pass** |
| **TM-EDGE-02** | Chuỗi ký tự vượt giới hạn | **Trường hợp biên 2** | Nhập chuỗi 300 ký tự vào ô "Mục tiêu" | 1. Nhập văn bản rất dài.<br>2. Bấm tạo hồ sơ. | Tự động bẻ dòng hợp lý (word-wrap), không làm tràn hay vỡ khung thẻ in[cite: 10, 15]. | **Pass** |
| **TM-EDGE-03** | Chống mã độc kịch bản XSS | **Trường hợp biên 3** | Nhập `<script>alert('XSS')</script>` vào Họ tên | 1. Dán mã kịch bản vào form.<br>2. Bấm tạo hồ sơ. | Nội dung xử lý dạng chuỗi ký tự thuần túy, không kích hoạt hộp thoại script[cite: 10, 15]. | **Pass** |
| **TM-EDGE-04** | Giá trị số không hợp lệ | **Trường hợp biên 4** | Nhập số sản phẩm là `-3` hoặc năm `2099` | 1. Nhập số âm hoặc năm tương lai.<br>2. Bấm tạo hồ sơ. | Bắt lỗi dữ liệu, thông báo yêu cầu nhập số nguyên dương hợp lệ[cite: 15]. | **Pass** |

### 8.2. Minh chứng hình ảnh lỗi trước và sau khi xử lý
- **Trước khi xử lý:** Form không kiểm tra dữ liệu rỗng, bấm tạo hồ sơ không có bất kỳ thông báo lỗi nào[cite: 15].
  ![Lỗi trước khi xử lý](loi-form-truoc-khi-validate.png)

- **Sau khi xử lý:** Hệ thống đã bắt lỗi tính hợp lệ (Validation), xuất hiện viền đỏ và thông báo nhắc nhở người dùng nhập liệu[cite: 10, 15].
  ![Đã xử lý lỗi](form-da-xu-ly-validate.png)
