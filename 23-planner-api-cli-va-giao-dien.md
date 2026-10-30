# REST API, đồ thị tác tử CLI và giao diện Planner

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **rest api, đồ thị tác tử cli và giao diện planner**. Phạm vi: **PLANNER: cả hai bản**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17–22; 25 chỉ cho RAG bản tích hợp.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/api.py`
- `PLANNER/src/main.py`
- `PLANNER/src/static/index.html`
- `WEB/dist/ai-planner/index.html`

## Yêu cầu triển khai

FastAPI phục vụ UI tại / và các POST /api/trip/initiate, /generate-itinerary, /modify, /stays, /finalize. Giữ request model và response shape riêng cho bản độc lập/tích hợp; lỗi đầu vào 422, lỗi nguồn/model có thông báo dễ hiểu. Không mở CORS production rộng chỉ vì bản dev đang dùng cấu hình rộng.

UI có 5 giai đoạn: yêu cầu → chọn điểm → lịch trình/duyệt/sửa → chọn lưu trú → hồ sơ cuối/chi phí/in hoặc lưu PDF bằng trình duyệt. Hiện đang tải, lỗi, thiếu GPS, nguồn tham khảo, nhãn dự toán; khóa thao tác phụ thuộc bước trước. Nội dung model render an toàn.

CLI dùng StateGraph với nodes requirements, destination, place_selection, routing, itinerary, human_gate, handle_modification, stay_agent, cost_calculator, final_planner. Gate có nhánh duyệt/sửa/start over; sửa quay về routing; sau lưu trú tính tiền và dossier. Phân biệt đây là đồ thị thực thi trong CLI; REST API gọi công cụ tương ứng, không mô tả mọi request đều đi qua cùng graph nếu mã không làm vậy.

Bản tích hợp đồng bộ UI được phục vụ tại WEB/dist/ai-planner/index.html và PLANNER/src/static/index.html khi thay đổi. Bản độc lập vẫn chạy riêng tại 8000. Hai Planner không chạy chung cổng 8000 cùng lúc.

## Tiêu chí nghiệm thu

Chạy trọn 5 bước với mock nguồn/model, thử quay lại sửa, print preview, số tiền VND; CLI qua được nhánh duyệt/sửa; UI website gửi cùng origin /api/trip thay vì hardcode host ngoài.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module rest api, đồ thị tác tử cli và giao diện planner cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
