# Dữ liệu đầu vào và ranh giới phục dựng

Tài liệu này giúp AI chuẩn bị dữ liệu để sinh dự án hoàn chỉnh. Không cần nạp dữ liệu của mọi nhóm khi chỉ làm một module nhỏ.

## Dữ liệu cần giữ theo nguồn

| Nhóm | Nguồn ưu tiên trong workspace gốc | Cách dùng |
| --- | --- | --- |
| Catalogue | WEB/dist/tours-data.js | Nguồn biên tập chính cho 10 tour và 13 điểm |
| Catalogue đã xuất | WEB/dist/data/tours.json; tour-catalogue.md | Có thể dùng khi không còn JS nguồn, rồi tái tạo schema |
| Booking | WEB/dist/data/tour-booking-config-v2.json | Toàn bộ giá, tùy chọn, lịch demo, chính sách và giới hạn |
| Mẫu yêu cầu booking | PROMPT_BOOKING_TOUR_DEMO_V2.md ở workspace gốc | Tham khảo nghiệp vụ; đối chiếu phần tài khoản/admin mới trong bộ skills |
| Ẩm thực/tin tức | WEB/dist/cuisine-data.js; news-data.js | Giữ bài viết, id, ảnh và nguồn |
| RAG | WEB/dist/data/rag-knowledge-base.json | Tái sinh từ nguồn bằng exporter; không biến JSON đã xuất thành nguồn sửa tay |
| Game | GAME/src/data/* | Quest, hội thoại, item, vùng, trà, shop, lake và achievement |
| Đặc tả game | DAC_TA_GAME_AI_TRAVEL_PLANNER.md ở workspace gốc | Tham khảo, đối chiếu state thực tế, vùng mở sẵn và chương bổ sung |
| Hồ sơ Planner | Mỗi PLANNER/mythainguyen_places.json | Dùng đúng dữ liệu của bản được chọn; bổ sung nguồn qua crawler |
| Ảnh website | WEB/dist/assets/ | Giữ file ảnh và chú thích; thư mục skills toàn Markdown không thay thế ảnh |
| Texture game | GAME/src/assets/pixelArtGenerator.ts; lakeArt.ts | Sinh bằng code procedural, không cần giả có sprite ảnh ngoài |

Bản JSON booking ở workspace gốc cũng có thể dùng làm đầu vào khi đúng phiên bản; không tự ghi đè bản đang chạy nếu hai file khác nhau. Knowledge base ở workspace gốc có thể là snapshot cũ; ưu tiên nguồn trong WEB và exporter của phiên bản đang làm.

## Hạt giống catalogue tối thiểu

Mã tour/id phải giữ TJ01/101 đến TJ10/110. Lấy tên tour, itinerary và giá chi tiết từ nguồn ưu tiên trên. Danh sách 13 điểm hiện có: Tân Cương, Hồ Núi Cốc, Hồ Ghềnh Chè, Chùa Hang, Hang Phượng Hoàng – Suối Mỏ Gà, ATK Định Hóa, Thác Khuôn Tát, Suối Cửa Tử, Hồ Ba Bể, Thảo nguyên Sam Chiêm, Hồ Bản Chang, Rừng trúc Yến Dương và Hang Thẳm Phầy. Dùng đúng ID trong catalogue nếu nguồn có cách viết tên hiển thị khác.

Không đồng nhất 13 điểm này với 5 điểm của bộ thiết kế theo quy tắc hoặc 8 vùng trong game. Ba danh mục phục vụ ba chức năng khác nhau.

## Tệp không lấy làm đầu vào sinh nội dung

Không sao chép .env thật, .private chứa tài khoản/booking, cookie/token, save cá nhân, node_modules, .venv, cache model hoặc Qdrant đang dùng. Chúng không thuộc bộ hướng dẫn nộp bài. Tạo file runtime mới bằng cơ chế bootstrap/khởi tạo khi cần và giữ dữ liệu thật ngoài bước kiểm thử.

## Nếu chỉ có các file skills

AI có thể dựng lại kiến trúc, giao diện, luồng nghiệp vụ và cấu trúc dữ liệu theo tài liệu. Để khớp nguyên bản, cần cung cấp thêm các dữ liệu biên tập và assets bên trên hoặc các snapshot công khai tương đương. Nếu chúng không có, AI phải báo cụ thể phần nào chỉ được tạo dữ liệu minh họa, không tự nhận nội dung/ảnh/giá là đã xác minh. Bộ skills không chứa bí mật hoặc bản sao dữ liệu khách hàng.

Việc thu thập lại từ web là một nhiệm vụ nguồn dữ liệu riêng; nội dung thu được có thể thay đổi theo thời điểm và không bảo đảm giống snapshot ban đầu.
