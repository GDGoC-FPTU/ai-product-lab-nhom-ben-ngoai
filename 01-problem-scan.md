<<<<<<< HEAD
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)


### 📝 List bài toán của tôi:
| # | Subsidiary            | Lens             | Mô tả ngắn bài toán                                                                                                                                      |
| - | --------------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Xanh SM               | Repetitive       | Dispatcher phải kiểm tra mức pin, tìm trạm sạc gần nhất và soạn tin nhắn hướng dẫn cho tài xế mỗi khi nhận yêu cầu hỗ trợ.                               |
| 2 | VinFast               | Time-consuming   | Nhân viên CSKH phải đọc log xe và lịch sử lỗi để phân loại nguyên nhân trước khi chuyển cho kỹ thuật viên, mất nhiều thời gian khi số lượng yêu cầu lớn. |
| 3 | Vinmec                | AI-upgrade       | Bác sĩ phải đọc toàn bộ hồ sơ bệnh án và kết quả xét nghiệm trước khi khám; AI có thể tóm tắt thông tin quan trọng để rút ngắn thời gian chuẩn bị.       |
| 4 | Vinhomes              | Stakeholder Pain | Cư dân phản ánh sự cố (điện, nước, thang máy...) qua nhiều kênh, nhân viên phải phân loại và chuyển đúng bộ phận nên thường chậm hoặc nhầm lẫn.          |
| 5 | Vinpearl / VinWonders | AI-upgrade       | Chatbot hỗ trợ đặt phòng và đặt vé vẫn trả lời theo kịch bản cố định, chưa tư vấn linh hoạt theo nhu cầu của khách hàng.                                 |


---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                      │
│                                                            │
│ Bài toán: Hỗ trợ dispatcher xử lý tài xế Xanh SM sắp hết pin│
│                                                            │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                            │
│ Ai đang đau (Actor)? Dispatcher Xanh SM                   │
│                                                            │
│ Workflow thủ công hiện tại (3-5 bước):                    │
│ 1. Nhận yêu cầu từ tài xế                                 │
│    ──> 2. Kiểm tra mức pin và vị trí                       │
│    ──> 3. Tìm trạm sạc hoặc phương án hỗ trợ               │
│    ──> 4. Soạn và gửi hướng dẫn cho tài xế                 │
│                                                            │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Tìm phương án phù hợp và soạn hướng dẫn                    │
│ (⏱ khoảng 5 phút/lượt)                                    │
│                                                            │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Đề xuất phương án xử lý và soạn tin nhắn theo quy định.    │
│                                                            │
│ Đo thành công bằng gì?                                     │
│ Giảm thời gian xử lý từ 5 phút xuống dưới 1 phút,          │
│ 95% phản hồi đúng quy trình vận hành.                      │
│                                                            │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM [ ] Agent   │
└─────────────────────────────────────────────────────────────┘
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                      │
│                                                            │
│ Bài toán: Tóm tắt log lỗi xe trước khi chuyển kỹ thuật viên│
│                                                            │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM              │
│                     [ ] Vinhomes [ ] Vinmec               │
│                                                            │
│ Ai đang đau (Actor)? Nhân viên CSKH VinFast               │
│                                                            │
│ Workflow thủ công hiện tại (3-5 bước):                    │
│ 1. Nhận yêu cầu khách hàng                                │
│    ──> 2. Đọc log xe và lịch sử sửa chữa                  │
│    ──> 3. Tóm tắt nguyên nhân                              │
│    ──> 4. Chuyển cho kỹ thuật viên                         │
│                                                            │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Đọc và tổng hợp log lỗi                                   │
│ (⏱ khoảng 10 phút/lượt)                                   │
│                                                            │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Tóm tắt log và gợi ý nhóm lỗi để nhân viên kiểm tra.       │
│                                                            │
│ Đo thành công bằng gì?                                     │
│ Giảm thời gian đọc log từ 10 phút xuống dưới 2 phút,       │
│ độ chính xác phân loại đạt trên 90%.                       │
│                                                            │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM [ ] Agent   │
└─────────────────────────────────────────────────────────────┘
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                      │
│                                                            │
│ Bài toán: Phân loại phản ánh cư dân và chuyển đúng bộ phận │
│                                                            │
│ Công ty thành viên: [ ] VinFast [ ] Xanh SM [x] Vinhomes   │
│                     [ ] Vinmec                             │
│                                                            │
│ Ai đang đau (Actor)? Nhân viên chăm sóc cư dân            │
│                                                            │
│ Workflow thủ công hiện tại (3-5 bước):                    │
│ 1. Nhận phản ánh từ cư dân                                │
│    ──> 2. Đọc nội dung                                     │
│    ──> 3. Phân loại sự cố                                  │
│    ──> 4. Chuyển ticket cho bộ phận phụ trách              │
│                                                            │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Phân loại và định tuyến ticket                             │
│ (⏱ khoảng 6 phút/lượt)                                    │
│                                                            │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Phân loại nội dung và đề xuất bộ phận xử lý phù hợp.       │
│                                                            │
│ Đo thành công bằng gì?                                     │
│ Giảm thời gian xử lý từ 6 phút xuống dưới 1 phút,          │
│ 95% ticket được chuyển đúng bộ phận ngay lần đầu.          │
│                                                            │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM [ ] Agent   │
└─────────────────────────────────────────────────────────────┘
=======
# 01-problem-scan.md

