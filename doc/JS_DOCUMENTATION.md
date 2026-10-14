# TÀI LIỆU KỸ THUẬT CÁC HÀM JAVASCRIPT & JQUERY 
 # 1. Cấu trúc dữ liệu (`js/data.js`)
Dữ liệu dự án được lưu trữ dưới dạng mảng các đối tượng (Array of Objects):
- `MEMBERS`: Lưu trữ thông tin 4 thành viên (Mã SV, Họ tên, Vai trò, Kỹ năng, Avatar, Liên hệ).
- `PRODUCTS`: Lưu trữ danh sách sản phẩm bài giảng, phần mềm, phiếu bài tập (Tiêu đề, Loại, Công nghệ, Link demo).
# 2. Các hàm xử lý chính (`js/main.js`)
    # 2.1. Trang Hồ sơ Thành viên (`thanhvien.html`)
- `renderMembers(list)`: Nhận mảng dữ liệu thành viên và sinh cấu trúc HTML Card tương ứng lên giao diện.
- `filterMembers()`: Lắng nghe sự kiện `input` trên ô tìm kiếm `#m-search` để lọc thành viên theo tên hoặc kỹ năng.
     # 2.2. Trang Sản phẩm (`sanpham.html`)
- `renderProducts(list)`: Sinh danh sách sản phẩm dạng Grid responsive Bootstrap 5.3.
- `filterProducts()`: Lắng nghe các sự kiện trên ô tìm kiếm `#p-search`, lọc kỹ năng `#p-skill`, năm học `#p-year` và sắp xếp `#p-sort`.
- `showProductDetail(id)`: Hiển thị thông tin chi tiết sản phẩm trong Modal `#productModal` khi bấm "Xem chi tiết".
-   # 3. Logic xử lý dữ liệu rỗng (Empty State)
- Khi bộ lọc trả về mảng rỗng (`filteredList.length === 0`):
  - Cập nhật thông số: *"Hiển thị 0/5 sản phẩm"*.
  - Khung danh sách ẩn đi và hiển thị thẻ thông báo `#product-empty`: *"Không tìm thấy sản phẩm. Hãy đổi bộ lọc hoặc bấm “Đặt lại”."*
