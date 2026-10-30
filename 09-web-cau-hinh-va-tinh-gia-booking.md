# Cấu hình booking và máy tính báo giá

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **cấu hình booking và máy tính báo giá**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

03; đọc PROMPT_BOOKING_TOUR_DEMO_V2.md và tour-booking-config-v2.json ở workspace nếu còn.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/data/tour-booking-config-v2.json`
- `WEB/demo-booking-api.cjs: validateSelection/quoteSelection`
- `WEB/dist/tour-booking.js: calculateDemoQuote`

## Yêu cầu triển khai

Giữ schemaVersion/currency/locale/timezone/mode, lookupCatalogs, pricingEngine, inventoryDemo, simulatedPayment, demoPolicies và cấu hình từng mã TJ01–TJ10. Danh mục booking liên kết đúng code/id của catalogue.

Báo giá từ người lớn/trẻ em/trẻ nhỏ, ngày khởi hành, phương tiện, điểm đón, phòng/số phòng, addons và mã ưu đãi. Xử lý các đơn vị per_person, per_person_per_day, per_day_per_booking, per_adult, per_room_per_night và khoản theo booking; áp dụng override của từng tour.

Giá null là dịch vụ cần báo giá, không hiểu bằng 0. Kiểm tra tuổi ở ngày khởi hành khi có ngày sinh, giới hạn trẻ/khách và điều kiện thể lực theo cấu hình. Không cộng đồng thời ưu đãi nhóm và coupon khi luật hiện có loại trừ.

Tổng từ lineItems; cọc 30% làm tròn nghìn theo công thức floor((total*30/100+500)/1000)*1000; balance=total-deposit. Backend tính lại toàn bộ, không tin tổng tiền frontend gửi. Hai nơi tính giá phải cho cùng kết quả trên fixture chung.

## Tiêu chí nghiệm thu

Báo giá TJ01 khớp fixture gốc; kiểm tra dịch vụ null, coupon hết hạn, số phòng, nhóm trẻ, tampering tổng tiền; tổng lineItems và cọc/còn lại khớp nhau.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module cấu hình booking và máy tính báo giá cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