# Phase 1 --- SCAN

  -------------------------------------------------------------------------------
  \#    Subsidiary           Lens             Mô tả ngắn bài toán
  ----- -------------------- ---------------- -----------------------------------
  1     Vinmec               Time-consuming   Bác sĩ phải đọc hồ sơ bệnh án cũ
                                              trước khi khám, mất nhiều thời gian
                                              tổng hợp thông tin bệnh nhân.

  2     Xanh SM              Stakeholder Pain Tài xế phản ánh hệ thống gợi ý điểm
                                              đón chưa tối ưu khiến phải gọi điện
                                              xác nhận với khách nhiều lần.

  3     VinFast              AI-upgrade       Nhân viên CSKH phải trả lời hàng
                                              nghìn câu hỏi về lỗi xe, bảo hành
                                              và cập nhật OTA mỗi ngày.

  4     Vinhomes             Repetitive       Ban quản lý phải đọc và phân loại
                                              hàng trăm phản ánh cư dân rồi
                                              chuyển đúng bộ phận.

  5     Vinpearl             AI-upgrade       Nhân viên CSKH phải tư vấn lịch
                                              trình, đặt phòng và giải đáp chính
                                              sách cho khách quốc tế bằng nhiều
                                              ngôn ngữ.
  -------------------------------------------------------------------------------

# Phase 2 --- QUICK-ASSESS

## QUICK PROBLEM CARD #1

**Bài toán:** Tự động phân loại và tóm tắt phản ánh của cư dân.

**Công ty thành viên:** Vinhomes

**Actor:** Nhân viên chăm sóc cư dân.

**Workflow thủ công hiện tại**

1.  Cư dân gửi phản ánh.
2.  Nhân viên đọc nội dung.
3.  Phân loại vấn đề.
4.  Chuyển bộ phận xử lý.
5.  Theo dõi trạng thái.

**Bottleneck:** Đọc và phân loại phản ánh (≈6 phút/ticket)

**AI hỗ trợ:** LLM tóm tắt, phân loại và đề xuất phòng ban.

**Success Metric**

-   Giảm thời gian từ 6 phút xuống dưới 1 phút/ticket.
-   Độ chính xác phân loại ≥95%.
-   Tỷ lệ chuyển sai \<3%.

**Quick Architecture:** LLM

------------------------------------------------------------------------

## QUICK PROBLEM CARD #2

**Bài toán:** Trợ lý AI hỗ trợ trả lời câu hỏi kỹ thuật và bảo hành xe.

**Công ty thành viên:** VinFast

**Actor:** Nhân viên tổng đài CSKH.

**Workflow**

1.  Nhận cuộc gọi.
2.  Nghe mô tả.
3.  Tra cứu tài liệu.
4.  Trả lời khách.
5.  Ghi chú.

**Bottleneck:** Tra cứu tài liệu (≈8 phút/cuộc gọi)

**AI hỗ trợ:** Agent (LLM + RAG) tìm tài liệu và sinh câu trả lời.

**Success Metric**

-   Giảm thời gian tra cứu từ 8 xuống dưới 2 phút.

-   90% câu hỏi được trả lời đúng ngay lần đầu.

-   Giảm 40% thời gian xử lý cuộc gọi.

**Quick Architecture:** Agent

------------------------------------------------------------------------

## QUICK PROBLEM CARD #3

**Bài toán:** Tự động tóm tắt hồ sơ bệnh án trước khi bác sĩ khám.

**Công ty thành viên:** Vinmec

**Actor:** Bác sĩ.

**Workflow**

1.  Mở hồ sơ.
2.  Đọc lịch sử khám.
3.  Đọc xét nghiệm.
4.  Ghi chú bệnh nền.
5.  Bắt đầu khám.

**Bottleneck:** Đọc hồ sơ (≈12 phút/bệnh nhân)

**AI hỗ trợ:** LLM tóm tắt lịch sử bệnh án và các chỉ số quan trọng.

**Success Metric**

-   Giảm thời gian đọc từ 12 xuống dưới 3 phút.
-   Độ đầy đủ thông tin ≥95%.
-   Giảm 50% thời gian chuẩn bị trước khám.

**Quick Architecture:** LLM (Human-in-the-loop)
>>>>>>> abc566be596c2553674b6a4e4aebd9ac0b7ec5ba
