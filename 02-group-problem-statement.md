# 02 — Group Problem Statement (This part is submitted for all group members)

## Phase 3 — Group Convergence

### Candidate problem nhóm chọn

Người đi học/đi làm xa nhà mất nhiều thời gian tìm phòng trọ phù hợp vì thông tin nằm rải rác trên Facebook, TikTok, website cho thuê trọ và bản đồ; đồng thời khó đánh giá nơi nào vừa rẻ, vừa gần chỗ học/làm, vừa thuận tiện di chuyển và ít rủi ro lừa đảo.

### Vì sao nhóm chọn

Nhóm chọn problem này vì đây là pain thực tế với sinh viên và người đi làm xa nhà. Người thuê thường phải tự lướt nhiều nguồn như Facebook Marketplace, nhóm Facebook, TikTok, Chợ Tốt/Nhà Tốt, Batdongsan và Google Maps. Các nền tảng hiện có có bộ lọc giá/vị trí, nhưng vẫn khó xử lý bài đăng tự do, viết tắt, thiếu thông tin hoặc video review. Facebook Marketplace có mục Property Rentals, Nhà Tốt/Chợ Tốt và Batdongsan cũng có danh sách phòng trọ/cho thuê theo giá, diện tích, vị trí.

### Vì sao không chọn các candidate khác

| Candidate | Vì sao không chọn |
|---|---|
| Debug training model AI | Pain mạnh nhưng chỉ phù hợp với nhóm học AI, phạm vi người dùng hẹp hơn |
| Tóm tắt worksheet/lab | Có thể giải bằng checklist hoặc template, chưa cần Agent |
| Quản lý chi tiêu cá nhân | Nhiều app đã có, AI value chưa rõ bằng bài toán tìm trọ |
| Tìm tài liệu học tập | Scope rộng, khó validate nhanh trong thời gian lab |

### Score table

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | AI value | Làm trong lab | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|
| Tìm phòng trọ tối ưu bằng Agent | 5 | 5 | 5 | 5 | 5 | 4 | 29 |
| Debug training model | 5 | 5 | 4 | 5 | 4 | 4 | 27 |
| Tóm tắt worksheet/lab | 5 | 4 | 4 | 4 | 2 | 5 | 24 |
| Quản lý chi tiêu cá nhân | 4 | 4 | 3 | 4 | 3 | 4 | 22 |

### Candidate nhóm chốt

**Agent hỗ trợ tìm phòng trọ tối ưu theo địa điểm học/làm, ngân sách thuê và chi phí di chuyển.**

---

## Phase 4 — Validation + Research

### Quick validation

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Phỏng vấn nhanh sinh viên/người đi làm xa nhà | 3 | Đều từng mất nhiều giờ lướt Facebook, TikTok hoặc website để tìm phòng | Một số người vẫn ưu tiên hỏi người quen trước | Thu hẹp problem vào “shortlist phòng phù hợp”, không thay người dùng quyết định thuê |
| Quan sát workflow hiện tại | 5 bài đăng/phòng trọ mẫu | Tin đăng thiếu thông tin, viết tắt, giá/địa điểm không đồng nhất | Nguồn dữ liệu có thể không đầy đủ hoặc tin đã hết phòng | Agent cần gắn cờ “cần xác minh” thay vì khẳng định chắc chắn |
| Research rủi ro | Tin tức/case scam | Có rủi ro lừa đảo khi thuê nhà qua nền tảng rao vặt/social media | Không phải tin nào trên social cũng xấu | Agent chỉ cảnh báo rủi ro, người dùng vẫn phải xác minh và đi xem phòng |

### Research giải pháp đã có

| Nguồn / tool | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống | Bài học cho nhóm |
|---|---|---|---|---|
| Facebook Marketplace Property Rentals | Có danh sách nhà/phòng cho thuê theo khu vực | Nhiều tin đăng từ người dùng | Nội dung tự do, khó chuẩn hóa, khó đánh giá độ tin cậy | Agent cần đọc và bóc tách tin đăng phi cấu trúc |
| Nhà Tốt / Chợ Tốt | Có nhiều tin phòng trọ, giá, diện tích, vị trí | Dữ liệu nhiều và cập nhật | Vẫn cần người dùng tự so sánh nhiều tin | Agent có thể gom và xếp hạng |
| Batdongsan | Có bộ lọc giá, diện tích, vị trí | Structured hơn social | Không bao phủ hết tin từ Facebook/TikTok | Không nên chỉ phụ thuộc một nguồn |
| Google Maps Routes API | Tính thời gian/khoảng cách di chuyển giữa nhiều điểm | Phù hợp để so sánh tiện di chuyển | Cần kết hợp với giá thuê và nhu cầu cá nhân | Agent nên dùng map như một tool để tính commute score |
| TikTok rental videos | Có video review phòng và mô tả ngắn | Người dùng thích xem trực quan | Dữ liệu video khó lọc bằng rule | AI có lợi thế trong tóm tắt nội dung phi cấu trúc |

