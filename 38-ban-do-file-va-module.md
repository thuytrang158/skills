# Bản đồ file và module

Bảng đối chiếu các file nguồn, dữ liệu văn bản, cấu hình và kiểm thử đã thấy trong cả ba dự án. File build có hash, thư viện cài đặt, dữ liệu riêng và assets ảnh không liệt kê từng file. Ảnh thuộc module 02/07/08 và tài liệu 40; game build thuộc 36; package-lock theo package.json của module 01. File __init__.py là khởi tạo package, không cần chức năng nghiệp vụ riêng.

## Website

| File | Module hướng dẫn |
| --- | --- |
| `travel-web/.env.example` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/.gitignore` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/README.md` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/admin-api.cjs` | [14](14-web-api-quan-tri.md) |
| `travel-web/check.cjs` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/configure-groq-keys.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/customer-api.cjs` | [12](12-web-api-tai-khoan-khach.md) |
| `travel-web/demo-booking-api.cjs` | [09](09-web-cau-hinh-va-tinh-gia-booking.md), [10](10-web-api-booking-va-ton-cho.md) |
| `travel-web/export-catalogue.cjs` | [03](03-web-du-lieu-tour.md) |
| `travel-web/export-rag-data.cjs` | [24](24-rag-knowledge-base-va-chat.md) |
| `travel-web/integrate-engagement.cjs` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/package.json` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/rag-chat.cjs` | [24](24-rag-knowledge-base-va-chat.md) |
| `travel-web/server.cjs` | [16](16-web-server-va-proxy.md) |
| `travel-web/.openai/hosting.json` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/dist/app.js` | [04](04-web-tim-kiem-va-yeu-thich.md), [06](06-web-thiet-ke-hanh-trinh.md), [08](08-web-tin-tuc-va-danh-gia.md) |
| `travel-web/dist/chat-widget.css` | [24](24-rag-knowledge-base-va-chat.md) |
| `travel-web/dist/chat-widget.js` | [24](24-rag-knowledge-base-va-chat.md) |
| `travel-web/dist/cuisine-data.js` | [07](07-web-am-thuc.md) |
| `travel-web/dist/cuisine.css` | [07](07-web-am-thuc.md) |
| `travel-web/dist/cuisine.js` | [07](07-web-am-thuc.md) |
| `travel-web/dist/customer.css` | [13](13-web-tai-khoan-va-thanh-toan.md) |
| `travel-web/dist/customer.js` | [13](13-web-tai-khoan-va-thanh-toan.md) |
| `travel-web/dist/index.html` | [02](02-web-bo-cuc-va-giao-dien.md) |
| `travel-web/dist/news-data.js` | [08](08-web-tin-tuc-va-danh-gia.md) |
| `travel-web/dist/news.css` | [08](08-web-tin-tuc-va-danh-gia.md) |
| `travel-web/dist/news.js` | [08](08-web-tin-tuc-va-danh-gia.md) |
| `travel-web/dist/style.css` | [02](02-web-bo-cuc-va-giao-dien.md) |
| `travel-web/dist/tour-booking.js` | [09](09-web-cau-hinh-va-tinh-gia-booking.md), [11](11-web-giao-dien-dat-tour.md) |
| `travel-web/dist/tour-details.css` | [05](05-web-chi-tiet-tour.md), [11](11-web-giao-dien-dat-tour.md) |
| `travel-web/dist/tour-details.js` | [05](05-web-chi-tiet-tour.md) |
| `travel-web/dist/tour-engagement.css` | [04](04-web-tim-kiem-va-yeu-thich.md) |
| `travel-web/dist/tour-engagement.js` | [04](04-web-tim-kiem-va-yeu-thich.md) |
| `travel-web/dist/tour-reviews-data.js` | [04](04-web-tim-kiem-va-yeu-thich.md), [08](08-web-tin-tuc-va-danh-gia.md) |
| `travel-web/dist/tours-data.js` | [03](03-web-du-lieu-tour.md) |
| `travel-web/dist/admin/admin.css` | [15](15-web-trang-quan-tri.md) |
| `travel-web/dist/admin/admin.js` | [15](15-web-trang-quan-tri.md) |
| `travel-web/dist/admin/index.html` | [15](15-web-trang-quan-tri.md) |
| `travel-web/dist/ai-planner/index.html` | [23](23-planner-api-cli-va-giao-dien.md) |
| `travel-web/dist/data/rag-knowledge-base.json` | [24](24-rag-knowledge-base-va-chat.md) |
| `travel-web/dist/data/tour-booking-config-v2.json` | [09](09-web-cau-hinh-va-tinh-gia-booking.md) |
| `travel-web/dist/data/tour-catalogue.md` | [03](03-web-du-lieu-tour.md) |
| `travel-web/dist/data/tours.json` | [03](03-web-du-lieu-tour.md) |
| `travel-web/test/demo-booking-api.test.cjs` | [37](37-kiem-thu-va-ban-giao.md) |

## Game

| File | Module hướng dẫn |
| --- | --- |
| `game12/.gitignore` | [37](37-kiem-thu-va-ban-giao.md) |
| `game12/README.md` | [37](37-kiem-thu-va-ban-giao.md) |
| `game12/index.html` | [01](01-kien-truc-va-khoi-tao.md), [26](26-game-khoi-dong-va-assets.md) |
| `game12/package.json` | [01](01-kien-truc-va-khoi-tao.md), [26](26-game-khoi-dong-va-assets.md) |
| `game12/tsconfig.json` | [01](01-kien-truc-va-khoi-tao.md), [26](26-game-khoi-dong-va-assets.md) |
| `game12/vite.config.ts` | [01](01-kien-truc-va-khoi-tao.md), [26](26-game-khoi-dong-va-assets.md) |
| `game12/scripts/check-village.cjs` | [37](37-kiem-thu-va-ban-giao.md) |
| `game12/src/main.ts` | [26](26-game-khoi-dong-va-assets.md) |
| `game12/src/style.css` | [26](26-game-khoi-dong-va-assets.md) |
| `game12/src/assets/lakeArt.ts` | [26](26-game-khoi-dong-va-assets.md), [33](33-game-ho-nui-coc.md) |
| `game12/src/assets/pixelArtGenerator.ts` | [26](26-game-khoi-dong-va-assets.md), [33](33-game-ho-nui-coc.md) |
| `game12/src/data/achievements.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/destinations.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/dialogues.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/items.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/lake.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/quests.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/regionAccess.mjs` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/shopProducts.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/teaBrewingProfiles.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/data/teaCultivars.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/entities/NPC.ts` | [29](29-game-nhan-vat-ui-va-am-thanh.md) |
| `game12/src/entities/Player.ts` | [29](29-game-nhan-vat-ui-va-am-thanh.md) |
| `game12/src/integrations/tourismApi.ts` | [36](36-game-tich-hop-website.md) |
| `game12/src/minigames/CaveLightMinigame.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/minigames/CulturalQuizModal.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/minigames/DestinationActivityMinigame.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/minigames/HistoricalTimelineMinigame.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/minigames/LakeLegendMinigame.ts` | [33](33-game-ho-nui-coc.md) |
| `game12/src/minigames/RiverCrossingMinigame.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/minigames/TeaBrewingMinigame.ts` | [32](32-game-pha-tra-va-danh-gia.md) |
| `game12/src/minigames/TeaHarvestMinigame.ts` | [31](31-game-hai-va-che-bien-che.md) |
| `game12/src/minigames/TeaProcessingMinigame.ts` | [31](31-game-hai-va-che-bien-che.md) |
| `game12/src/minigames/TungConMinigame.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/scenes/AtkDinhHoaScene.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/scenes/BaoTangVanHoaScene.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/scenes/BootScene.ts` | [26](26-game-khoi-dong-va-assets.md) |
| `game12/src/scenes/DenDuomScene.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/scenes/HangPhuongHoangScene.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/scenes/HoNuiCocScene.ts` | [33](33-game-ho-nui-coc.md) |
| `game12/src/scenes/MainMenuScene.ts` | [26](26-game-khoi-dong-va-assets.md) |
| `game12/src/scenes/RegionalChapterScene.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/scenes/SuoiCuaTuScene.ts` | [34](34-game-atk-hang-va-suoi.md) |
| `game12/src/scenes/TanCuongScene.ts` | [30](30-game-tan-cuong-va-nha-tra.md) |
| `game12/src/scenes/TeaHouseScene.ts` | [30](30-game-tan-cuong-va-nha-tra.md) |
| `game12/src/scenes/ThaiHaiScene.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/systems/AudioManager.ts` | [29](29-game-nhan-vat-ui-va-am-thanh.md) |
| `game12/src/systems/InventoryManager.ts` | [28](28-game-luu-tien-trinh-va-phan-thuong.md) |
| `game12/src/systems/LakeJourney.ts` | [33](33-game-ho-nui-coc.md) |
| `game12/src/systems/ProgressionService.ts` | [28](28-game-luu-tien-trinh-va-phan-thuong.md) |
| `game12/src/systems/QuestManager.ts` | [28](28-game-luu-tien-trinh-va-phan-thuong.md) |
| `game12/src/systems/RegionRegistry.ts` | [28](28-game-luu-tien-trinh-va-phan-thuong.md) |
| `game12/src/systems/RegionalExplorerGuide.ts` | [35](35-game-thai-hai-den-duom-bao-tang.md) |
| `game12/src/systems/SaveManager.ts` | [28](28-game-luu-tien-trinh-va-phan-thuong.md) |
| `game12/src/systems/TeaBrewingEvaluator.ts` | [32](32-game-pha-tra-va-danh-gia.md) |
| `game12/src/types/game.ts` | [27](27-game-du-lieu-va-kieu.md) |
| `game12/src/ui/LakeExperience.ts` | [33](33-game-ho-nui-coc.md) |
| `game12/src/ui/LakeFieldGuide.ts` | [33](33-game-ho-nui-coc.md) |
| `game12/src/ui/ShopModal.ts` | [29](29-game-nhan-vat-ui-va-am-thanh.md) |
| `game12/src/ui/UIManager.ts` | [29](29-game-nhan-vat-ui-va-am-thanh.md) |
| `game12/src/ui/VillageGuide.ts` | [29](29-game-nhan-vat-ui-va-am-thanh.md) |
| `game12/src/ui/lake.css` | [33](33-game-ho-nui-coc.md) |
| `game12/test/lake_chapter.test.js` | [37](37-kiem-thu-va-ban-giao.md) |
| `game12/test/quest_and_save.test.js` | [37](37-kiem-thu-va-ban-giao.md) |
| `game12/test/region_access.test.js` | [37](37-kiem-thu-va-ban-giao.md) |

