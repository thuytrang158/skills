# Cách dùng và phạm vi của bộ skills

## Mục đích

Bộ tài liệu hướng dẫn AI **sinh code triển khai**, cấu hình, dữ liệu, giao diện và kiểm tra cho cả ba dự án trong workspace. Đây không chỉ là bản mô tả chức năng. Các yêu cầu được đối chiếu mã nguồn tại thời điểm lập bộ tài liệu ngày 30/10/2026.

Giữ tất cả file Markdown trong cùng một thư mục `skills`. `SKILL.md` là điểm vào và các file đánh số là tài liệu theo module. Cấu trúc phẳng này đáp ứng yêu cầu gom các file `.md`; không cần tạo 37 thư mục con. Nếu môi trường AI không tự nhận skills, yêu cầu AI đọc `skills/SKILL.md` và tài liệu module cụ thể. Nếu cài như một skill có cơ chế tự phát hiện, dùng thư mục tên `tra-journey-projects` chứa nguyên bộ file, theo cấu hình của công cụ bạn đang sử dụng.

## Quy ước đường dẫn

Tất cả ký hiệu dưới đây tính từ thư mục chung chứa ba dự án; phải đổi thành đường dẫn tương ứng ở máy mới.

| Ký hiệu | Thư mục | Vai trò |
| --- | --- | --- |
| WEB | `travel-web/` | Website Node, booking, tài khoản, admin, chatbot |
| GAME | `game12/` | Mã nguồn game Phaser/TypeScript |
| STANDALONE | `Multi-Agent-AI-Travel-Planner/` | AI Planner độc lập |
| INTEGRATED | `travel-web/Multi-Agent-AI-Travel-Planner/` | Planner mở rộng cho website và RAG |
| PLANNER | STANDALONE hoặc INTEGRATED | Chọn rõ một bản trước khi làm module 17–23 |

Một danh sách rút gọn như `GAME/src/systems/A.ts; B.ts` nghĩa là cả hai file cùng thư mục `GAME/src/systems/`. Bản đồ file 38 luôn dùng đường dẫn đầy đủ để tra chính xác.

## Hai bản AI Planner

Cả hai có FastAPI, giao diện 5 bước, CLI LangGraph, nguồn địa danh, geocoding/routing, lưu trú và dự toán. Bản INTEGRATED bổ sung `src/tools/requirements.py`, `src/tools/intent.py`, `src/rag_retrieval.py`, request_text/trip_requirements và hai bài kiểm thử yêu cầu/ý định. STANDALONE hiện không có các file này. Không sao chép đè qua lại để làm hai bản giống nhau.

Mỗi bản có requirements.txt, tests và UI riêng. Chỉ chạy một FastAPI trên cổng 8000 tại một thời điểm. Website cần bản INTEGRATED cho chatbot dense retrieval; chạy STANDALONE sẽ không tự có `/api/rag/retrieve`.

## Chế độ sinh dự án

- **Từ mã đang có:** đọc file liên quan, giữ tên/export/schema, bổ sung phần thiếu. Không chỉ mô tả lại rồi dừng.
- **Từ thư mục trống:** khởi tạo theo module 01, dùng hợp đồng trong 39, sinh đầy đủ phần phụ thuộc. Những tên hàm ở hướng dẫn là giao diện cần tạo, không phải giả định file đã tồn tại.
- **Phục dựng giống nguyên bản:** cần dữ liệu, ảnh và nội dung biên tập đầu vào nêu ở 40. Chỉ từ các hướng dẫn này có thể tái tạo kiến trúc/chức năng, nhưng không khôi phục chính xác ảnh gốc hay toàn bộ bài viết không được cung cấp. Không bịa dữ liệu để tuyên bố đã khôi phục nguyên bản.

## Thứ tự triển khai

