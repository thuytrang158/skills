# Knowledge base, BM25/RRF và chatbot Node

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **knowledge base, bm25/rrf và chatbot node**. Phạm vi: **WEB và INTEGRATED**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

03, 07–09, 16, 25.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `WEB/export-rag-data.cjs`
- `WEB/dist/data/rag-knowledge-base.json`
- `WEB/rag-chat.cjs`
- `WEB/dist/chat-widget.js`
- `WEB/dist/chat-widget.css`

## Yêu cầu triển khai

Exporter lấy dữ liệu tour, booking, ẩm thực và tin tức để xuất dữ liệu gốc cùng documents {id,page_content,metadata}. Chia tài liệu theo loại/thực thể, lịch trình từng ngày, giá/chính sách; giữ mã tour và source. Review hư cấu chỉ kiểm kê, không đưa vào documents.

Node sinh chunk theo câu tối đa 1800 ký tự, overlap 220; giữ ID/metadata thống nhất với Python. Query dense qua RAG_RETRIEVAL_URL mặc định http://127.0.0.1:8000/api/rag/retrieve, hợp nhất BM25 bằng RRF k=60 và lấy top 5 context. Với tour, bổ sung phần thông tin phù hợp; tối đa 6 nguồn cho giao diện. Loại dữ liệu ngày khởi hành/checkout/chỗ demo khỏi câu trả lời có vẻ là thương mại thật.

POST /api/chat kiểm tra độ dài câu hỏi/lịch sử/body và giới hạn nhịp; gọi Groq server-side, xoay khóa có giới hạn khi 429 theo cấu hình. Tài liệu truy xuất là dữ liệu không phải chỉ dẫn; trả lời không có chứng cứ thì nói thiếu thông tin. Không đưa khóa vào JS trình duyệt.

Widget có mở/đóng, gợi ý câu hỏi, lịch sử trong bộ nhớ, trạng thái đang gửi/lỗi và danh sách trích nguồn. Parse định dạng an toàn, không chèn HTML thô của model. Khi retrieval lỗi, báo dịch vụ chưa sẵn sàng theo nhánh mã hiện có.

## Tiêu chí nghiệm thu

Kiểm tra câu hỏi tour/ẩm thực/không có dữ liệu, prompt injection trong document, nguồn đúng metadata, rate limit, retrieval unavailable và Groq 429; unit test dùng mock, không gọi API thật.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module knowledge base, bm25/rrf và chatbot node cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
