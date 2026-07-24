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
