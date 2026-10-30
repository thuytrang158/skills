# API quản trị và bootstrap admin

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **api quản trị và bootstrap admin**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

10.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/admin-api.cjs`
- `WEB/.private/admin-users.json (runtime)`

## Yêu cầu triển khai

Export createAdminApi({storePath,bookingApi}) và bootstrap. Bootstrap chỉ khi chưa có admin hoạt động; sinh mật khẩu ngẫu nhiên và in một lần, lưu salt/hash scrypt. Không chạy bootstrap trên kho thật đã có tài khoản.

API /api/admin: POST login/logout/password; GET session/dashboard/orders/orders/:code/users/audit; POST orders/:code/decision và users; PATCH users/:id. Danh sách orders hỗ trợ q/status/page, page size 12.

Cookie tour_admin HttpOnly, SameSite=Strict, Path=/api/admin, phiên 8 giờ. CSRF cho thao tác ghi, giới hạn đăng nhập. safeBooking không lộ token đơn hoặc trường bí mật. Duyệt/từ chối gọi bookingApi; từ chối cần lý do ít nhất 5 ký tự; ghi audit ai/làm gì/khi nào.

Tạo admin với mật khẩu tạm; đổi mật khẩu cần mật khẩu hiện tại và mật khẩu mới 12–128 ký tự. Không tự khóa tài khoản đang dùng; giữ tối thiểu một admin hoạt động. Những ràng buộc này kiểm tra ở backend.

## Tiêu chí nghiệm thu

Chưa đăng nhập trả 401; sai CSRF bị chặn; duyệt/từ chối cập nhật kho đơn và thông báo khách; không khóa admin cuối; audit không chứa mật khẩu/token.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module api quản trị và bootstrap admin cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
