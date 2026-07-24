# 02-problem-deep-dive.md

# 🗳️ Quyết định lựa chọn của nhóm

**Bài toán được chọn:** Vinmec - Tự động tóm tắt hồ sơ bệnh án trước khi
bác sĩ khám.

## Lý do lựa chọn

-   Đây là tác vụ lặp lại hằng ngày và tốn nhiều thời gian của bác sĩ.
-   AI có thế mạnh trong việc đọc, tổng hợp và tóm tắt văn bản dài.
-   AI chỉ đóng vai trò hỗ trợ, quyết định chuyên môn vẫn thuộc về bác
    sĩ nên rủi ro được kiểm soát.

------------------------------------------------------------------------

# 🏗️ Phase 3 --- DEEP-DIVE

## 3.1 Current-State Workflow

``` text
Bệnh nhân đến khám
      │
      ▼
Bác sĩ mở hồ sơ bệnh án điện tử
      │
      ▼
Đọc lịch sử khám, đơn thuốc, kết quả xét nghiệm 🔴 (8 phút)
      │
      ▼
Tự tổng hợp thông tin quan trọng 🔴 (4 phút)
      │
      ▼
Khám và đưa ra chẩn đoán

⏱ Tổng thời gian chuẩn bị: khoảng 12 phút/bệnh nhân
```

------------------------------------------------------------------------

## 3.2 Problem Statement (6-field)

  -----------------------------------------------------------------------
  Field                               Nội dung
  ----------------------------------- -----------------------------------
  **1. Actor / Operator**             Bác sĩ khám bệnh tại Vinmec.

  **2. Current Workflow**             Bác sĩ mở hồ sơ bệnh án điện tử,
                                      đọc lịch sử khám, kết quả xét
                                      nghiệm, đơn thuốc và tự tổng hợp
                                      thông tin trước khi bắt đầu khám.

  **3. Bottleneck**                   Việc đọc và tổng hợp hồ sơ bệnh án
                                      dài, mất khoảng 12 phút/bệnh nhân
                                      và dễ bỏ sót thông tin quan trọng.

  **4. Business Impact**              Giảm số lượng bệnh nhân được khám
                                      mỗi ngày, tăng thời gian chờ của
                                      bệnh nhân và làm tăng áp lực cho
                                      bác sĩ.

  **5. Success Metric**               Giảm thời gian chuẩn bị từ 12 phút
                                      xuống dưới 3 phút; độ đầy đủ thông
                                      tin tóm tắt đạt ≥95%; giảm ít nhất
                                      50% thời gian chuẩn bị trước khám.

  **6. Operational Boundary**         AI chỉ được tóm tắt hồ sơ và làm
                                      nổi bật thông tin quan trọng. AI
                                      không được chẩn đoán bệnh, kê đơn
                                      hoặc đưa ra quyết định điều trị.
                                      Bác sĩ phải xem xét và phê duyệt
                                      kết quả (Human-in-the-loop).
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 3.3 Future-State Flow & AI Fit

**AI Fit:** LLM Feature

``` text
Bệnh nhân đến khám
      │
      ▼
Bác sĩ mở hồ sơ
      │
      ▼
🔵 AI tự động đọc toàn bộ hồ sơ
      │
      ▼
🔵 AI tạo bản tóm tắt bệnh án
      │
      ▼
🟢 Bác sĩ xem và phê duyệt
      │
      ▼
Khám bệnh

↩️ Fallback:
Nếu AI lỗi hoặc thiếu thông tin,
bác sĩ đọc hồ sơ theo quy trình cũ.
```

------------------------------------------------------------------------

# 🏁 Phase 5 --- EVALUATE

## AI Readiness Checklist

-   [x] Có dữ liệu hồ sơ bệnh án điện tử để thử nghiệm.
-   [x] Có Human-in-the-loop nên rủi ro được kiểm soát.
-   [ ] Cần làm sạch và ẩn danh dữ liệu trước khi huấn luyện.

## Quyết định

**GO (Prototype với phạm vi hẹp)**

## Justification

Bài toán có giá trị thực tế vì bác sĩ dành nhiều thời gian đọc hồ sơ
bệnh án. Mô hình LLM phù hợp với tác vụ tóm tắt văn bản y khoa, trong
khi quyết định chuyên môn vẫn do bác sĩ thực hiện nên rủi ro thấp.

Giai đoạn đầu chỉ cần xây dựng prototype trên dữ liệu đã ẩn danh. Chi
phí chủ yếu gồm hạ tầng GPU và API LLM để thử nghiệm, không cần triển
khai hệ thống agent phức tạp. Nếu kết quả đạt mục tiêu (thời gian chuẩn
bị dưới 3 phút và độ đầy đủ ≥95%), dự án có thể mở rộng sang nhiều
chuyên khoa khác.
