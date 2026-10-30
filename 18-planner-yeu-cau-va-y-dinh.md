# Thu thập yêu cầu và ý định chuyến đi

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **thu thập yêu cầu và ý định chuyến đi**. Phạm vi: **PLANNER; mở rộng chỉ có ở bản tích hợp**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17, 01.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/main.py: requirements_agent_node`
- `INTEGRATED/src/tools/requirements.py`
- `INTEGRATED/src/tools/intent.py`
- `INTEGRATED/tests/test_requirements_agent.py`
- `INTEGRATED/tests/test_trip_intent.py`

## Yêu cầu triển khai

Bản độc lập: thu thập destination, number_of_days, number_of_travelers, budget_per_day, transportation_preference và interests từ CLI/API. Hỏi bổ sung trường thiếu thay vì sinh lịch trình khi đầu vào không đủ.

Bản tích hợp: extract_trip_requirements(text,context) gọi model, lấy JSON có kiểm tra Pydantic, chuẩn hóa chuỗi rỗng/null/unknown; trả lỗi có kiểu RequirementsOutputError khi output không hợp lệ. requirements_model_info mô tả provider/model, không chứa API key.

Tách required_places, excluded_places, preferences và pace relaxed/balanced/active. intent.py chuẩn hóa tên tiếng Việt, đối chiếu địa danh, đánh dấu required_for, rank_for_intent, requirement_report và validate_selection. Báo thiếu/xung đột ràng buộc cho người dùng; không lặng lẽ bỏ địa danh bắt buộc.

Ngữ cảnh và yêu cầu bổ sung phải hợp nhất có chủ đích; yêu cầu mới rõ ràng của khách thay thế trường cũ tương ứng, không xóa các trường không liên quan. Lịch trình sau sửa vẫn phải đáp ứng các ràng buộc còn hiệu lực.

## Tiêu chí nghiệm thu

Thử hội thoại tiếng Việt nhiều lượt, yêu cầu thêm/bỏ điểm, null, số ngày sai, output model không phải JSON; dùng mock model, không tiêu quota trong unit test.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module thu thập yêu cầu và ý định chuyến đi cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
