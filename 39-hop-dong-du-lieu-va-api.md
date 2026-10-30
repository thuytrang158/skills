# Hợp đồng dữ liệu và API giữa các module

Đọc cùng module nghiệp vụ. Ví dụ JSON bên dưới là hình dạng payload; ngày và ID lựa chọn phải lấy từ cấu hình đang sử dụng, không cố định vào ngày đã qua. Không đưa khóa/token phiên thật vào ví dụ.

## Website: quan hệ danh mục

- `TRA_CATALOG.tours[].id`: số định danh tour, hiện 101–110.
- `.code`: TJ01–TJ10; booking liên kết bằng `tourId` và `tourCode` cùng khớp.
- `.destinationIds`: tham chiếu danh mục điểm đến; `.places` là tên dùng hiển thị/lọc.
- `.itinerary[]`: mỗi ngày có title, meals, stay, activities[]; mỗi activity có time/title/description.
- `TRA_CUISINE` và `TRA_NEWS` là dữ liệu riêng, exporter RAG đưa vào cùng knowledge base bằng metadata loại tài liệu.
- Không dùng ID region dạng `tan_cuong` của game thay trực tiếp destinationId dạng `tan-cuong` của website; cần mapping rõ ràng.

## Booking: lựa chọn và tạo đơn

Ví dụ selection theo fixture TJ01 hiện có:

```json
{
  "tourCode": "TJ01", "tourId": 101, "date": "2026-11-07",
  "adults": 2, "children": 1, "infants": 0,
  "transportId": "shuttle", "pickupId": "thai-nguyen-center",
  "roomId": "", "rooms": 0, "addonIds": [], "promoCode": ""
}
```

1. `GET /api/demo/catalog` trả cấu hình và tours.
2. `GET /api/demo/departures?tourCode=TJ01` trả departures có `availableSeatsDemo`, `seatStatus`, `canSelect`.
3. `POST /api/demo/quote` nhận selection, trả `{quote:{lineItems,totalVND,depositVND,balanceVND,discountVND,warnings,needsQuote,isComplete}}`.
4. `POST /api/demo/holds` nhận selection, trả `holdToken`, `expiresAt`, `availableSeatsDemo`, `quote`.
5. Khách đăng nhập rồi `POST /api/demo/bookings` với payload sau:

```json
{
  "holdToken": "<hold trả từ API>",
  "idempotencyKey": "<mã ngẫu nhiên riêng cho lần gửi>",
  "selection": {},
  "lead": {"fullName":"Khách thử nghiệm","phone":"0912345678","email":"demo@example.test"},
  "travellers": [],
  "paymentMethod": "pay_later",
  "consents": {"privacy":true,"policies":true}
}
```

Thay selection bằng object đầy đủ từ bước báo giá. `travellers` tùy chọn; nếu nhập một người thì họ tên/ngày sinh phải hợp lệ và khớp nhóm tuổi. Hóa đơn có các trường invoiceRequested/companyName/taxCode/invoiceEmail/companyAddress trong lead, kiểm tra theo module 10. Tạo mới trả HTTP 201 với `{booking,ownerToken}`; lặp idempotency hợp lệ không tạo đơn thứ hai. ownerToken chỉ dùng qua `X-Booking-Token` với API đọc/hủy/đổi đơn, không đưa URL/localStorage.

Luồng chính hiện tại:

```text
pending_review_demo hoặc pending_payment
  ├─ admin approve → confirmed, paymentStatus vẫn not_paid
  │                    ├─ customer payment success → paid
  │                    └─ customer payment failure → failed → có thể thử lại
  └─ admin reject → rejected + rejectionReason + trả chỗ
```

`bookingStatus` và `paymentStatus` là hai trường khác nhau. Khi hủy đơn dùng trạng thái kết thúc `cancelled_demo` theo chính sách hiện có. Không chuyển `paid` bằng dữ liệu người dùng tự khai khi chưa xác thực quyền/điều kiện. API thanh toán chỉ mô phỏng, không liên kết ngân hàng.

## Tài khoản và admin

| Nhóm | Đường dẫn | Bảo vệ |
| --- | --- | --- |
| Khách | `/api/customer/register`, `/login`, `/session`, `/logout` | Cookie tour_customer và CSRF cho thao tác ghi sau đăng nhập |
| Đơn khách | `/api/customer/bookings`, `/notifications` | Chỉ customerId lấy từ phiên |
| Trả cọc | `POST /api/customer/bookings/:code/payment` với `{outcome:"success"}` hoặc failure | Đơn đúng chủ, confirmed, chưa paid, CSRF |
| Admin | `/api/admin/login`, `/session`, `/logout` | Cookie tour_admin, phiên 8 giờ |
| Duyệt | `POST /api/admin/orders/:code/decision` với `{decision:"approve"}` hoặc `{decision:"reject",reason:"..."}` | Admin + CSRF, lý do từ chối đủ độ dài |
| Quản lý | `/api/admin/dashboard`, `/orders`, `/users`, `/password`, `/audit` | Admin, phương thức ghi cần CSRF |

