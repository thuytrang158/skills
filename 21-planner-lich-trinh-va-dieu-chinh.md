# Sinh lịch trình và vòng duyệt/điều chỉnh

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **sinh lịch trình và vòng duyệt/điều chỉnh**. Phạm vi: **PLANNER: cả hai bản**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17–20.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/api.py: build_itinerary, generate/modify`
- `PLANNER/src/tools/modification.py`
- `PLANNER/src/main.py: itinerary_agent_node/human gate`

## Yêu cầu triển khai

Xây lịch trình theo nhóm ngày và thời gian di chuyển, giữ đúng số ngày, điểm đã chọn và nguồn tuyến. Tạo schedule theo giờ có khoảng nghỉ/ăn và đệm; không để hoạt động chồng giờ hoặc ngày rỗng vô cớ. Bản tích hợp truyền trip_requirements vào khâu kiểm tra và dựng lịch.

Cho khách Accept / Modify / Start Over. Modify nhận feedback và selected_places/available_places, dùng modify_selection_with_llm để thêm/bỏ/chỉnh selection, xác thực đầu ra rồi tính lại routes và lịch. Không trả lịch cũ khi yêu cầu đã thay đổi; cũng không chấp nhận địa điểm do model tự bịa không có nguồn.

API trả cấu trúc itinerary/routes và trạng thái để UI hiển thị; không tự suy rằng HTTP thành công nghĩa là người dùng đã duyệt. Trong CLI, human_itinerary_gate_node quyết định đi tiếp lưu trú, quay lại sửa hoặc bắt đầu lại.

Nếu ràng buộc quá nhiều điểm cho thời gian hiện có hoặc điểm bắt buộc bị loại, bản tích hợp trả báo cáo rõ ràng để khách điều chỉnh.

## Tiêu chí nghiệm thu

Mock model: thêm/bỏ điểm có tác dụng, điểm bắt buộc không mất, JSON lỗi được xử lý, routes được tính lại, luồng từ chối/đồng ý chạy đúng và số ngày lịch bằng đầu vào.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module sinh lịch trình và vòng duyệt/điều chỉnh cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
