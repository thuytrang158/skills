# Tin tức, cẩm nang và bài trải nghiệm

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **tin tức, cẩm nang và bài trải nghiệm**. Phạm vi: **WEB**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

02.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/dist/news-data.js`
- `WEB/dist/news.js`
- `WEB/dist/news.css`
- `WEB/dist/app.js: renderReviews và form bài trải nghiệm`
- `WEB/dist/assets/news/`

## Yêu cầu triển khai

Tạo globalThis.TRA_NEWS, renderNews và openNewsArticle. Giữ ba bài đầy đủ cùng thẻ liên kết Hồ Núi Cốc theo dữ liệu đang có; thẻ dẫn nguồn ngoài không được giả như bài toàn văn đã nhập. Mỗi bài có id, tiêu đề, ảnh, chuyên mục, tóm tắt, nội dung và nguồn khi có.

Sinh khu đánh giá chung: form tên hiển thị, tiêu đề, mức 1–5 sao và nội dung; lưu tra-reviews, giữ tối đa 30 bài và hiển thị tối đa 3 bài gần nhất. Nói rõ bài lưu riêng trên thiết bị, chưa đăng công khai. Khi chưa có đánh giá thật, dùng trạng thái rỗng.

Phân biệt tư liệu sự kiện đã biên tập với lịch tương lai. Không sinh tin mới hoặc xác nhận lịch lễ hội khi không có nguồn đầu vào. Encode/escape dữ liệu người dùng, liên kết ngoài có rel noopener.

## Tiêu chí nghiệm thu

Thẻ tin mở đúng nội dung hoặc đúng liên kết ngoài; form từ chối chuỗi chỉ có khoảng trắng; reload giữ bài tại máy; không xuất review giả trên catalogue.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module tin tức, cẩm nang và bài trải nghiệm cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
