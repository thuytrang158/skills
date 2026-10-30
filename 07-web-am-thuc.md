# Danh mục, bài giới thiệu và tương tác ẩm thực

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **danh mục, bài giới thiệu và tương tác ẩm thực**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

02.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/cuisine-data.js`
- `WEB/dist/cuisine.js`
- `WEB/dist/cuisine.css`
- `WEB/dist/assets/cuisine/`

## Yêu cầu triển khai

Tạo globalThis.TRA_CUISINE với 13 món theo dữ liệu gốc, phân nhóm Bánh dân gian, Món chính & Gỏi nướng, Danh trà & Thức quà. Mỗi món có id ổn định, tên, nhóm, mô tả, ảnh, nội dung giới thiệu và dữ liệu liên quan theo schema đang dùng.

Sinh thẻ món, bộ lọc nhóm, dialog/bài chi tiết, nút thích và form nhận xét. Tách dữ liệu khỏi hàm render. Dùng các khóa tra-cuisine-likes và tra-cuisine-reviews; thích/nhận xét chỉ phản ánh dữ liệu trên thiết bị, không tự nhận là tương tác toàn hệ thống.

Escape nội dung do người nhập, giới hạn độ dài, có empty state và fallback nếu lưu thất bại. Bảo đảm mở bài món ăn không xung đột dialog tour. Dùng ảnh đúng món và giữ tên file hiện có để exporter RAG tham chiếu được.

## Tiêu chí nghiệm thu

Hiện đủ 13 món, lọc từng nhóm đúng, mở/đóng chi tiết, thích bỏ thích và nhận xét còn sau reload; chuỗi HTML nhập vào chỉ hiển thị như văn bản.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module danh mục, bài giới thiệu và tương tác ẩm thực cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
