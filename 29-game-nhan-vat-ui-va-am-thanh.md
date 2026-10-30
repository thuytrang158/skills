# Nhân vật, HUD, hội thoại, shop và âm thanh

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **nhân vật, hud, hội thoại, shop và âm thanh**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

26–28.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/entities/Player.ts`
- `GAME/src/entities/NPC.ts`
- `GAME/src/ui/UIManager.ts`
- `ShopModal.ts`
- `VillageGuide.ts (src/ui)`
- `GAME/src/systems/AudioManager.ts`

## Yêu cầu triển khai

Player di chuyển 4 hướng bằng WASD/mũi tên và điều khiển cảm ứng, animation theo hướng, giới hạn map và va chạm. NPC có cấu hình, sprite, vùng tương tác và hội thoại theo trạng thái quest; E/Space và nút chạm thực hiện tương tác phù hợp.

UIManager điều phối HUD, tên/xu, nhật ký, inventory, achievement, destination card, dialogue branching, toast, modal/minigame và world map. Khi modal mở phải khóa điều khiển nhân vật; đóng thì khôi phục và xóa trạng thái phím/touch đang giữ. Không đăng ký listener trùng mỗi lần mở.

Shop dùng shopProducts và InventoryManager, kiểm tra đủ xu trước mua, phản ánh kho sau giao dịch; tiền chỉ trong game. VillageGuide giúp tìm khu/nhiệm vụ và điểm tương tác.

AudioManager singleton dùng Web Audio procedural, có mute/resume và các âm footsteps/nhặt đồ/nhiệm vụ/chè. Hủy timer/listener khi scene shutdown; không tự tạo AudioContext mới ở mỗi tương tác.

## Tiêu chí nghiệm thu

PC/mobile đi và tương tác đúng; modal không cho nhân vật chạy phía sau; mở shop liên tục không trừ tiền nhiều lần; thiếu xu không mua được; bật/tắt âm và resume tab hoạt động.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module nhân vật, hud, hội thoại, shop và âm thanh cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
