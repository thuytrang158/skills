# Bố cục và giao diện website

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **bố cục và giao diện website**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

01; 03 cung cấp danh mục; các module giao diện còn lại gắn vào khung này.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/index.html`
- `WEB/dist/style.css`
- `WEB/dist/assets/`

## Yêu cầu triển khai

Sinh trang chủ tiếng Việt với thương hiệu Trà Journey, màu xanh trà/kem, ảnh hero, thanh điều hướng, tìm tour, danh mục tour, game, AI Planner, ẩm thực, thiết kế hành trình, tin tức, đánh giá và footer.

Giữ các điểm gắn DOM: #search, #destination, #duration, #price, #sort, #tags, #tour-grid, #result-count, #planner, #places, #plan-result, #news-story-grid, #cuisine-grid, #review-grid, #saved-plans, #modal, #modal-content, #toast, #customer-dialog, #customer-content, #travel-chat. Các tên này là hợp đồng với JavaScript.

Tải script defer theo thứ tự: tours-data, tour-reviews-data, tour-engagement, cuisine-data, news-data, app, tour-details, tour-booking, cuisine, news, chat-widget, customer. tour-details và tour-booking mở rộng openTour nên không đảo thứ tự tùy tiện.

Có nhãn cho form, skip link, dialog đóng bằng bàn phím, thông báo aria-live, trạng thái rỗng và responsive. Dùng assets sẵn có hoặc ghi rõ thiếu ảnh; không gán nhầm ảnh địa danh. Liên kết game /game/, Planner /ai-planner/.

## Tiêu chí nghiệm thu

Mở trên desktop và màn hình nhỏ; mọi mục điều hướng và dialog hoạt động; không có lỗi do thiếu phần tử DOM hoặc thứ tự script; không tràn ngang.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module bố cục và giao diện website cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
