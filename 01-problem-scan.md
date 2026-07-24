# Lab 02 — Bài cá nhân: Scan & Quick Problem Cards

> Phạm vi: Phase 1 (SCAN) và Phase 2 (QUICK-ASSESS).
>
> Lưu ý về số liệu: các con số thời gian và tỷ lệ bên dưới là baseline giả định
> phục vụ scoping ban đầu, chưa phải số liệu vận hành chính thức. Trước khi quyết
> định đầu tư, nhóm dự án cần xác minh bằng log hệ thống và time study trong 2–4
> tuần.

## Phase 1 — SCAN

| # | Công ty thành viên | Lens chính | Bài toán/bottleneck quan sát được |
|---:|---|---|---|
| 1 | Xanh SM | Stakeholder Pain, Time-consuming | Khi xe điện gần cạn pin giữa ca, tài xế phải mô tả vị trí và tình trạng qua nhiều lượt trao đổi; điều phối viên tra cứu trạm, đánh giá rủi ro và soạn hướng dẫn thủ công, dễ chậm trong tình huống khẩn cấp. |
| 2 | VinFast | Repetitive, Time-consuming | Nhân viên hậu mãi đọc mô tả lỗi, lịch sử bảo dưỡng và ảnh đính kèm để phân loại yêu cầu bảo hành rồi chuyển đúng xưởng/nhóm kỹ thuật. |
| 3 | Vinhomes | AI-upgrade, Stakeholder Pain | Phản ánh của cư dân đến từ ứng dụng, hotline và email; nhân viên phải gộp nội dung trùng, xác định mức khẩn cấp và soạn phản hồi ban đầu. |
| 4 | Vinmec | Time-consuming, Stakeholder Pain | Trước lịch khám, nhân viên kiểm tra thủ công hồ sơ người bệnh để phát hiện biểu mẫu hoặc tài liệu còn thiếu, sau đó liên hệ bổ sung. |
| 5 | Vinpearl/VinWonders | Repetitive, AI-upgrade | Nhân viên CSKH trả lời lặp lại các câu hỏi đa ngôn ngữ về giờ mở cửa, điều kiện vé, dịch vụ và quy trình đổi lịch; các trường hợp ngoại lệ vẫn phải chuyển người phụ trách. |
| 6 | VinFast | AI-upgrade | Kỹ thuật viên phải rà soát nhiều dòng log chẩn đoán để tóm tắt dấu hiệu bất thường trước khi kiểm tra xe thực tế. |

### Tiêu chí chọn top 3

Ba bài toán được chọn ưu tiên các tình huống có tần suất lặp lại, đầu vào ngôn
ngữ tự nhiên, metric đo được, phạm vi thử nghiệm hẹp và ranh giới con người phê
duyệt rõ ràng:

1. Hỗ trợ điều phối xe Xanh SM khi pin ở mức nguy cấp.
2. Phân loại phản ánh cư dân Vinhomes và soạn phản hồi ban đầu.
3. Trợ lý CSKH đa ngôn ngữ cho Vinpearl/VinWonders.

## Phase 2 — QUICK-ASSESS

### Quick Problem Card #1 — Điều phối hỗ trợ xe điện gần cạn pin

```text
+----------------------------------------------------------------------------+
| QUICK PROBLEM CARD #1                                                      |
| ĐIỀU PHỐI HỖ TRỢ XE ĐIỆN GẦN CẠN PIN — XANH SM (GSM)                       |
+----------------------------------------------------------------------------+
| BÀI TOÁN                                                                   |
| Rút ngắn thời gian điều phối hỗ trợ an toàn khi pin xe xuống mức nguy cấp. |
+----------------------------------------------------------------------------+
| ACTOR / OPERATOR                                                           |
| Điều phối viên đội xe; tài xế là người trực tiếp chịu rủi ro chờ xử lý.    |
+----------------------------------------------------------------------------+
| WORKFLOW THỦ CÔNG HIỆN TẠI                                                 |
| Báo vị trí + mức pin → Xác minh → Tra cứu nguồn hỗ trợ                     |
|                         → Đánh giá rủi ro → Soạn phương án                  |
+----------------------------------------------------------------------------+
| BOTTLENECK                                                                 |
| Tra cứu, đánh giá và soạn phương án: 8–12 phút/lượt (baseline giả định).   |
+----------------------------------------------------------------------------+
| AI CÓ THỂ HỖ TRỢ                                                          |
| Chuẩn hóa sự cố → Nhận diện pin < 5% → Tạo bản nháp điều xe sạc lưu động.  |
+----------------------------------------------------------------------------+
| METRIC THÀNH CÔNG                                                         |
| • Thời gian tạo phương án: 8–12 phút → ≤ 2 phút                           |
| • 100% trường hợp pin < 5% không gợi ý trạm xa hơn 5 km                   |
| • 100% đầu ra bắt đầu bằng [DRAFT_ONLY]                                   |
+----------------------------------------------------------------------------+
| QUICK ARCHITECTURE                                                         |
| RULE + LLM + HUMAN-IN-THE-LOOP                                             |
| Rule kiểm tra pin/khoảng cách → LLM soạn nháp → Con người duyệt.           |
+----------------------------------------------------------------------------+
| RANH GIỚI                                                                  |
| AI không tự gửi tin, tự điều xe hoặc đoán dữ liệu còn thiếu.               |
+----------------------------------------------------------------------------+
```

