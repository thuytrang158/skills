# Trang quản trị đơn và tài khoản

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **trang quản trị đơn và tài khoản**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

14.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/admin/index.html`
- `WEB/dist/admin/admin.js`
- `WEB/dist/admin/admin.css`

## Yêu cầu triển khai

Sinh trang /admin/ với đăng nhập, dashboard tổng/chờ/duyệt/từ chối, đơn gần đây, danh sách tìm kiếm/lọc/phân trang, chi tiết liên hệ/lựa chọn/giá và lịch sử đơn.

Cung cấp duyệt, từ chối có lý do, quản lý admin, đổi mật khẩu, audit và xuất CSV. Lấy trạng thái cập nhật từ server sau thao tác; chống click lặp và hiển thị lỗi 401/403/409/422 rõ ràng. Giữ CSRF trong phiên giao diện.

CSV mã hóa UTF-8 tiếng Việt, escape dấu nháy/dấu phẩy/xuống dòng, xử lý ô có thể được bảng tính hiểu là công thức. Không xuất token booking, hash/salt mật khẩu hoặc session. Giao diện có empty state và không tràn bảng trên mobile.

## Tiêu chí nghiệm thu

Tìm theo mã/tên/email/điện thoại; lọc và chuyển trang đúng; từ chối thiếu lý do bị chặn; CSV mở đúng tiếng Việt; session hết hạn quay về đăng nhập mà không thực hiện lệnh cũ.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module trang quản trị đơn và tài khoản cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
