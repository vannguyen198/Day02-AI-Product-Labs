# Official Deliverable Submission - Le Van Nguyen

# 01 — Individual Problem Scan
Case: Startup về AI/Chatbot cho học sinh ôn luyện các môn học văn hoá.

| # | Lăng kính | Problem quan sát được | Ai đang đau? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại, tốn thời gian | Các đầu sách, tài liệu sử dụng để train mô hình AI cho Giáo dục thường phải nhập hoặc upload thủ công lên portal nội bộ | Đội ngũ manual entry | Mất 2 phút để up được đầu sách có nhập liệu thông tin (chưa kể độ trễ do quá tải) |
| 2 | Pain từ người khác | Không có đội ngũ tester/BA chính thức | Đội ngũ manual entry | Phải tự lên test case đang bị FAILED song song với manual testing cũng như tài liệu use case |
| 3 | Tốn thời gian, Pain từ người khác | Các dữ liệu về ngân hàng câu hỏi, đầu sách khi có typo không thể chỉnh sửa hay xoá bớt | Đội ngũ manual entry | Sau khi up xong đầu sách, không có nút "Delete" bằng chữ hay ký hiệu thùng rác hay nút "Modify" để xoá hay chỉnh sửa |
| 4 | Pain từ người khác | Khi nhập xong một đầu dữ liệu về ngân hàng câu hỏi, không thể biết dữ liệu câu hỏi được lưu lại ở đâu | Đội ngũ manual entry | Khi bấm "Save" khi nhập xong dữ liệu của 1 câu hỏi, nó chỉ hiện thông báo "Lưu thành công" rồi các phần dữ liệu câu hỏi điền lập tức biến mất |
| 5 | Tốn thời gian | Đến cả những câu hỏi cơ bản nhất trong đề thi, kiểm tra vẫn vừa phải nhập lời giải chi tiết và vừa phải nhập lời giải từng bước | Đội ngũ manual entry | Thời gian nhập xong dữ liệu 1 câu hỏi trắc nghiệm, đúng/sai bị tăng lên đến 4-5 phút/câu |
| 6 | AI có thể tốt hơn | Người xem (học sinh) nhận được dữ liệu không đồng nhất về cách giải | Cả team | Số lượng phản hồi/report về lỗi mâu thuẫn giữa 2 phần lời giải tăng đáng kể |
| 7 | Pain từ người khác | Mất thời gian formatting (LaTeX/hình ảnh) cho các khung nhập liệu | Đội ngũ manual entry | Với các câu hỏi trả lời đúng/sai, trả lời nhanh bị tăng lên đến 8-10 phút/câu, những trục trặc trong quá trình format LaTeX, hình ảnh xuất hiện thường xuyên hơn, khoảng 5-6 file/ngày gặp trục trặc |
| 8 | Tốn thời gian, lặp lại | Tổng hợp daily KPI thủ công | Đội ngũ manual entry | Lặp lại mỗi ngày, mỗi buổi sáng/chiều và mất thời gian để tổng hợp hết mỗi ngày từ cả đội ngũ |

## Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Các dữ liệu về ngân hàng câu hỏi, đầu sách khi có typo không có nút chỉnh sửa hoặc xoá | Không thể để cho đội ngũ data entry thêm đau vì không thể xoá hay chỉnh sửa | Chưa biết sau khi xoá được hay chỉnh sửa được dữ liệu, bộ dữ liệu sau khi vào có được xoá hay được chỉnh sửa hay không |
| 2 | Không có đội tester | Bất kỳ dự án nào về phần mềm hiện nay bắt buộc phải có đội ngũ tester/BA riêng, đầy đủ các tài liệu về test case (manual/automation) cũng như là tài liệu use case cho BA để kết nối với bộ phận, người làm dev | Những chức năng mới chưa chắc đã đảm bảo được user experience (UX) |
| 3 | Tổng hợp daily KPI thủ công | Cực kỳ lặp lại và tốn thời gian khi tổng hợp từ một đội ngũ manual entry | Data access khó, scope có thể quá lớn khi phải tổng hợp từ rất nhiều người trong đội ngũ manual entry đó |

## Problem Card #1 — Workflows & Test Cases

**Problem:**  
Các dữ liệu về ngân hàng câu hỏi, đầu sách khi có typo không có phải có nút chỉnh sửa hoặc xoá

**Actor:**  
Bộ phận dev chịu toàn bộ trách nhiệm trong việc thêm đầy đủ chức năng chỉnh sửa + xoá dữ liệu cho cổng nhập nội bộ

