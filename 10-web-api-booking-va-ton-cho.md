# Booking API, giữ chỗ và vòng đời đơn

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **booking api, giữ chỗ và vòng đời đơn**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

09; 12 cung cấp bộ giải tài khoản khách; 14 tiêu thụ thao tác duyệt.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/demo-booking-api.cjs`
- `WEB/.private/booking-state.json (chỉ sinh lúc chạy)`

## Yêu cầu triển khai

Export createDemoBookingApi(configPath,statePath). Cung cấp matches/handle và các hàm liên kết adminList, adminDecide, customerList, customerPay, setCustomerResolver. API: GET /api/demo/catalog, /departures?tourCode=; POST /quote, /date-requests, /holds, /holds/release, /bookings, /payments/simulate; GET /bookings/:code; POST /bookings/:code/cancel và /reschedule, tất cả dưới /api/demo.

Hold có hạn 10 phút, trừ số chỗ còn khả dụng cùng booking đã ghi nhận; hết hạn hoặc giải phóng thì trả chỗ. Kiểm tra lại chỗ khi tạo đơn và đổi ngày để ngăn oversell. Tạo đơn cần tài khoản khách theo resolver hiện có; token đơn ngẫu nhiên, truy cập qua X-Booking-Token, không đưa vào URL/localStorage hoặc phản hồi admin công khai.

Ghi lịch sử trạng thái, thông tin đại diện bắt buộc, hành khách tùy chọn. Lưu bền vững bên ngoài public, ghi file nhất quán; khởi động lại giữ đơn. Áp dụng lead time, hủy/hoàn tiền mô phỏng và phí đổi ngày từ config. Tách bookingStatus khỏi paymentStatus, giữ tên trạng thái và nhánh chuyển trong mã gốc khi phục dựng.

Duyệt trước thanh toán; hủy/trả chỗ và thanh toán phải chống thao tác lặp. Khi nâng cấp luồng đổi ngày, tính quote hợp lệ trước khi cập nhật kho chỗ.

## Tiêu chí nghiệm thu

Test API với store trong thư mục tạm: hold hết hạn, token sai, truy cập chéo tài khoản, thiếu chỗ, hủy hai lần, đổi lịch không hợp lệ và persistence sau tạo lại API. Không chạy thử ghi vào .private thật.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module booking api, giữ chỗ và vòng đời đơn cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
