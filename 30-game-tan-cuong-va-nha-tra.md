# Chương Tân Cương và nhà trà

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **chương tân cương và nhà trà**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27–29, 31, 32.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/scenes/TanCuongScene.ts`
- `GAME/src/scenes/TeaHouseScene.ts`
- `GAME/scripts/check-village.cjs`

## Yêu cầu triển khai

Sinh làng chè có môi trường, công trình, bụi chè, NPC, người làm chè và hiệu ứng; nhân vật có thể tìm các trạm hái/sao/pha theo quest và guide. Dùng ID quest/objective từ data thay vì so text.

Kết nối harvest → processing → brewing bằng outcome có kiểm tra; applyHarvestOutcome/applyProcessingOutcome cập nhật vật phẩm/xu/objectives và lưu. Không thưởng chỉ vì người chơi mở rồi đóng minigame.

TeaHouseScene là nội thất dùng launch/pause/resume với TanCuongScene; có các trạm, hành động luyện tập và lối ra. Khi rời, đóng modal, dọn input và gọi onReturn đúng một lần. Hỗ trợ luyện lại mà không phá quest đã hoàn thành.

Có chòi thưởng trà, ngồi/đứng, cinematic hoàng hôn và phản hồi kết thúc hành trình theo state. Autosave gồm tọa độ/hướng, inventory, quests và tiến trình. Giữ cảnh về làng là điểm nối tới các vùng khác, không hardcode khóa tuyến tuần tự trái với save hiện có.

## Tiêu chí nghiệm thu

Hoàn thành chuỗi chè nhận mảnh trà một lần; vào/ra nhà trà nhiều lần không treo điều khiển; tải lại trở về checkpoint; thực hành lại không làm mất đồ hoặc nhân đôi phần thưởng.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module chương tân cương và nhà trà cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