**Thời điểm / bối cảnh:**  
Đội ngũ manual entry đang không thể xoá hay chỉnh sửa bất cứ dữ liệu nhập thủ công nào, đặc biệt là khi nhập các đầu sách hay tài liệu.

**Current workflow:**

```text
1. Bộ phận dev thiết kế API/Endpoint chỉnh sửa & Xoá cho hệ thống
2. Tích hợp cũng như loại bỏ một số tính năng thừa lên giao diện (UI) dựa trên Test case sẵn có
3. Tự động hoá kiểm thử (Automated Test): Tạo đoạn script check lỗi cơ bản (xác nhận dữ liệu đã xoá/sửa trong Database), có thể tích hợp AI Agent
4. Đội ngũ nhập liệu tự test tính năng với tài khoản quyền Admin/Editor (không cần qua bước báo cáo).
5. Đẩy kết quả cập nhật bug vào hệ thống Jira/Trello hoặc tài liệu test case.
```

**Bottleneck:**  
Dữ liệu bị nhập sai luôn trong trạng thái dễ bị tồn đọng và phải sửa lại thủ công nếu có dữ liệu sai

**Impact:**  
Không người nào trong đội ngũ nhập liệu có thể xoá, chỉnh sửa, và mọi dữ liệu đã được nhập lên luôn có sự trùng lặp.

**Success metric:**  
Các nút chỉnh sửa/xoá BẮT BUỘC phải được hoàn thành đầy đủ các chức năng và hoạt động tốt. Đồng thời triệt tiêu tuyệt đối việc phải nhập liệu lại những dữ liệu bị sai, typo, tránh mọi tồn đọng về dữ liệu sai được nhập lên.

**Non-AI alternative:**  
Thông qua tài liệu test case, rà soát bug, update lại các test case

**AI hypothesis:**  
AI hỗ trợ việc truy vết dữ liệu sai được nhập lên trong quá trình update thông qua RAG

**Quick gut:**  
Workflow

### Current workflow

```text
CURRENT STATE — 90 phút

[1 Bộ phận dev thiết kế API/Endpoint chỉnh sửa & Xoá cho hệ thống: 30']
→ [2 Tích hợp tính năng lên giao diện (UI) dựa trên Test case sẵn có: 30']
→ [3 Tự động hoá kiểm thử (Automated Test): Tạo đoạn script check lỗi cơ bản (xác nhận dữ liệu đã xoá/sửa trong Database), có thể tích hợp AI Agent: 15']
→ [4 Đội ngũ nhập liệu tự test tính năng với tài khoản quyền Admin/Editor (không cần qua bước báo cáo): 10']
→ [5 Đẩy kết quả bug vào hệ thống Jira/Trello hoặc tài liệu test case: 5']  

```

### Future workflow

```text
FUTURE STATE — 45 phút

[1 Tự động QC tức thời: AI check typo/format ngay khi nhập: 2']
→ [2 Xử lý dữ liệu bị sai còn tồn đọng, có gợi ý từ AI Agent: 10']
→ [3 Review tập trung: PM/dev chỉ review các câu hỏi AI đánh dấu "Confidence low" (nghi ngờ lỗi): 15']
→ [Feedback loop: Chatbot/Học sinh review câu hỏi (cộng đồng/AI kiểm chứng): 10']  <-- human boundary
→ [5 PM gửi: 8']

```

## Problem Cards #2 và #3 — tóm tắt

| Card | Actor | Bottleneck | Metric | Quick gut | Vì sao chưa chọn làm #1 |
|---|---|---|---|---|---|
| Không có đội tester | Toàn bộ các member bao gồm PM | Đề xuất buổi họp riêng về bổ sung vị trí tuyển dụng cho các đội ngũ tester và BA | Đầy đủ đội ngũ tester, BA và có đầy đủ các use case | Workflow (không AI) | Cần có sự tìm kiếm và đồng thuận, hoàn toàn thuộc về yếu tố con người |
| Tổng hợp daily KPI thủ công | Toàn bộ các member bao gồm PM| Phát triển các dashboard trực quan về độ học của cả hệ thống bên cạnh chỉ số KPI của bộ phận nhập liệu | Đầy đủ các dashboard riêng về độ học của hệ thống, KPI nhằm điều chỉnh hệ thống chatbot và KPI của cả đội ngũ | Workflow | Data access và scope rộng |