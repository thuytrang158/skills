# Kiến trúc, cấu hình và khởi tạo

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **kiến trúc, cấu hình và khởi tạo**. Phạm vi: **Cả ba dự án**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

Đọc SKILL.md và 00-su-dung-va-pham-vi.md trước.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/package.json`
- `WEB/server.cjs`
- `WEB/.env.example`
- `GAME/package.json`
- `GAME/tsconfig.json`
- `GAME/vite.config.ts`
- `PLANNER/requirements.txt`
- `PLANNER/src/config.py`
- `PLANNER/src/__init__.py`
- `PLANNER/src/tools/__init__.py`
- `PLANNER/.env.example (nếu có)`

## Yêu cầu triển khai

Xây dựng ba ứng dụng: website tiếng Việt Trà Journey bằng HTML/CSS/JavaScript thuần và Node CommonJS; game Phaser 3 + TypeScript + Vite; AI Planner Python + FastAPI + Pydantic + LangGraph. Website chính không cần framework hoặc dependency npm bên ngoài. Game hiện dùng Phaser ^3.88.2, TypeScript ^5.7.3, Vite ^6.2.0; dùng package lock hiện có khi phục dựng.

Node nghe 127.0.0.1:4173; FastAPI 8000; Vite dev 3000. Tách static trong WEB/dist khỏi dữ liệu riêng WEB/.private. Lưu ý dist của website là mã nguồn giao diện đang được chỉnh trực tiếp, còn GAME/dist là đầu ra build.

Giữ cấu hình model bằng biến môi trường: GROQ_API_KEY, GROQ_API_KEY_1 đến _6, GROQ_MODEL, PLANNER_GROQ_MODEL, OLLAMA_MODEL, OLLAMA_BASE_URL. Hai bản Planner cần kiểm tra riêng cách đọc .env, không buộc chúng dùng chung khóa. Bản tích hợp đọc .env ở WEB. Sinh mẫu rỗng, không chép giá trị bí mật.

Tạo cấu trúc thư mục và entrypoint trước, sau đó sinh module theo đồ thị phụ thuộc. Nếu chưa có dependency Python, dùng requirements.txt đúng của bản được chọn; bản tích hợp bổ sung thư viện embedding/vector, bản độc lập không mặc định có chúng.

Tiện ích configure-groq-keys.py dùng nhập khóa ẩn, giữ giá trị cũ khi bỏ trống và chỉ ghi .env cục bộ, không in lại khóa. .gitignore loại .env, .private, môi trường ảo, node_modules và cache. Nếu giữ .openai/hosting.json thì coi là cấu hình đóng gói của môi trường hiện tại; không hardcode định danh tài khoản/hosting máy cũ hoặc tự xuất bản website.

## Tiêu chí nghiệm thu

Website khởi động khi chưa cấu hình AI; game có lệnh dev/build/test; Planner import được src.api sau khi cài môi trường. Các đường dẫn hoạt động ở bản clone khác, không chứa đường dẫn tuyệt đối của máy tác giả.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module kiến trúc, cấu hình và khởi tạo cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
