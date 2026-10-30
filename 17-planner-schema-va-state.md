# Schema Pydantic và trạng thái Planner

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **schema pydantic và trạng thái planner**. Phạm vi: **PLANNER: cả độc lập và tích hợp**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

01; chọn bản Planner trong 00.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/schemas.py`
- `PLANNER/src/state.py`
- `PLANNER/src/api.py: request models`

## Yêu cầu triển khai

Sinh ExtractedTripRequirements, Place, DestinationPlaces, RouteSegment, ActivitySchedule, DaySchedule, TripItinerary, AccommodationOption và TripCostBreakdown theo kiểu hiện có. Ngày đi 1–30, số người >0; Place cho latitude/longitude null để vẫn giữ hồ sơ địa danh chưa có GPS.

Place giữ id/name/category/description/introduction/address/images/sources, trạng thái/lý do geocode, nguồn/attribution tọa độ và reference_data. RouteSegment có khoảng cách km, phút và nhãn nguồn. Itinerary có total_days và days với schedule theo giờ.

TripPlannerState TypedDict chứa messages, yêu cầu, places, selection, routes, itinerary, trạng thái duyệt, feedback, lưu trú, estimated_cost/final_trip_summary. Không tự trộn state Python với store tài khoản Node.

Bản tích hợp bổ sung Interest Literal, required_places/excluded_places/preferences/pace, trip_requirements và trường mô tả lý do đề xuất. Bản độc lập hiện không có toàn bộ các mở rộng này; chỉ thêm nếu yêu cầu nâng cấp. Request model của mỗi bản là hợp đồng API, không suy từ README cũ.

## Tiêu chí nghiệm thu

Pydantic từ chối ngày 0/31 và số người âm; chấp nhận địa danh thiếu tọa độ; JSON round-trip không mất nguồn; schema và tên trường frontend/API trùng nhau.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module schema pydantic và trạng thái planner cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