## Planner độc lập

| File | Module hướng dẫn |
| --- | --- |
| `Multi-Agent-AI-Travel-Planner/.env.example` | [01](01-kien-truc-va-khoi-tao.md) |
| `Multi-Agent-AI-Travel-Planner/.gitignore` | [37](37-kiem-thu-va-ban-giao.md) |
| `Multi-Agent-AI-Travel-Planner/LICENSE` | [37](37-kiem-thu-va-ban-giao.md) |
| `Multi-Agent-AI-Travel-Planner/README.md` | [37](37-kiem-thu-va-ban-giao.md) |
| `Multi-Agent-AI-Travel-Planner/mythainguyen_places.json` | [19](19-planner-nguon-dia-danh.md) |
| `Multi-Agent-AI-Travel-Planner/requirements.txt` | [01](01-kien-truc-va-khoi-tao.md) |
| `Multi-Agent-AI-Travel-Planner/src/__init__.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `Multi-Agent-AI-Travel-Planner/src/api.py` | [17](17-planner-schema-va-state.md), [23](23-planner-api-cli-va-giao-dien.md) |
| `Multi-Agent-AI-Travel-Planner/src/config.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `Multi-Agent-AI-Travel-Planner/src/main.py` | [18](18-planner-yeu-cau-va-y-dinh.md), [21](21-planner-lich-trinh-va-dieu-chinh.md), [23](23-planner-api-cli-va-giao-dien.md) |
| `Multi-Agent-AI-Travel-Planner/src/schemas.py` | [17](17-planner-schema-va-state.md) |
| `Multi-Agent-AI-Travel-Planner/src/state.py` | [17](17-planner-schema-va-state.md) |
| `Multi-Agent-AI-Travel-Planner/src/static/index.html` | [23](23-planner-api-cli-va-giao-dien.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/__init__.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/accommodation.py` | [22](22-planner-luu-tru-va-chi-phi.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/clustering.py` | [20](20-planner-geocoding-va-routing.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/cost_calculator.py` | [22](22-planner-luu-tru-va-chi-phi.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/currency.py` | [22](22-planner-luu-tru-va-chi-phi.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/modification.py` | [21](21-planner-lich-trinh-va-dieu-chinh.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/mythainguyen.py` | [19](19-planner-nguon-dia-danh.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/places.py` | [19](19-planner-nguon-dia-danh.md), [20](20-planner-geocoding-va-routing.md) |
| `Multi-Agent-AI-Travel-Planner/src/tools/routing.py` | [20](20-planner-geocoding-va-routing.md) |
| `Multi-Agent-AI-Travel-Planner/tests/test_place_sources.py` | [37](37-kiem-thu-va-ban-giao.md) |
| `Multi-Agent-AI-Travel-Planner/tests/test_thai_nguyen_places.py` | [37](37-kiem-thu-va-ban-giao.md) |

## Planner tích hợp

| File | Module hướng dẫn |
| --- | --- |
| `travel-web/Multi-Agent-AI-Travel-Planner/.env.example` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/.gitignore` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/LICENSE` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/README.md` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/mythainguyen_places.json` | [19](19-planner-nguon-dia-danh.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/requirements.txt` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/__init__.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/api.py` | [17](17-planner-schema-va-state.md), [23](23-planner-api-cli-va-giao-dien.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/config.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/main.py` | [18](18-planner-yeu-cau-va-y-dinh.md), [21](21-planner-lich-trinh-va-dieu-chinh.md), [23](23-planner-api-cli-va-giao-dien.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/rag_retrieval.py` | [25](25-rag-bge-m3-va-qdrant.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/schemas.py` | [17](17-planner-schema-va-state.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/state.py` | [17](17-planner-schema-va-state.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/static/index.html` | [23](23-planner-api-cli-va-giao-dien.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/__init__.py` | [01](01-kien-truc-va-khoi-tao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/accommodation.py` | [22](22-planner-luu-tru-va-chi-phi.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/clustering.py` | [20](20-planner-geocoding-va-routing.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/cost_calculator.py` | [22](22-planner-luu-tru-va-chi-phi.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/currency.py` | [22](22-planner-luu-tru-va-chi-phi.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/intent.py` | [18](18-planner-yeu-cau-va-y-dinh.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/modification.py` | [21](21-planner-lich-trinh-va-dieu-chinh.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/mythainguyen.py` | [19](19-planner-nguon-dia-danh.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/places.py` | [19](19-planner-nguon-dia-danh.md), [20](20-planner-geocoding-va-routing.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/requirements.py` | [18](18-planner-yeu-cau-va-y-dinh.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/src/tools/routing.py` | [20](20-planner-geocoding-va-routing.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/tests/test_place_sources.py` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/tests/test_requirements_agent.py` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/tests/test_thai_nguyen_places.py` | [37](37-kiem-thu-va-ban-giao.md) |
| `travel-web/Multi-Agent-AI-Travel-Planner/tests/test_trip_intent.py` | [37](37-kiem-thu-va-ban-giao.md) |

Tổng số file nguồn/cấu hình/dữ liệu văn bản được ánh xạ: **162**. Bảng phản ánh snapshot hiện tại; khi thêm component mới cần cập nhật module tương ứng.
