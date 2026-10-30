# Kiểu dữ liệu, hội thoại, nhiệm vụ và bản đồ vùng

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **kiểu dữ liệu, hội thoại, nhiệm vụ và bản đồ vùng**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

26; là hợp đồng cho 28–36.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/types/game.ts`
- `GAME/src/data/items.ts`
- `quests.ts`
- `dialogues.ts`
- `destinations.ts`
- `achievements.ts`
- `shopProducts.ts`
- `teaCultivars.ts`
- `teaBrewingProfiles.ts`
- `lake.ts`
- `regionAccess.mjs`
- `regionAccess.d.mts (các file sau đều trong src/data)`

## Yêu cầu triển khai

Sinh Direction, IItem, IQuestObjective/IQuest, IDialogueChoice/Node, INPCConfig, IDestination, ITourRecommendation, IAchievement, IGameSaveData, IRegionProgress và state pha trà/công thức. ID item/quest/objective/dialogue/scene là khóa bền vững, không suy từ text hiển thị.

Dữ liệu vùng: tan_cuong, ho_nui_coc, atk_dinh_hoa, hang_phuong_hoang, suoi_cua_tu, thai_hai, den_duom, bao_tang_van_hoa. Giữ REGION_SCENE_KEYS, REGION_IDS, SUGGESTED_ROUTE và 7 MEMORY_FRAGMENT_IDS trong regionAccess.mjs với declaration TypeScript tương ứng.

Bảy mảnh ký ức: tea_culture, legend, history, nature, exploration, people, tradition với tiền tố fragment_. Bảo tàng là vùng riêng bổ sung, không tự tạo mảnh thứ tám.

Mọi NPC trỏ tới hội thoại và quest tồn tại, reward trỏ item/achievement tồn tại, destination trỏ scene có đăng ký. Nội dung văn hóa lấy từ dữ liệu/đặc tả sẵn có, tách thông tin đời thực khỏi hư cấu gameplay. Tạo dữ liệu từng nhóm trước khi code scene sử dụng.

## Tiêu chí nghiệm thu

Không có ID trùng/tham chiếu gãy; registry đủ 8 vùng; đủ 7 fragment; declaration khớp exports .mjs; build TypeScript phát hiện kiểu sai.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module kiểu dữ liệu, hội thoại, nhiệm vụ và bản đồ vùng cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
