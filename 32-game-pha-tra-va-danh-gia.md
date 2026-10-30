# Mô phỏng pha trà, công thức và đánh giá

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **mô phỏng pha trà, công thức và đánh giá**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27–30.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/minigames/TeaBrewingMinigame.ts`
- `GAME/src/systems/TeaBrewingEvaluator.ts`
- `GAME/src/data/teaBrewingProfiles.ts`
- `GAME/src/data/teaCultivars.ts`

## Yêu cầu triển khai

Sinh luồng pha guided/free với 12 stage theo dữ liệu hiện có: lựa trà, dụng cụ, lượng trà, nước, nhiệt, rót/ngâm, hương và chén. Dùng ITeaBrewingSessionState để snapshot stage/tham số và tiếp tục sau đóng/mở.

TeaBrewingEvaluator nhận BrewingParameters, so với profile giống trà để tính SimulatedTeaResult xác định; feedback theo lượng/nhiệt/thời gian và kết quả pha, không dùng random thay chất lượng. Clamp NaN, số âm và giá trị ngoài khoảng.

Lưu teaBrewingSession, history và favoriteTeaRecipes trong save; công thức có ID, tên và thời điểm. Mục tiêu quest chỉ tiến khi đạt hành động được yêu cầu, thao tác lặp không nhân phần thưởng. Có reset/retry có chủ đích, không xóa kho game.

Nói rõ kết quả là mô phỏng, không phải kết luận cảm quan thực của nghệ nhân. destroy dọn timer, animation và listener.

## Tiêu chí nghiệm thu

Cùng tham số cho cùng kết quả; đổi nhiệt/ngâm có ảnh hưởng theo profile; load lại tiếp tục đúng stage; công thức yêu thích khôi phục đúng số; hoàn tất quest và luyện lại không trùng thưởng.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module mô phỏng pha trà, công thức và đánh giá cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
