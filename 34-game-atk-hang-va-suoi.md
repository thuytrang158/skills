# Các chương ATK, Hang Phượng Hoàng và Suối Cửa Tử

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **các chương atk, hang phượng hoàng và suối cửa tử**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27–29.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/scenes/AtkDinhHoaScene.ts`
- `HangPhuongHoangScene.ts`
- `SuoiCuaTuScene.ts (src/scenes)`
- `GAME/src/minigames/HistoricalTimelineMinigame.ts`
- `CaveLightMinigame.ts`
- `RiverCrossingMinigame.ts`
- `CulturalQuizModal.ts (src/minigames)`

## Yêu cầu triển khai

Mỗi scene có môi trường nhận diện, NPC, tương tác, quest, minigame và đường trở về bản đồ; sử dụng initializeRegionSystems/persistRegionCheckpoint/transitionToRegion. Không làm mới toàn bộ quest khi vào vùng.

ATK: câu chuyện lịch sử và HistoricalTimelineMinigame sắp sự kiện theo dữ liệu, hoàn thành mục tiêu nhận fragment_history. Hang Phượng Hoàng: khám phá/ánh sáng qua CaveLightMinigame, nhận fragment_nature khi đủ điều kiện. Suối Cửa Tử: RiverCrossingMinigame và thử thách khám phá, nhận fragment_exploration. CulturalQuizModal dùng câu hỏi/đáp án/phản hồi có bước nhận thưởng.

Mỗi minigame start trong container, chỉ báo hoàn tất hợp lệ một lần, thất bại cho thử lại, đóng giữa chừng không tính thành công. Nội dung lịch sử lấy từ dữ liệu đặc tả; hoạt động qua suối/hang là gameplay, không trình bày như hướng dẫn an toàn du lịch thực tế.

Cleanup input/timer khi shutdown; quay lại scene đúng vị trí/checkpoint.

## Tiêu chí nghiệm thu

Đi hết ba chapter, thất bại rồi thử lại, rời khi popup đang mở, tải lại từng vùng; có đúng fragment tương ứng, không bị kẹt bản đồ hoặc nhân đôi listener.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module các chương atk, hang phượng hoàng và suối cửa tử cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
