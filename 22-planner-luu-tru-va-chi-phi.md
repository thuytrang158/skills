# Lưu trú, chi phí xác định và đơn vị tiền

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **lưu trú, chi phí xác định và đơn vị tiền**. Phạm vi: **PLANNER: cả hai bản**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17, 20, 21.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/tools/accommodation.py`
- `PLANNER/src/tools/cost_calculator.py`
- `PLANNER/src/tools/currency.py`
- `PLANNER/src/api.py: stays/finalize`

## Yêu cầu triển khai

search_accommodations kết hợp destination, stay_type, max_budget và preferred_area; parse JSON từ model có kiểm tra; trả AccommodationOption cùng disclaimer cần kiểm tra giá/chỗ trên nhà cung cấp. Model đề xuất không tương đương đã xác minh phòng còn trống.

Tính tiền bằng Python thuần calculate_trip_cost, không để LLM tự cộng. Lưu trú, di chuyển, ăn uống, hoạt động, dự phòng và tổng phải có đơn vị rõ ràng. Giữ breakdown_notes về số đêm, km và đơn giá.

Hiện cost_calculator dùng INR nội bộ, API đổi sang VND qua currency.py; /stays đổi budget VND sang INR và nightly_rate trả về VND, /finalize đổi về INR cho engine rồi chuyển kết quả ra VND. Tỷ lệ trong file là hằng tham khảo lịch sử, không phải tỷ giá trực tiếp. Không đổi hai lần hoặc gắn nhãn VND lên số INR.

Đặc điểm mã hiện tại: nights=max(days-1,1), vì vậy chuyến một ngày vẫn tính một đêm. Khi phục dựng, ghi rõ hành vi tương thích này; nếu được yêu cầu sửa logic nghiệp vụ thì đổi có kiểm thử, không âm thầm khẳng định một ngày đã có chi phí 0 đêm.

## Tiêu chí nghiệm thu

Kiểm tra tổng năm nhóm bằng tổng dự toán theo quy tắc làm tròn đã chọn (xem sai khác trong 00), đầu ra có currency VND, thử chuyển đổi hai chiều và một ngày/nhiều ngày; mock lưu trú không đúng bộ lọc không được trình bày là kết quả phù hợp.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module lưu trú, chi phí xác định và đơn vị tiền cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