1. Nền tảng: 01; website: 02–03; Planner: 17; game: 26–28.
2. Website nội dung: 04–08. Backend booking: 09–10, 12, 14. Sau đó giao diện 11, 13, 15 và server 16.
3. Planner riêng: 18–22 rồi 23, thực hiện cho STANDALONE và INTEGRATED theo khác biệt đã ghi. Module 18 chỉ thêm các file mở rộng cho INTEGRATED.
4. RAG website: 24 và 25 làm thành một nhóm để thống nhất chunk ID/metadata, sau đó nối vào server/widget. Module 25 chỉ có ở INTEGRATED.
5. Game: 29, các minigame 31–32, chương 30; tiếp theo 33–35, cuối cùng tích hợp/build 36. Scene có thể dựng sau khi lớp phụ thuộc tương ứng đã có.
6. Chạy kiểm tra/bàn giao 37 và đối chiếu bản đồ 38. Dùng 39 để chốt hợp đồng giữa các phần, 40 để chuẩn bị dữ liệu.

Khi chỉ làm một module, không cần sinh lại cả hệ thống hoặc chỉnh các phần không liên quan. Khi làm toàn bộ, theo dõi tiến độ theo từng module và hoàn tất các bước nối API/UI, không coi file scaffold trống là hoàn thành.

## Sai khác và lỗi quan sát được cần xử lý có chủ đích

- README và test booking cũ có chỗ vẫn mong tạo đơn không đăng nhập, `unpaid/simulated_paid` và tự xác nhận sau thanh toán; mã hiện tại yêu cầu tài khoản, admin duyệt và dùng `not_paid/paid/failed`. Sinh bộ test theo hợp đồng hiện tại; không đổi hệ thống ngược lại chỉ để qua test cũ.
- Trong `demo-booking-api.cjs`, `customerPay` gọi `save()` nhưng hàm lưu kho booking hiện tên `saveState()`. Khi sinh mới phải dùng đúng hàm lưu; khi nhiệm vụ là sửa module này, kiểm tra và sửa lỗi đó rồi thử persistence bằng store tạm. Bộ tài liệu không tự sửa ứng dụng gốc.
- Đổi lịch còn dùng một số trạng thái cũ; xem lại chuyển trạng thái và inventory trước khi gọi luồng này hoàn chỉnh. Quyết định dùng bộ tên trạng thái nhất quán trong module 10/39, không thêm tên tùy hứng.
- Engine chi phí dùng INR và ít nhất một đêm; các chi phí sau khi đổi VND từng phần có thể chênh vài đồng so với đổi tổng vì làm tròn. Nếu nâng cấp quy tắc làm tròn, chọn rõ làm tròn từng khoản rồi cộng hoặc giữ tương thích và hiển thị chênh lệch; kiểm tra đúng quy tắc đã chọn.
- Game mặc định mở cả 8 vùng; số vùng không đồng nghĩa số mảnh ký ức. Không suy từ mô tả cốt truyện rằng bắt buộc khóa tuần tự.
- Các hướng dẫn kiểm thử là tiêu chí cho code sẽ sinh, không phải khẳng định mọi kiểm thử của dự án hiện tại đã vượt qua.

## Mẫu yêu cầu sinh toàn hệ thống

> Đọc skills/SKILL.md, 00-su-dung-va-pham-vi.md, 38-ban-do-file-va-module.md, 39-hop-dong-du-lieu-va-api.md và 40-du-lieu-dau-vao.md. Hãy xây dựng đủ ba dự án travel-web, game12, Multi-Agent-AI-Travel-Planner; giữ bản Planner tích hợp trong travel-web là một biến thể riêng. Triển khai theo thứ tự module, sinh code chạy được và kiểm tra từng nhóm. Dùng dữ liệu/ảnh nguồn được cung cấp; báo rõ đầu vào còn thiếu. Hoàn thành cả tích hợp website–game–Planner, không chỉ tạo giao diện hoặc file rỗng. Cuối cùng báo cách chạy, các kiểm tra đã thực hiện và giới hạn còn lại.
