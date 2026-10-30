# HTTP server, static và proxy FastAPI

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **http server, static và proxy fastapi**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

01, 10, 12, 14, 24.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/server.cjs`

## Yêu cầu triển khai

Dùng node:http/fs/path, đọc .env cục bộ mà không ghi đè biến môi trường đã có. Tạo booking/admin/customer/chat API một lần khi khởi động; nối booking resolver tới getCustomerFromRequest.

Dispatch theo thứ tự admin → customer → demo booking → chat; sau đó /api/ còn lại chuyển sang 127.0.0.1:8000. POST /api/chat chỉ nhận phương thức hỗ trợ. Không proxy nhầm /api/admin hoặc /api/demo sang Python.

Phục vụ static chỉ dưới WEB/dist, directory dùng index.html; decode URL lỗi trả 400, chặn traversal và đặt MIME/nosniff. .private và .env nằm ngoài public. Khi FastAPI dừng trả JSON 503 dễ hiểu, website thường vẫn xem được.

Giữ cổng 4173 và cách gọi npm start của dự án. Không tự mở server public hoặc triển khai hosting trong bước sinh module.

## Tiêu chí nghiệm thu

GET /, /admin/, /game/, /ai-planner/ đúng file; không truy cập được .private/.env hoặc đường dẫn thoát root; API cục bộ đúng handler; FastAPI dừng cho 503 thay vì làm Node crash.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module http server, static và proxy fastapi cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
