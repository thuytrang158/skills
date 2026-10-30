# Giao diện tài khoản, thông báo và QR mô phỏng

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **giao diện tài khoản, thông báo và qr mô phỏng**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

12, 10.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/customer.js`
- `WEB/dist/customer.css`
- `WEB/dist/index.html: customer-dialog`

## Yêu cầu triển khai

Sinh dialog đăng ký/đăng nhập, tự khôi phục phiên qua GET session, nút tài khoản trên header và dashboard khách. Expose window.customerUser, openCustomerAccount, refreshCustomerDashboard để booking dùng.

Dashboard hiển thị đơn, ngày, số khách, tổng tiền, bookingStatus/paymentStatus, thông báo và lý do từ chối. Chỉ cho mở payment khi đơn confirmed và chưa paid. QR là nội dung tham chiếu nội bộ, số tiền là depositVND; chọn kết quả thành công/thất bại và POST đúng endpoint customer payment với CSRF.

Không coi quét QR là chuyển tiền ngân hàng thật. Lỗi/thất bại phải hiện trạng thái và cho thử lại khi hợp lệ. Poll khi dialog đang mở và đã có phiên; dọn interval khi đăng xuất. Token/CSRF chỉ giữ trong bộ nhớ giao diện theo thiết kế, không ghi vào URL hoặc localStorage.

## Tiêu chí nghiệm thu

Đăng ký → booking → admin duyệt → có thông báo → trả cọc mô phỏng; thử từ chối và payment thất bại; chưa duyệt không có nút thanh toán; reload lấy lại phiên đúng.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module giao diện tài khoản, thông báo và qr mô phỏng cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
