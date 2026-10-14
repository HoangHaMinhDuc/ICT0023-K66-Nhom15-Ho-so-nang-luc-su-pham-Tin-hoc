# TÀI LỆU KỸ THUẬT CÁC HÀM JAVASCRIPT
# 1. Mạch logic và Luồng xử lý chính (Data Flow)
Mã nguồn JavaScript chính được tổ chức trong thư mục `js/` (bao gồm `data.js` chứa dữ liệu tĩnh JSON và `main.js` chứa logic tương tác).
   # Luồng hoạt động:
  1. Khi trang web tải xuống xong (`DOMContentLoaded`), hàm khởi tạo sẽ gọi `renderProducts(productsData)` để hiển thị toàn bộ danh sách sản phẩm ra màn hình dưới dạng Card Bootstrap.
    2. Khi người dùng nhập từ khóa vào ô tìm kiếm hoặc chọn danh mục/năm học từ thẻ `<select>`, sự kiện `input` / `change` sẽ kích hoạt hàm `filterProducts()`.
        3. Nếu mảng kết quả sau khi lọc có độ dài bằng 0 (`list.length === 0`), hệ thống sẽ gọi hàm `handleEmptyData()` để hiển thị thông báo "Không tìm thấy kết quả phù hợp".
 # 2. Chi tiết các chức năng xử lý Tìm kiếm & Bộ lọc (Filter & Search)
    # 2.1. Hàm `filterProducts()`
  - **Chức năng**: Lấy từ khóa từ ô tìm kiếm (`<input>`) và giá trị được chọn từ các thẻ `<select>` (kỹ năng, năm học) để thực hiện lọc mảng dữ liệu sản phẩm `productsData`.
     - **Đầu vào (Input)**: Chuỗi từ khóa nhập từ người dùng và lựa chọn từ các thẻ danh sách thả xuống.
         - **Đầu ra (Output)**: Gọi hàm `renderProducts()` với mảng dữ liệu đã được lọc.
   # 2.2. Hàm `renderProducts(dataList)`
      - **Chức năng**: Nhận danh sách mảng dữ liệu đầu vào và duyệt qua từng phần tử bằng phương thức `forEach()` để tạo và chèn các thẻ Card HTML tương ứng lên màn hình.
         - **Đầu vào (Input)**: Mảng đối tượng sản phẩm `dataList`.
              - **Đầu ra (Output)**: Giao diện danh sách sản phẩm được cập nhật động trên màn hình.

    # 2.3. Hàm `handleEmptyData(container)`
 - **Chức năng**: Kiểm tra nếu mảng kết quả tìm kiếm bị rỗng, tiến hành chèn giao diện thông báo kèm biểu tượng và dòng chữ *"Không tìm thấy kết quả phù hợp"*.
   - **Đầu vào (Input)**: Phần tử DOM container chứa danh sách.
# 3. Quy chuẩn Kỹ thuật JavaScript (ES6+)
- **Cú pháp ES6+**:
  - Khai báo biến bằng cách sử dụng `const` cho các phần tử DOM/hằng số không đổi và `let` cho các biến thay đổi trong phạm vi.
  - Sử dụng hàm mũi tên (`Arrow Functions`) cho các sự kiện xử lý gọi lại (callback) và duyệt mảng.
 - **Lắng nghe sự kiện (`EventListener`)**:
  - Gắn sự kiện `addEventListener('input', ...)` cho ô tìm kiếm từ khóa.
  - Gắn sự kiện `addEventListener('change', ...)` cho bộ lọc Dropdown.
- **Xử lý mảng (`Array Methods`)**:
  - Sử dụng phương thức `.filter()` để lọc dữ liệu.
  - Sử dụng `.toLowerCase()` và `.includes()` để tìm kiếm từ khóa không phân biệt chữ hoa/chữ thường.
