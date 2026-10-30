# Dense retrieval BGE-M3 và Qdrant local

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **dense retrieval bge-m3 và qdrant local**. Phạm vi: **Chỉ INTEGRATED, không có trong Planner độc lập hiện tại**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17, 24.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `INTEGRATED/src/rag_retrieval.py`
- `INTEGRATED/src/api.py: rag routes/startup`
- `INTEGRATED/requirements.txt`
- `WEB/.private/qdrant (runtime)`

## Yêu cầu triển khai

Sinh BgeM3VectorIndex, initialize_rag_index, retrieve_rag_chunks và rag_index_health. Đọc knowledge base do WEB export, build chunk theo cùng chuẩn Node; embedding dense bằng BAAI/bge-m3 và lưu Qdrant local. Không mô tả là dùng sparse/multi-vector của BGE-M3 nếu mã chỉ dùng dense.

Fingerprint dữ liệu, model và cấu hình chunk; dùng lại index không đổi, rebuild khi cần. Đường dẫn model/vector store cấu hình bằng BGE_M3_MODEL và RAG_VECTOR_STORE_PATH. Cache mô hình hợp lý và bảo vệ khởi tạo đồng thời; không mở nhiều client ghi cùng Qdrant local thiếu kiểm soát.

GET /api/rag/health và POST /api/rag/retrieve với query/limit; trả chunk ID/text/metadata/score mà Node có thể đối chiếu. Startup thử warm index, lỗi có thể hoãn và retry có kiểm soát, không làm toàn bộ Planner ngừng hoạt động; retrieval thất bại trả 503.

Lần đầu cần tải mô hình và RAM, không đưa model weights vào repo. Không tự thêm chức năng này cho Planner độc lập khi nhiệm vụ chỉ phục dựng phiên bản đó.

## Tiêu chí nghiệm thu

Với model/vector store mock: dữ liệu đổi gây rebuild, dữ liệu không đổi tái sử dụng index, metadata giữ nguyên; health phân biệt chưa sẵn sàng và ready; không cần tải model lớn để chạy unit test.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module dense retrieval bge-m3 và qdrant local cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
