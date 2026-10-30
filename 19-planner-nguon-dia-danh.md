# Khám phá địa danh và thu thập My Thái Nguyên

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **khám phá địa danh và thu thập my thái nguyên**. Phạm vi: **PLANNER: cả hai bản**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

17; 18 khi bản tích hợp cần lọc ý định.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `PLANNER/src/tools/mythainguyen.py`
- `PLANNER/src/tools/places.py`
- `PLANNER/mythainguyen_places.json`
- `PLANNER/tests/test_place_sources.py`
- `PLANNER/tests/test_thai_nguyen_places.py`

## Yêu cầu triển khai

Sinh parser HTML/crawler My Thái Nguyên: lấy danh mục có giới hạn max_pages/max_details/deadline, lấy trang hồ sơ, parse tên, giới thiệu, địa chỉ, ảnh, nguồn và tọa độ. Cache request có TTL, timeout và dữ liệu nguồn. Không lấy tọa độ từ thẻ địa điểm liên quan/footer rồi gán cho hồ sơ hiện tại.

Tại Thái Nguyên, dùng danh mục nguồn trực tiếp, không gọi LLM để tự chọn/xếp hạng địa danh. Giữ hồ sơ không có tọa độ và lý do; chọn theo sở thích/ý định bằng logic xác định. Chuẩn hóa tên/alias, deduplicate theo id/URL/tên, giới hạn phạm vi địa lý và giữ provenance.

Với nơi khác, duy trì nhánh khám phá trong places.py theo mã nguồn và cấu hình hiện có. mythainguyen_places.json là đầu vào nguồn cục bộ khi có, không phải cơ sở dữ liệu booking. Không bịa ảnh, GPS, giá, giờ mở cửa hoặc nội dung trích nguồn.

Đầu ra search_places_osm và get_places_notice phải dùng được cho cả API lẫn CLI. Dùng fixture HTML offline để kiểm tra parser; không phụ thuộc trang đang thay đổi cho unit test.

## Tiêu chí nghiệm thu

Parser phân biệt hồ sơ chính với related content; dữ liệu trùng được gộp; timeout vẫn trả trạng thái giải thích; mọi địa điểm có nguồn hoặc được ghi rõ thiếu nguồn; Thái Nguyên không cần model để xếp điểm.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module khám phá địa danh và thu thập my thái nguyên cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
