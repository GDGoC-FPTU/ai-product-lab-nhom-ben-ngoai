# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

# 🔍 Phase 1 — SCAN (Cá nhân)

### Bảng quét cơ hội (Opportunity Matrix)

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| **1** | **Xanh SM (GSM)** | Stakeholder Pain / Time-consuming | Điều phối & Hỗ trợ tài xế khi xe điện sắp hết pin dưới 5%: Tra cứu vị trí trạm sạc khả thi, kiểm tra trụ trống và gửi chỉ đường cho tài xế. |
| **2** | **VinFast** | Repetitive / AI-upgrade | Phân loại và xử lý ticket phản hồi lỗi phần mềm/log sự cố từ xe điện thông minh (Connected Car Logs) về đúng các đội R&D chuyên trách. |
| **3** | **Vinmec** | Time-consuming / AI-upgrade | Tóm tắt hồ sơ bệnh án tiền sử lâu năm của bệnh nhân mãn tính và gợi ý danh mục kiểm tra lâm sàng trước khi vào phòng khám chính. |
| **4** | **Vinpearl / VinWonders** | Repetitive / Stakeholder Pain | Tự động phân loại sentiment, trích xuất thông tin phàn nàn và tạo bản thảo phản hồi đa ngôn ngữ cho đánh giá (review) của khách hàng trên OTA/Google. |
| **5** | **Vinhomes** | Repetitive / Time-consuming | Tự động tiếp nhận, phân loại và điều phối yêu cầu hỗ trợ/sửa chữa kỹ thuật của cư dân trên app Vinhomes Resident về đúng Đội Bảo trì Phân khu. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân)

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                       │
│                                                             │
│ Bài toán (1 câu): Hỗ trợ điều phối viên phản hồi chỉ đường  │
│ sạc khẩn cấp cho tài xế Xanh SM khi xe sắp hết pin (< 5%).  │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tổng đài viên điều phối & Tài xế GSM.  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tài xế gọi/nhắn báo pin < 5% ──> 2. Tổng đài viên mở   │
│   bản đồ trạm sạc ──> 3. Kiểm tra trạm gần nhất còn trụ ──> │
│   4. Soạn tin nhắn / Gọi chỉ đường cho tài xế.              │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Tra cứu vị trí trạm còn    │
│ trụ trống + tính khoảng cách an toàn (⏱ 5 - 8 phút/lượt)    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Tự động phân tích     │
│ vị trí/pin, truy vấn API trạm sạc và soạn sẵn tin nhắn chỉ  │
│ đường (Draft) cho tổng đài viên bấm duyệt.                  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian điều   │
│ phối hỗ trợ từ 7 phút xuống dưới 1.5 phút/lượt; 0% sự cố    │
│ xe bị cạn pin mid-route do chỉ dẫn sai trạm.                │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                       │
│                                                             │
│ Bài toán (1 câu): Phân loại tự động các ticket báo lỗi kỹ   │
│ thuật/log phần mềm từ xe VinFast về đúng phòng R&D.         │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ thuật viên hỗ trợ phần mềm (Tier-1).│
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Xe/Khách gửi log lỗi ──> 2. Kỹ thuật viên đọc mô tả +  │
│   mã log ──> 3. Đối chiếu danh mục lỗi VinFast ──> 4. Gán   │
│   tag & Chuyển ticket cho phòng R&D tương ứng (Pin/ADAS...). │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Đọc log text và phân loại  │
│ thủ công (⏱ 10 - 15 phút/ticket)                           │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Trích xuất thông tin  │
│ từ log, tự động gán tag phân loại lỗi và chuyển ticket.     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian xử lý  │
│ ticket từ 12 phút xuống dưới 30 giây; Tăng độ chính xác     │
│ phân loại từ 75% lên > 95%.                                 │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                       │
│                                                             │
│ Bài toán (1 câu): Tự động phân tích cảm xúc và tạo bản thảo│
│ phản hồi đánh giá khách hàng đa ngôn ngữ cho Vinpearl.      │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Vinpearl / VinWonders  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Quản trị chất lượng CSKH.    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Thu thập review trên OTA ──> 2. Dịch review đa ngôn    │
│   ngữ sang tiếng Việt ──> 3. Phân loại vấn đề ──> 4. Soạn    │
│   thư phản hồi chuẩn tone giọng thương hiệu.                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Dịch thuật và viết câu   │
│ trả lời cá nhân hóa theo từng tình huống (⏱ 15 phút/review) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Dịch thuật, trích xuất│
│ vấn đề cốt lõi và sinh bản thảo phản hồi cá nhân hóa.       │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian phản   │
│ hồi từ 15 phút xuống dưới 2 phút/review; 100% review phản  │
│ hồi trong vòng 24 giờ.                                      │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm)
*(Tập trung bài toán tiêu biểu: **Xanh SM Intelligent Dispatcher**)*

