# API tài khoản khách và phân quyền đơn

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **api tài khoản khách và phân quyền đơn**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

01, 10.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/customer-api.cjs`
- `WEB/.private/customer-users.json (runtime)`

## Yêu cầu triển khai

Export createCustomerApi({storePath,bookingApi}) với matches, handle, getCustomerFromRequest. API /api/customer: POST register/login/logout; GET session/bookings/notifications; POST bookings/:code/payment.

Đăng ký họ tên 2–80 ký tự, email chuẩn hóa lowercase không trùng, điện thoại Việt Nam và mật khẩu 10–128 ký tự theo quy tắc hiện có. Hash mật khẩu bằng scrypt với salt ngẫu nhiên; so sánh an toàn; phản hồi chỉ publicUser.

Phiên cookie tour_customer HttpOnly, SameSite=Strict, Path=/api; có CSRF token cho thao tác thay đổi. Chặn đăng nhập quá nhịp. booking/notification/payment luôn gắn customerId từ phiên, không nhận quyền sở hữu do client tự khai.

Thông báo lấy từ statusHistory của các đơn khách sở hữu, gồm cập nhật administrator/payment và lý do từ chối. Đăng xuất xóa session và cookie. Lưu user bền vững riêng với kho đơn.

## Tiêu chí nghiệm thu

Tạo hai tài khoản thử trong store tạm; tài khoản A không đọc/trả tiền đơn B; email trùng bị từ chối; thiếu/sai CSRF không đổi trạng thái; mật khẩu không xuất hiện trong JSON trả về.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module api tài khoản khách và phân quyền đơn cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
