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
