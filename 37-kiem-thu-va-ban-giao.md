# Kiểm thử, vận hành cục bộ và bàn giao

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **kiểm thử, vận hành cục bộ và bàn giao**. Phạm vi: **Cả ba dự án**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

Tất cả module thuộc phạm vi được chọn.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/check.cjs`
- `WEB/test/demo-booking-api.test.cjs`
- `GAME/test/quest_and_save.test.js`
- `lake_chapter.test.js`
- `region_access.test.js (GAME/test)`
- `PLANNER/tests/`
- `README của từng dự án`
- `các script export/configure hiện có`

## Yêu cầu triển khai

Website: chạy npm run check và node check.cjs. Trước npm test, đọc test/demo-booking-api.test.cjs: bản hiện có dùng store mặc định trong .private và có kỳ vọng cũ; chạy trong bản sao tạm không có dữ liệu thật hoặc sửa harness dùng statePath tạm khi triển khai module kiểm thử. Không chạy trực tiếp bài test đó lên kho đang dùng. Sau sửa catalogue chạy node export-catalogue.cjs; sau sửa nguồn RAG chạy npm run export:rag. check chỉ kiểm tra một số cú pháp/logic, không thay thế kiểm tra trình duyệt.

Game: npm test, npm run build và node scripts/check-village.cjs khi thay chương Tân Cương. Quan sát menu, điều khiển desktop/mobile, modal, save/reload, đổi vùng, minigame và ending. Không coi test tên trường/chuỗi đơn thuần là bằng chứng gameplay hoàn chỉnh.

Planner độc lập và tích hợp chạy riêng từ đúng thư mục bằng python -m unittest discover -s tests nếu test hiện có dùng unittest; kiểm tra nội dung test trước chọn runner. Kiểm tra cú pháp/import mà không tải model khi có thể. Mock Groq/Ollama, OSRM, Nominatim, nguồn HTML và embeddings trong unit test; smoke test thật chỉ khi môi trường có sẵn.

Khởi động WEB bằng npm start; chỉ khi kho mới cần npm run admin:bootstrap. Planner dùng uvicorn src.api:app --host 127.0.0.1 --port 8000. Game dùng npm run dev. Không xóa .private/save để tạo kết quả test đẹp; dùng store tạm.

Tài liệu bàn giao ghi rõ lệnh đã chạy/kết quả, file thay đổi, phần cần key/model/mạng, hạn chế demo và lỗi tồn đọng. Giữ README/LICENSE/.gitignore, mẫu env và package lock; không commit .env, .private, virtualenv/node_modules. integrate-engagement.cjs là tiện ích chỉnh nguồn có thể cũ, đọc trước, không chạy tự động ghi đè giao diện.

## Tiêu chí nghiệm thu

Một người khác làm theo README chạy được ba dự án; không có khóa hoặc dữ liệu khách trong gói; danh mục/API/game đồng nhất; phân biệt kiểm tra đã chạy với kiểm tra còn cần làm.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module kiểm thử, vận hành cục bộ và bàn giao cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
