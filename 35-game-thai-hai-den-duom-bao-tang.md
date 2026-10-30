# Thái Hải, Đền Đuổm và Bảo tàng văn hóa

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **thái hải, đền đuổm và bảo tàng văn hóa**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27–29.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/scenes/RegionalChapterScene.ts`
- `ThaiHaiScene.ts`
- `DenDuomScene.ts`
- `BaoTangVanHoaScene.ts (src/scenes)`
- `GAME/src/systems/RegionalExplorerGuide.ts`
- `GAME/src/minigames/DestinationActivityMinigame.ts`
- `TungConMinigame.ts (src/minigames)`

## Yêu cầu triển khai

RegionalChapterScene nhận cấu hình region, dựng môi trường, điểm khám phá, hướng dẫn, hoạt động và checkpoint. Ba lớp scene con truyền cấu hình riêng, không sao chép toàn bộ runtime.

RegionalExplorerGuide đánh dấu visitedStops khi đi đúng vùng, render hướng dẫn, lưu theo region. DestinationActivityMinigame phân mode thai_hai/den_duom/museum với thao tác chọn/ghép/sắp xếp và submit kiểm tra. Thái Hải kết nối cộng đồng/văn hóa và fragment_people; Đền Đuổm có không gian di tích/lễ hội, TungConMinigame và fragment_tradition.

Bảo tàng là chapter trưng bày, cho chọn cardIds, đặt title/captions và lưu exhibition trong IRegionProgress, không tạo thêm fragment thứ tám. Văn bản triển lãm do người dùng nhập phải escape.

Hoàn thành các mục tiêu rồi awardIfComplete qua ProgressionService; phục hồi selections/completedActivities/checkpoint sau reload. Hộ chiếu và ending dựa trên state chung, không hardcode hoàn tất khi chỉ ghé điểm.

## Tiêu chí nghiệm thu

Đủ ba scene vào/ra được; hoạt động sai đáp án không hoàn thành; ném còn khởi động lại không giữ timer cũ; triển lãm lưu/khôi phục đúng; hai mảnh người/truyền thống trao đúng một lần.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module thái hải, đền đuổm và bảo tàng văn hóa cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