### Quick Problem Card #2 — Phân loại phản ánh cư dân và soạn phản hồi

```text
+----------------------------------------------------------------------------+
| QUICK PROBLEM CARD #2                                                      |
| PHÂN LOẠI PHẢN ÁNH CƯ DÂN VÀ SOẠN PHẢN HỒI — VINHOMES                     |
+----------------------------------------------------------------------------+
| BÀI TOÁN                                                                   |
| Hợp nhất, phân loại và soạn phản hồi đầu tiên cho phản ánh từ nhiều kênh.  |
+----------------------------------------------------------------------------+
| ACTOR / OPERATOR                                                           |
| Nhân viên chăm sóc cư dân và bộ phận vận hành tòa nhà/khu đô thị.          |
+----------------------------------------------------------------------------+
| WORKFLOW THỦ CÔNG HIỆN TẠI                                                 |
| Nhận phản ánh → Nhập lại → Kiểm tra trùng → Gắn mức ưu tiên                |
|                                              → Soạn và chuyển xử lý         |
+----------------------------------------------------------------------------+
| BOTTLENECK                                                                 |
| Đọc, chuẩn hóa và phân loại: 6–10 phút/ticket (baseline giả định).         |
+----------------------------------------------------------------------------+
| AI CÓ THỂ HỖ TRỢ                                                          |
| Tóm tắt → Gợi ý ticket trùng → Đề xuất nhãn → Soạn phản hồi ban đầu.       |
+----------------------------------------------------------------------------+
| METRIC THÀNH CÔNG                                                         |
| • ≥ 85% ticket được gợi ý đúng nhóm ở top-1                               |
| • Thời gian xử lý ban đầu: 6–10 phút → ≤ 3 phút/ticket                    |
| • 100% sự cố cháy, an ninh hoặc y tế được chuyển người trực ngay          |
+----------------------------------------------------------------------------+
| QUICK ARCHITECTURE                                                         |
| RULE + LLM + HUMAN-IN-THE-LOOP                                             |
| Rule bắt sự cố khẩn → LLM xử lý ngôn ngữ → Nhân viên xác nhận.             |
+----------------------------------------------------------------------------+
| RANH GIỚI                                                                  |
| Không tự hứa bồi thường, kết luận trách nhiệm, đóng ticket hoặc lộ dữ liệu.|
+----------------------------------------------------------------------------+
```

### Quick Problem Card #3 — Trợ lý CSKH đa ngôn ngữ về vé và dịch vụ

```text
+----------------------------------------------------------------------------+
| QUICK PROBLEM CARD #3                                                      |
| TRỢ LÝ CSKH ĐA NGÔN NGỮ VỀ VÉ VÀ DỊCH VỤ — VINPEARL / VINWONDERS          |
+----------------------------------------------------------------------------+
| BÀI TOÁN                                                                   |
| Trả lời nhanh, nhất quán, đa ngôn ngữ cho các câu hỏi phổ biến của khách.  |
+----------------------------------------------------------------------------+
| ACTOR / OPERATOR                                                           |
| Nhân viên CSKH qua chat/email; khách du lịch là người nhận phản hồi.       |
+----------------------------------------------------------------------------+
| WORKFLOW THỦ CÔNG HIỆN TẠI                                                 |
| Nhận câu hỏi → Xác định ngôn ngữ → Tra cứu FAQ → Soạn/dịch                |
|                                                     → Gửi hoặc chuyển cấp   |
+----------------------------------------------------------------------------+
| BOTTLENECK                                                                 |
| Tra cứu và soạn/dịch: 5–8 phút/yêu cầu (baseline giả định).               |
+----------------------------------------------------------------------------+
| AI CÓ THỂ HỖ TRỢ                                                          |
| Truy xuất FAQ đã duyệt → Soạn đúng ngôn ngữ → Nêu nguồn → Chuyển ngoại lệ. |
+----------------------------------------------------------------------------+
| METRIC THÀNH CÔNG                                                         |
| • Thời gian tạo bản nháp: 5–8 phút → ≤ 60 giây                            |
| • ≥ 90% câu trả lời FAQ đúng theo bộ kiểm thử                             |
| • 100% yêu cầu đổi/hoàn tiền ngoại lệ được chuyển nhân viên               |
+----------------------------------------------------------------------------+
| QUICK ARCHITECTURE                                                         |
| RAG + LLM + RULE + HUMAN REVIEW                                            |
| Kho FAQ phiên bản hóa → LLM soạn nháp → Rule chặn giao dịch/ngoại lệ.      |
+----------------------------------------------------------------------------+
| RANH GIỚI                                                                  |
| Không tự sửa booking, duyệt hoàn tiền hoặc tạo ra chính sách và mức giá.   |
+----------------------------------------------------------------------------+
```

## Kết luận cá nhân

Bài toán Xanh SM được ưu tiên cao nhất cho prototype vì phạm vi nhỏ, có hai quy
tắc an toàn kiểm thử được ngay và tác động thời gian rõ ràng. Tuy nhiên, rủi ro
an toàn cũng cao nhất, nên kiến trúc phù hợp là **Rule + LLM + Human-in-the-loop**,
không phải agent tự chủ. Hai bài toán Vinhomes và Vinpearl phù hợp cho pilot sau
khi có bộ dữ liệu mẫu đã ẩn thông tin cá nhân và bộ tiêu chí đánh giá nhãn/câu
trả lời.
