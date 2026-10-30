# Giao diện đặt tour trong popup

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **giao diện đặt tour trong popup**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

05, 09, 10, 13.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/tour-booking.js`
- `WEB/dist/tour-details.css và style liên quan`

## Yêu cầu triển khai

Mở rộng openTour sau khi tour-details đã nạp. Tải catalog/departures từ API; tạo form ngày, nhóm tuổi, phương tiện, điểm đón, phòng, dịch vụ thêm, coupon, người đại diện và hành khách tùy chọn. Dùng đúng name/id mà bộ tính giá và backend hiểu.

Hiện bảng giá chi tiết, cọc/còn lại, trường cần báo giá, lỗi theo trường và số chỗ mô phỏng. Khi chọn đổi, tải quote từ máy chủ, chống response cũ ghi đè lựa chọn mới. Trước gửi đơn phải đăng nhập tài khoản khách, giữ hold còn hiệu lực và khóa nút tránh gửi lặp.

Có tab/bước phù hợp desktop và mobile, bàn phím đi được trong modal. Refresh quote/chỗ theo khoảng cấu hình; khi đóng popup dọn interval, observer, listener và giải phóng hold khi thích hợp. Lỗi catalog không chặn xem thông tin tour.

Không giữ luồng phiếu localStorage cũ làm booking chính. Không hiển thị đã xác nhận chỉ vì POST tạo đơn thành công; phản ánh trạng thái chờ admin duyệt.

## Tiêu chí nghiệm thu

Thử chưa đăng nhập, quote lỗi, hold hết hạn, thiếu liên hệ, gửi lặp, thay ngày nhanh, đóng mở nhiều tour; tạo đơn thành công xuất hiện trong tài khoản và admin, không tự chuyển sang đã thanh toán.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module giao diện đặt tour trong popup cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
