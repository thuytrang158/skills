# Minigame hái chè và chế biến

## Khi sử dụng

Dùng tài liệu này để sinh mới hoặc tái tạo phần **minigame hái chè và chế biến**. Phạm vi: **GAME**. Đọc quy ước đường dẫn và chế độ phục dựng trong [00-su-dung-va-pham-vi.md](00-su-dung-va-pham-vi.md).

## Phụ thuộc và đầu vào

27–30.

Nếu mã nguồn còn tồn tại, đọc các file tương ứng để giữ hợp đồng dữ liệu. Nếu sinh từ đầu, triển khai theo yêu cầu dưới đây; dữ liệu/ảnh gốc chưa có phải được báo là đầu vào còn thiếu.

## File cần sinh hoặc cập nhật

- `GAME/src/minigames/TeaHarvestMinigame.ts`
- `GAME/src/minigames/TeaProcessingMinigame.ts`

## Yêu cầu triển khai

TeaHarvest có tutorial/standard/advanced, phân biệt perfect/immature/long_shoot/overmature/damaged. Tạo búp và lá có hình thái, cho chọn/quan sát/hái, phản hồi đúng sai, thời gian, độ chính xác, điểm và bonusCoins. Callback trả {harvested,bonusCoins}; reward thực tế do scene/progression xử lý.

TeaProcessing thể hiện các giai đoạn hiện có qua thao tác trên lá/trạm, mức curl/dry/damaged và điều kiện chuyển bước. Clamp tham số, không cho bỏ qua bước bằng click liên tiếp. Outcome {firstBatch} giúp scene phân biệt lần đầu với luyện tập.

Hai minigame có start/destroy và quản lý timer/pointer/listener rõ ràng. Đóng popup hoặc chuyển scene phải dừng hết timer. Hỗ trợ chạm, nút đủ lớn và phản hồi không chỉ dùng màu.

Dùng ngôn ngữ mô phỏng học tập; không nhận quy trình điểm số là tiêu chuẩn sản xuất/đánh giá chất lượng chè thực tế.

## Tiêu chí nghiệm thu

Thử từng loại búp, hết giờ, hoàn thành, đóng giữa chừng, mở lại; callback chỉ chạy theo lần hoàn thành hợp lệ; chế biến chưa đạt không đi bước sau; không còn timer sau destroy.

## Câu lệnh giao cho AI

> Đọc SKILL.md, 00-su-dung-va-pham-vi.md và tài liệu này. Sinh hoặc hoàn thiện module minigame hái chè và chế biến cho đúng dự án được chọn. Triển khai code chạy được, nối với các phụ thuộc đã có, kiểm tra các tiêu chí nghiệm thu và báo kết quả thực tế. Giữ nguyên dữ liệu riêng và phần ngoài phạm vi.
