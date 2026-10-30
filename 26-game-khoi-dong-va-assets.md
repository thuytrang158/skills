# Khởi động Phaser, menu và tài nguyên pixel

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **khởi động phaser, menu và tài nguyên pixel**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

01; 27–29 cung cấp runtime/data/UI.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/index.html`
- `GAME/src/main.ts`
- `GAME/src/style.css`
- `GAME/src/scenes/BootScene.ts`
- `GAME/src/scenes/MainMenuScene.ts`
- `GAME/src/assets/pixelArtGenerator.ts`
- `GAME/src/assets/lakeArt.ts`

## Yêu cầu triển khai

Phaser AUTO, canvas 960x540, pixelArt true, antialias false, roundPixels true, Scale.FIT/CENTER_BOTH, Arcade Physics không trọng lực. Khởi tạo UI trước engine; đăng ký toàn bộ scene bằng đúng key.

BootScene tạo textures procedural và animation player/NPC trước khi vào menu. Texture key, frame và scale phải thống nhất với entities/scenes; tái sử dụng generator hiện có thay vì đòi assets ngoài chưa được cung cấp. Lake art tách riêng.

Menu có bắt đầu mới, tiếp tục theo save, đặt tên và truy cập cài đặt/hướng dẫn phù hợp. Không xóa save hiện có khi chỉ mở menu. Khi bắt đầu mới, tạo state mặc định và vào Tân Cương; tiếp tục trở lại đúng region/checkpoint.

Expose __THAI_NGUYEN_QUEST__ cho tích hợp/debug nếu giữ API hiện có. Âm thanh chỉ init/resume sau click/keydown/touchstart đầu tiên. Giao diện tiếng Việt theo phong cách pixel, đọc được trên mobile.

## Tiêu chí nghiệm thu

npm run build qua TypeScript; boot không thiếu texture; menu tiếp tục đúng checkpoint; resize giữ tỉ lệ; trình duyệt chưa tương tác không báo lỗi autoplay.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module khởi động phaser, menu và tài nguyên pixel cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
