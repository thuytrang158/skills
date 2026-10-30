# Chi tiết tour, bản đồ tour và tải lịch trình

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **chi tiết tour, bản đồ tour và tải lịch trình**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

02, 03, 04; 06 cung cấp nguyên tắc bản đồ.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/tour-details.js`
- `WEB/dist/tour-details.css`

## Yêu cầu triển khai

Sinh tourDetailsHTML, tourMarkdown, openTour và renderTourDetailMap để hiển thị đầy đủ lịch trình từng ngày/giờ, tổng quan, đối tượng, độ khó, mùa phù hợp, di chuyển, ăn nghỉ, dịch vụ, phương án thời tiết và nguồn dẫn. Bổ sung đầy đủ lựa chọn lọc từ catalogue thay vì giới hạn bộ 5 điểm cũ.

Mở tour từ thẻ hoặc hash #tour-<id>. Tải lịch trình Markdown UTF-8 có cảnh báo giá dự kiến; nội dung tải tương ứng đúng tour đang xem. Đóng/mở liên tục phải hủy map instance cũ và dọn listener.

Tọa độ tour là vị trí khu vực gần đúng; đường nối minh họa không phải đường ô tô. Ảnh không có nguồn đúng thì giữ chú thích minh họa hoặc thiếu ảnh; không tự ghép địa danh khác. Cho phép xem tour ngay cả khi booking API lỗi.

## Tiêu chí nghiệm thu

Kiểm tra tour một ngày và nhiều ngày, mở bằng URL hash, tải Markdown, mở/đóng nhiều lần; không xuất hiện lỗi Leaflet container already initialized; booking có thể gắn thêm vào openTour.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module chi tiết tour, bản đồ tour và tải lịch trình cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