Hai API tài khoản dùng header `X-CSRF-Token` theo mã nguồn hiện có; cookie/CSRF lấy từ login/session, không dùng token hardcode. Mỗi response công khai phải loại salt/hash/token nội bộ.

## Planner: API độc lập và tích hợp

| Endpoint POST | Đầu vào chính | Đầu ra chính |
| --- | --- | --- |
| `/api/trip/initiate` | destination, number_of_days, number_of_travelers, budget_per_day, transportation_preference, interests | available_places, thông tin chuyến đi, status |
| `/api/trip/generate-itinerary` | destination, number_of_days, transportation_preference, selected_places | selected_places, routes, itinerary |
| `/api/trip/modify` | feedback, available_places, selected_places, destination, number_of_days, transportation_preference | selection và itinerary/routes đã tính lại |
| `/api/trip/stays` | destination, stay_type, max_budget VND, preferred_area | accommodation_options, giá/nghỉ đêm VND |
| `/api/trip/finalize` | destination, number_of_days, number_of_travelers, transportation_preference, itinerary, selected_accommodation, routes, selected_places | cost_breakdown, itinerary, stay, status FINALIZED và metadata |

Bản INTEGRATED thêm `request_text` tại initiate và `trip_requirements` cho các bước sau; stays thêm selected_places. Init có thể trả thông tin yêu cầu/trạng thái cần bổ sung; giữ response đúng code thay vì luôn coi đã tìm được điểm. interest của bản tích hợp thuộc 6 giá trị: Trekking & Adventure; Parks & Leisure; Heritage & Architecture; Spiritual & Wellness; Food & Culinary; Shopping & Bazaars.

```json
{
  "id":"source-stable-id", "name":"Tên địa danh", "category":"Heritage & Architecture",
  "description":"Mô tả ngắn", "latitude":null, "longitude":null,
  "introduction":"Nội dung nguồn", "images":[], "sources":[],
  "geocoding_status":"unavailable", "geocoding_reason":"Chưa có tọa độ phù hợp",
  "reference_data":{}
}
```

```json
{
  "destination":"Thái Nguyên", "total_days":1,
  "days":[{"day_number":1,"theme":"Khám phá xứ Trà","schedule":[
    {"time":"09:00","activity":"Tên địa danh đã chọn","details":"Mô tả hoạt động dự kiến"}
  ]}]
}
```

RouteSegment giữ origin_name/destination_name/distance_km/duration_minutes/source. Không đưa địa danh GPS null vào OSRM. Mọi số tiền UI/API phải có currency VND; engine INR nội bộ thực hiện chuyển đổi một lần ở biên API.

## RAG chỉ thuộc bản tích hợp

Knowledge base có `documents:[{id,page_content,metadata}]` và dữ liệu gốc; metadata giữ loại thực thể, mã tour, nguồn theo exporter. Node/Python thống nhất quy tắc tạo chunk ID.

- `GET /api/rag/health`: tình trạng index.
- `POST /api/rag/retrieve`: `{query:"Tour nào phù hợp gia đình?",limit:12}`; response `{matches:[{id,page_content,metadata,score}],model,chunk_count}`; giữ chunk ID thống nhất với Node.
- `POST /api/chat`: `{message:"...",history:[{role:"user",content:"..."}]}`; giới hạn lịch sử/độ dài theo handler. Response `{answer,citations,model,retrieval,chunkCount}`; citations là `{title,url}` với url có thể null. Khi không có kết quả phù hợp có thể chỉ trả answer/citations; khi lỗi trả `{error}` cùng HTTP status.

## Game: lưu và sự kiện

Save key `thai_nguyen_quest_save_v1`, version 1. Lưu currentRegion/playerCoords, inventory, quests/activeQuestId/completedQuestIds, collectedFragmentIds/unlockedRegionIds, achievements, teaHarvestHighScore, coins, passportStamps, regionProgress, trạng thái/lịch sử pha trà, công thức và journeyEndingPresented. `regionProgress[regionId]` có visitedStops/completedActivities/checkpoint/player/selections/exhibition. Không lưu class Phaser vào JSON.

Quest status: locked → available → active → completed, có thể chọn lại active quest theo cơ chế hiện có. Objective giữ id/text/completed/targetCount/currentCount. Hoàn tất quest mới xét reward; không cộng lại item khi reload.

DOM event `thai_nguyen_quest_event` chứa `{action,destinationId?,tourId?,payload?}`; iframe thêm `type:"THAI_NGUYEN_QUEST_EVENT"`. Event ending riêng tên `thai-nguyen-journey-ending`. Không đổi dấu gạch ngang/gạch dưới của tên sự kiện vì consumer phụ thuộc chúng.
