# Tìm kiếm, lọc, sắp xếp và yêu thích tour

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **tìm kiếm, lọc, sắp xếp và yêu thích tour**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

02, 03.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/app.js`
- `WEB/dist/tour-engagement.js`
- `WEB/dist/tour-engagement.css`
- `WEB/dist/tour-reviews-data.js`

## Yêu cầu triển khai

Sinh filteredTours, renderTours và tourCardHTML. Kết hợp bộ lọc điểm đến, số ngày, giá khởi điểm tối đa và tag; sắp xếp giá tăng/giảm mà không thay đổi danh mục gốc. Hiện số kết quả, trạng thái không có tour và nút xóa bộ lọc.

Thẻ tour hiển thị ảnh đúng, tên, số ngày, tuyến, tags, giá tham khảo, mở chi tiết và nút yêu thích. Dùng id tour ổn định và event delegation cho thẻ được render lại. Lưu yêu thích ở tra-favorites; JSON hỏng hoặc localStorage bị chặn phải có fallback.

Đánh giá tour mặc định là chưa có phản hồi; tour-reviews-data có thể giữ dữ liệu kiểm kê cũ nhưng không hiển thị review hư cấu như khách thật. Hiển thị thông tin nhanh và điều hướng các phần trong dialog qua tourQuickFactsHTML/bindTourEngagement.

## Tiêu chí nghiệm thu

Lọc đồng thời nhiều điều kiện đúng; xóa lọc khôi phục 10 tour; yêu thích còn sau reload; nút yêu thích không vô tình mở dialog; dữ liệu localStorage hỏng không làm trang dừng.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module tìm kiếm, lọc, sắp xếp và yêu thích tour cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
