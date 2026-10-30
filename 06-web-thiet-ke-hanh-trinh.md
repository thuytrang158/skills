# Thiết kế hành trình theo quy tắc và bản đồ

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **thiết kế hành trình theo quy tắc và bản đồ**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

02; độc lập với AI Planner ở các file 17–23.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/app.js: generatePlan, renderPlan, planText và quản lý hành trình`

## Yêu cầu triển khai

Sinh bộ thiết kế đơn giản với 5 điểm Tân Cương, Hồ Núi Cốc, ATK Định Hóa, Thái Hải, La Bằng. Đầu vào: ngân sách/người, số người, số ngày, phong cách và danh sách điểm. Khi khách đã chọn điểm, giữ lựa chọn; chưa chọn thì ưu tiên phong cách và chi phí, lấy tối đa min(days*2,3).

Tính theo công thức hiện có, đơn vị VND/người: visit=sum(cost điểm); food=days*180000; stay=(days-1)*350000; transport=ceil((days*600000/people)/10000)*10000; total=visit+food+stay+transport; groupTotal=total*people. Cảnh báo vượt ngân sách và mật độ điểm quá cao. Chia điểm theo ngày, có ngày nghỉ tự do khi thích hợp.

Tạo bản đồ Leaflet/OSM với marker số thứ tự, đường nối nét đứt, attribution và liên kết Google Maps đã encode. Không tải Leaflet được thì hiện sơ đồ dự phòng. Dọn map trước khi tạo mới.

Lưu tối đa 10 lịch trình tại tra-plans, xem lại và tải file; dùng readStore/writeStore có bắt lỗi. Đây là bộ tính theo quy tắc, không gọi mô hình AI và không thay catalogue 10 tour.

## Tiêu chí nghiệm thu

Kiểm tra một người/nhiều người, một ngày/nhiều ngày, có/không chọn điểm và vượt ngân sách; tổng nhóm bằng tổng/người nhân số khách; mất mạng vẫn có sơ đồ và tải lịch trình.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module thiết kế hành trình theo quy tắc và bản đồ cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
