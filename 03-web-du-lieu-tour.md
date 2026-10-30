# Danh mục 13 điểm đến và 10 tour

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **danh mục 13 điểm đến và 10 tour**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

01; dữ liệu tour gốc và cấu hình booking là đầu vào biên tập.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/tours-data.js`
- `WEB/export-catalogue.cjs`
- `WEB/dist/data/tours.json`
- `WEB/dist/data/tour-catalogue.md`

## Yêu cầu triển khai

Tạo globalThis.TRA_CATALOG làm nguồn danh mục chính: places, tours, sources, common và dữ liệu nguồn/chính sách theo cấu trúc hiện có. Giữ 10 mã TJ01–TJ10, id tour 101–110 và 13 destination ID ổn định; lấy đầy đủ tên, tuyến và lịch trình từ dữ liệu gốc khi có.

Mỗi tour có code, slug, name, destinationIds/places, days/nights, price/priceMax, tags, ảnh/chú thích, summary/description, đối tượng, thể lực, mùa, di chuyển, itinerary theo ngày với activities có thời gian, ăn nghỉ, dịch vụ gồm/không gồm, chuẩn bị, thời tiết và nguồn. Giữ trạng thái draft_itinerary, rating null, reviewCount 0.

Giá biên tập cho một người lớn trong đoàn 10 người ngày thường, không phải báo giá được xác nhận. Chuẩn hóa Yên Dương thành Yến Dương và giữ aliases; phân biệt Chùa Hang/Kim Sơn Tự với địa danh trùng tên.

Sinh exporter đọc nguồn JS rồi xuất JSON và Markdown UTF-8. Không duy trì ba bộ dữ liệu thủ công độc lập. Không tạo đánh giá khách hàng để làm đầy trang. Khi thiếu nguyên bản nội dung/ảnh, liệt kê phần thiếu; không tuyên bố phục dựng chính xác từ tên file.

## Tiêu chí nghiệm thu

10 mã/id duy nhất; 13 điểm được tour tham chiếu; số ngày/đêm và giờ lịch trình nhất quán; xuất lại JSON/Markdown khớp nguồn JS; chạy node check.cjs sau khi tích hợp.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module danh mục 13 điểm đến và 10 tour cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
