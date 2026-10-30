# Thẻ điểm đến, sự kiện tích hợp và đóng gói game

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **thẻ điểm đến, sự kiện tích hợp và đóng gói game**. Phạm vi: **GAME và WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

05, 26–35, 16.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/integrations/tourismApi.ts`
- `GAME/src/data/destinations.ts`
- `GAME/vite.config.ts`
- `GAME/dist/ (build)`
- `WEB/dist/game/ (bản phân phối)`

## Yêu cầu triển khai

TourismApiAdapter singleton có getDestination/getToursForDestination và dispatchAction cho view_destination/view_tour/book_tour/sync_progress/claim_reward. Phát CustomEvent thai_nguyen_quest_event; khi nhúng iframe phát message type THAI_NGUYEN_QUEST_EVENT. ID destination/tour không tự coi là cùng hệ ID website nếu chưa có mapping.

Destination card hiển thị thông tin đời thực và tour gợi ý. Adapter hiện phát event là điểm tích hợp, chưa đồng nghĩa đã tạo booking hoặc đồng bộ tài khoản máy chủ. Không hiển thị thưởng game là tiền/voucher thực nếu chưa có API thực.

Khi xây host nhận message, kiểm tra origin/source/type và whitelist action; dữ liệu cá nhân/token không truyền qua postMessage wildcard. Giữ khả năng chạy standalone không có parent.

Build nhúng bằng npm run build -- --base=/game/, rồi chép nội dung GAME/dist vào WEB/dist/game. Kiểm tra asset URL sau build. Bản dist đã đóng gói không thay thế source TypeScript; không sửa file hash JS trong dist để thêm gameplay.

## Tiêu chí nghiệm thu

Game chạy riêng tại dev server và qua /game/; asset không 404; destination card phát đúng action/id; iframe nhận đúng message; click book_tour không bị hiểu nhầm là đơn đã được tạo.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module thẻ điểm đến, sự kiện tích hợp và đóng gói game cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
