# Chương Hồ Núi Cốc và hành trình trên hồ

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **chương hồ núi cốc và hành trình trên hồ**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27–29.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/scenes/HoNuiCocScene.ts`
- `GAME/src/systems/LakeJourney.ts`
- `GAME/src/ui/LakeFieldGuide.ts`
- `LakeExperience.ts`
- `lake.css (src/ui)`
- `GAME/src/data/lake.ts`
- `GAME/src/assets/lakeArt.ts`
- `GAME/src/minigames/LakeLegendMinigame.ts`

## Yêu cầu triển khai

Sinh cảnh hồ, bến, điểm dừng, đường đi và cơ chế lên thuyền/di chuyển/xuống thuyền. Dùng DockId/LakeStopId từ data; kiểm tra walkable, vị trí bến và trạng thái trước chuyển động. Không đưa người chơi xuống nước khi chưa có đường đi hợp lệ.

LakeJourney sở hữu visitedStops, completedActivities và selections; initialize phục hồi, record/setSelection/visitStop/complete cập nhật bền vững rồi syncQuest. UI field guide/experience phản ánh cùng state, không tạo một bộ mục tiêu riêng.

Hoạt động truyền thuyết dùng LakeLegendMinigame, nội dung phân biệt chuyện kể với thông tin tham quan. Hoàn tất điều kiện chapter mới nhận fragment_legend và hộ chiếu qua service; reload hoặc tương tác lại không tạo thưởng trùng.

Đóng panel/đổi vùng reset vector cảm ứng, dừng vận tốc, cleanup listener/animation; lưu checkpoint cả khi đang khám phá. Dùng lakeArt procedural và CSS riêng để không làm thay đổi style modal toàn game.

## Tiêu chí nghiệm thu

Thử lên/xuống ở từng bến, điều hướng nhanh, PC/touch, reload giữa chapter, hoàn thành minigame rồi mở lại; quest đồng bộ với guide và fragment chỉ có một.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module chương hồ núi cốc và hành trình trên hồ cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
