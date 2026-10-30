# Save, inventory, quest và tiến trình

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **save, inventory, quest và tiến trình**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/systems/SaveManager.ts`
- `InventoryManager.ts`
- `QuestManager.ts`
- `ProgressionService.ts`
- `RegionRegistry.ts (đều src/systems)`

## Yêu cầu triển khai

SaveManager dùng thai_nguyen_quest_save_v1, version 1; load JSON lỗi/không tương thích trả mặc định; merge field/objective mới theo ID mà không mất objective hoàn thành cũ. Mặc định có nhật ký, giỏ chè, tiền xứ trà; 120 xu và các trường tiến trình/hộ chiếu/công thức.

Lưu ý hành vi hiện tại: getDefaultSaveData mở toàn bộ REGION_IDS, migration cũng bổ sung mọi vùng. regionAccess vẫn có logic xét mảnh trà cho save bị giới hạn. Khi phục dựng không tự đổi trò chơi thành tuyến bắt buộc khóa từng vùng.

Inventory quản lý số lượng, coin, thêm/bớt và event listeners; không âm số lượng. Quest quản lý locked/available/active/completed, đếm mục tiêu và completion. ProgressionService ghi checkpoint, trao fragment/item/achievement/hộ chiếu một lần và đồng bộ state; minigame chỉ báo outcome.

RegionRegistry là nơi tra scene, init runtime, persist và chuyển vùng. Fade kết thúc có callback dự phòng nhưng chỉ start scene một lần. Đủ 7 mảnh phát thai-nguyen-journey-ending một lần qua journeyEndingPresented. Không reset toàn bộ tiến trình khi mở chapter khác.

## Tiêu chí nghiệm thu

Chơi lại hoạt động không nhân đôi thưởng; migration giữ quest hoàn thành; localStorage lỗi không crash; 8 vùng truy cập được theo save mặc định; đủ mảnh phát kết thúc đúng một lần.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module save, inventory, quest và tiến trình cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
