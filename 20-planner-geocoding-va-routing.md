# Geocoding, tuyến đường và chia điểm theo ngày

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **geocoding, tuyến đường và chia điểm theo ngày**. Phạm vi: **PLANNER: cả hai bản**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17, 19.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/tools/places.py: geocode/retry_missing_coordinates`
- `PLANNER/src/tools/routing.py`
- `PLANNER/src/tools/clustering.py`

## Yêu cầu triển khai

Tra tọa độ Nominatim theo tên/alias/địa chỉ và phạm vi; xác thực match, kiểu kết quả và miền địa lý trước nhận. Cấu hình NOMINATIM_BASE_URL/USER_AGENT, cache, timeout, Retry-After và giới hạn nhịp như mã hiện có. Không tự thay GPS thiếu bằng tọa độ trung tâm tỉnh. Khi triển khai nhiều worker, limiter bộ nhớ một process không đủ.

calculate_route gọi OSRM theo thứ tự longitude,latitude, chuyển mét/giây sang km/phút; kiểm tra HTTP/JSON/route rỗng. Lỗi dùng haversine_fallback và ghi source Haversine Fallback, không nhận là tuyến đường lái xe đã xác minh.

group_places_by_days phân nhóm gần nhau theo số ngày, mỗi điểm xuất hiện đúng một lần và không mất điểm. Khi thiếu tọa độ, giữ hồ sơ trong danh sách nhưng chỉ đưa vào định tuyến nếu hợp lệ; báo lý do và cho thử lấy tọa độ lại.

Không dùng đoạn đường Leaflet minh họa của website làm quãng đường thực trong dự toán Planner. Các hệ số fallback là giả định của mã, không phải số đo thực địa.

## Tiêu chí nghiệm thu

Mock OSRM thành công/lỗi, GPS null, lat/lng đảo, địa danh trùng tên; kiểm tra mỗi điểm trong nhóm đúng một lần, không crash khi ít điểm hơn số ngày và nhãn fallback được giữ tới UI.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module geocoding, tuyến đường và chia điểm theo ngày cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