Google Routes API có thể tính khoảng cách/thời gian di chuyển giữa nhiều điểm, phù hợp với bài toán so sánh phòng trọ theo địa điểm học/làm. Ngoài ra, rủi ro rental scam trên các nền tảng rao vặt/social media là có thật, nên Agent không được tự kết luận “an toàn”, mà chỉ nên đưa cảnh báo và yêu cầu người dùng xác minh.

---

## Phase 5 — Workflow + Problem Statement

### Current Workflow

```text
CURRENT STATE — 3 đến 4 giờ

[1 Nhập nhu cầu trong đầu]
→ [2 Lướt Facebook groups / Marketplace]
→ [3 Xem TikTok review phòng]
→ [4 Tìm thêm trên Chợ Tốt / Batdongsan]
→ [5 Mở Google Maps để xem khoảng cách]
→ [6 Ghi chú thủ công các phòng phù hợp]
→ [7 So sánh giá thuê + khoảng cách + tiện ích]
→ [8 Nhắn tin chủ trọ]
→ [9 Đi xem phòng và quyết định]
```

### Bottleneck
- [2 Lướt nhiều nguồn]
- [5 Tự kiểm tra khoảng cách]
- [7 So sánh thủ công]

### Future Workflow — Agent
FUTURE STATE — 30 đến 45 phút
```text
[1 Người dùng nhập nhu cầu]
    - địa điểm học/làm
    - ngân sách thuê
    - phương tiện di chuyển
    - bán kính mong muốn
    - ưu tiên: rẻ / gần / an toàn / tiện ích
        ↓
[2 Agent thu thập listing từ nhiều nguồn]
    - Facebook / groups
    - website phòng trọ
    - TikTok review
    - nguồn người dùng paste vào
        ↓
[3 Agent bóc tách thông tin]
    - giá thuê
    - địa chỉ/khu vực
    - diện tích
    - tiện ích
    - số điện thoại/chủ đăng
    - dấu hiệu thiếu tin cậy
        ↓
[4 Agent gọi map/tool để tính commute]
    - khoảng cách đến nơi học/làm
    - thời gian di chuyển
    - tuyến đường/phương tiện phù hợp
        ↓
[5 Agent chấm điểm và xếp hạng]
    - rent score
    - commute score
    - convenience score
    - risk score
    - overall fit score
        ↓
[6 Agent tạo shortlist Top 5–10 phòng]
        ↓
[7 Người dùng kiểm tra, liên hệ và đi xem phòng]
```
### Before/After impact
| Metric | Trước | Sau kỳ vọng | Ghi chú |
| :--- | :---: | :---: | :--- |
| **Thời gian tìm phòng** | 3–4 giờ | 30–45 phút | Agent gom, lọc, xếp hạng |
| **Số tin phải đọc** | 80–100+ tin | 5–10 tin shortlist | Người dùng chỉ đọc tin phù hợp |
| **Số nguồn phải tự mở** | 4–5 nguồn | 1 giao diện tổng hợp | Agent thu thập và chuẩn hóa |
| **Rủi ro bỏ sót phòng phù hợp** | Cao | Thấp hơn | Agent quét nhiều nguồn |
| **Rủi ro tin không đáng tin** | Cao | Có cảnh báo | Agent chỉ flag, không đảm bảo an toàn tuyệt đối |

### Problem Statement
| Field | Nội dung |
| :--- | :--- |
| **Actor** | Sinh viên hoặc người đi làm xa nhà cần tìm phòng trọ gần nơi học/làm |
| **Workflow** | Người dùng lướt Facebook/TikTok/website, mở map kiểm tra khoảng cách, ghi chú phòng phù hợp, so sánh giá và liên hệ chủ trọ |
| **Bottleneck** | Dữ liệu rải rác, không có cấu trúc; người dùng phải tự lọc, tự so sánh và tự tính khoảng cách |
| **Impact** | Mất 3–4 giờ tìm kiếm; dễ bỏ sót phòng phù hợp; có rủi ro gặp tin thiếu tin cậy hoặc lừa đảo |
| **Success Metric** | Giảm thời gian tìm kiếm xuống 30–45 phút; shortlist 5–10 phòng phù hợp; giảm số tin phải đọc thủ công |
| **Boundary** | Agent không tự đặt cọc, không tự ký hợp đồng, không khẳng định tin đăng an toàn tuyệt đối |