## 3.1. Current-State Workflow Mapping
* **Quy trình hiện tại:**
  `[Tài xế báo sự cố Pin < 5%]` ──(Handoff 1)──> `[Tổng đài tiếp nhận thông tin]` ──(🔴 Bottleneck: Mở bản đồ, tìm trạm sạc gần nhất, check trụ trống thủ công)──(Handoff 2)──> `[Tổng đài viên tính toán khoảng cách < 5km]` ──> `[Gửi tin nhắn / Gọi điện chỉ đường]`
* **Thời gian vận hành trung bình:** **6 - 8 phút / lượt xử lý**.

## 3.2. Problem Statement (6-field) & Metrics

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Tổng đài viên điều phối (Dispatcher) tại trung tâm vận hành Xanh SM. |
| **2. Current Workflow** | Tổng đài viên tiếp nhận yêu cầu hỗ trợ pin khẩn cấp qua app/cuộc gọi, tự tra cứu trạm sạc trên bản đồ nội bộ, kiểm tra trạng thái trụ trống và gửi hướng dẫn thủ công cho tài xế. |
| **3. Bottleneck** | Thao tác tra cứu vị trí trạm sạc, kiểm tra trạng thái trụ trống realtime và tính toán bán kính di chuyển an toàn ($< 5\text{ km}$) thủ công tốn quá nhiều thời gian, dễ gây cạn pin giữa đường. |
| **4. Business Impact** | Xe bị kiệt pin giữa đường làm ngưng trệ ca trực, gây ùn tắc giao thông, tăng chi phí cứu hộ và giảm chỉ số hài lòng của tài xế/khách hàng. |
| **5. Success Metric** | - Thời gian xử lý từ lúc phát sinh cảnh báo đến khi gửi chỉ đường: **Giảm từ 7 phút xuống < 1.5 phút/trường hợp**.<br>- Tỷ lệ chỉ dẫn thành công không bị kiệt pin giữa đường: **100%**. |
| **6. Operational Boundary** | - AI **chỉ tạo bản thảo tin nhắn (Draft)** kèm tag `[DRAFT_ONLY]`.<br>- AI **TUYỆT ĐỐI KHÔNG** tự động gửi tin nhắn cho tài xế mà chưa qua xác nhận của Tổng đài viên (Human-In-The-Loop).<br>- AI **KHÔNG** đề xuất trạm sạc cách xa $> 5\text{ km}$ khi pin dưới $5\%$. |

## 3.3. Future-State Flow & AI Fit
* **Mức AI Fit:** **Agentic Loop / LLM Feature** (LLM nhận dữ liệu vị trí/pin, truy vấn API trạm sạc, áp dụng quy tắc an toàn và đề xuất giải pháp).
* **Future-State Flow:**
  `[Hệ thống phát hiện Pin < 5%]` ──> 🔵 **[AI Step: LLM Agent kiểm tra bán kính < 5km & Lọc trạm trống qua API]** ──> 🔵 **[AI Step: LLM tạo draft bản tin chỉ đường + Tag [DRAFT_ONLY]]** ──> 🟢 **[Human Step: Tổng đài viên review & bấm Approval/Gửi]**
* ↩️ **Fallback Plan:** Nếu LLM gặp lỗi API hoặc không tìm thấy trạm trong bán kính $5\text{ km}$, hệ thống tự động kích hoạt Rule-based Fallback: Chuyển thẳng cuộc gọi ưu tiên cao nhất về Tổng đài viên con người kèm cảnh báo *"Cứu hộ khẩn cấp - Pin < 5%"*.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm)

Nhóm đã hoàn thành lập trình bản mẫu Prompt trên file `starter-code/prompt_prototype.py` với cấu trúc như sau:

* **System Instruction:** Thiết lập vai trò Co-pilot trợ lý điều phối cho Xanh SM. Quy định nghiêm ngặt bắt buộc gắn tiền tố `[DRAFT_ONLY]` và cấm gợi ý trạm sạc $> 5\text{ km}$ khi pin dưới $5\%$.
* **Adversarial Testing:** Tiến hành 3 bài test tấn công (như cố tình ép AI bỏ tag `[DRAFT_ONLY]` hoặc ép AI gợi ý trạm sạc xa $10\text{ km}$).
* **Kết quả:** Mô hình tuân thủ $100\%$ ranh giới an toàn, trả về đúng định dạng yêu cầu.

---

# 🏁 Phase 5 — EVALUATE (Nhóm)

### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs vị trí trạm sạc và trạng thái pin sạch để test.
2. [x] Rủi ro khi AI sai nằm trong tầm kiểm soát nhờ có cơ chế HITL (Tổng đài viên duyệt) và Fallback tự động.
3. [x] Stakeholders (Đội ngũ vận hành Xanh SM) sẵn sàng tiếp nhận công cụ co-pilot mới.

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype)**

**Justification:**
Bài toán có giá trị vận hành cao, giảm thời gian điều phối hơn $70\%$, giảm thiểu rủi ro kiệt pin xe điện trên đường. Kiến trúc đề xuất an toàn tuyệt đối nhờ cơ chế Human-in-the-loop (Tổng đài viên kiểm tra trước khi gửi) và Fallback rõ ràng. Chi phí triển khai API LLM thấp hơn rất nhiều so với tổn thất vận hành do sự cố kiệt pin gây ra.