## Phase 6 - Rule / Workflow / Agent + Decision
### Bài toán nằm ở mức độ như nào
- Bài toán có độ phức tạp cao
#### Vì sao:
- Độ mơ hồ cao: tin đăng Facebook/TikTok dùng ngôn ngữ tự do, viết tắt, thiếu thông tin.
- Độ phức tạp cao: cần nhiều bước liên tục như thu thập dữ liệu, bóc tách, gọi map, tính chi phí, xếp hạng, cảnh báo rủi ro.
- Agent có thể phù hợp vì cần gọi nhiều tool và tự điều phối các bước theo input người dùng.

### So sánh Rule / Workflow / Agent
| Mức | Phương án | Khi nào đủ | Rủi ro | Chọn? |
| :--- | :--- | :--- | :--- | :--- |
| **Rule** | Bộ lọc theo giá, quận, diện tích, bán kính | Đủ nếu dữ liệu đã sạch và có cấu trúc | Không hiểu bài đăng tự do, video, viết tắt, thiếu địa chỉ | Không đủ |
| **Workflow** | Người dùng paste tin → AI tóm tắt → tính khoảng cách → xếp hạng | Đủ cho demo nhỏ với nguồn dữ liệu cố định | Cần người dùng tự đưa dữ liệu, chưa tự động hóa nhiều | Có thể dùng cho MVP |
| **Agent** | Agent nhận nhu cầu → tìm nguồn → bóc tách → gọi map → tính điểm → shortlist → cảnh báo rủi ro | Phù hợp khi cần nhiều nguồn, nhiều tool, nhiều bước phụ thuộc nhau | Có rủi ro sai dữ liệu, hallucination, vi phạm nguồn nếu crawl không đúng | Chọn cho hướng phát triển |

### Agent input
- Địa điểm học/làm
- Ngân sách thuê tối đa
- Phương tiện di chuyển
- Bán kính mong muốn
- Ưu tiên cá nhân: rẻ, gần, an toàn, tiện ích
- Nguồn dữ liệu phòng trọ hoặc link bài đăng

### Agent tools
| Tool | Mục đích |
| :--- | :--- |
| **Search/listing collector** | Thu thập hoặc nhận danh sách phòng từ nhiều nguồn |
| **Parser/Extractor** | Bóc tách giá, địa chỉ, diện tích, tiện ích |
| **Map/Route tool** | Tính khoảng cách và thời gian di chuyển |
| **Scoring tool** | Tính điểm phù hợp |
| **Risk checker** | Gắn cờ tin thiếu thông tin, giá bất thường, yêu cầu cọc sớm |
| **Summary generator** | Tạo shortlist dễ đọc cho người dùng |

### Problems statement
| Field | Nội dung |
| :--- | :--- |
| **Actor** | Sinh viên/người đi làm xa nhà cần tìm phòng trọ gần nơi học/làm |
| **Workflow** | Nhập nhu cầu → Agent thu thập listing → bóc tách thông tin → tính commute bằng map → xếp hạng → người dùng kiểm tra và liên hệ |
| **Bottleneck** | Tự tìm và so sánh phòng từ nhiều nguồn mất 3–4 giờ, đặc biệt ở bước đọc tin phi cấu trúc và kiểm tra khoảng cách |
| **Impact** | Tốn thời gian, dễ bỏ sót phòng phù hợp, khó tối ưu giữa giá thuê và commute, có rủi ro gặp tin thiếu tin cậy |
| **Success Metric** | Giảm thời gian tìm phòng xuống 30–45 phút; tạo shortlist 5–10 phòng; giảm số tin phải đọc từ 80–100+ xuống dưới 15 |
| **Boundary** | Agent không tự đặt cọc, không tự ký hợp đồng, không đảm bảo tin 100% an toàn, không thay người dùng đi xem phòng |
| **AI intervention point** | Bóc tách dữ liệu phi cấu trúc, gọi map, tính điểm phù hợp, tạo shortlist và cảnh báo rủi ro |
| **Mức chọn** | Agent |
| **Rủi ro & người thật kiểm tra** | **Rủi ro:** dữ liệu sai, tin hết phòng, giá không cập nhật, scam.<br>**Người thật:** Người dùng phải xác minh với chủ trọ, đi xem phòng và không chuyển cọc trước khi kiểm tra |