Quyết định lựa chọn
Dự án AI được chọn

Tên bài toán: AI hỗ trợ tóm tắt hồ sơ bệnh án trước khi bác sĩ khám bệnh.

Công ty thành viên: Vinmec

Lý do lựa chọn:

Quy trình đọc hồ sơ bệnh án hiện tại tốn nhiều thời gian.
Hồ sơ bệnh án chứa nhiều dữ liệu văn bản, phù hợp với khả năng tóm tắt của LLM.
AI chỉ hỗ trợ tổng hợp thông tin, quyết định chuyên môn vẫn do bác sĩ đưa ra (Human-in-the-loop).
Có thể đo lường hiệu quả bằng thời gian chuẩn bị và mức độ đầy đủ của bản tóm tắt.
Phase 3.2 – Problem Statement (6-field)
Field	Nội dung
1. Actor / Operator	Bác sĩ khám bệnh tại Vinmec.
2. Current Workflow	Khi bệnh nhân đến khám, bác sĩ mở hồ sơ bệnh án điện tử (EMR), đọc tiền sử bệnh, kết quả xét nghiệm, đơn thuốc và các lần khám trước, sau đó tổng hợp thông tin quan trọng rồi mới bắt đầu khám và tư vấn. Quy trình hoàn toàn thủ công.
3. Bottleneck	Việc đọc và tổng hợp hồ sơ bệnh án mất nhiều thời gian, đặc biệt với bệnh nhân có lịch sử điều trị dài hoặc nhiều kết quả xét nghiệm. Trung bình mất khoảng 8–10 phút cho mỗi lượt khám.
4. Business Impact	Mỗi bác sĩ khám hàng chục bệnh nhân mỗi ngày. Việc dành quá nhiều thời gian đọc hồ sơ làm giảm số lượng bệnh nhân có thể khám, tăng thời gian chờ và ảnh hưởng đến trải nghiệm người bệnh.
5. Success Metric	(1) Giảm thời gian chuẩn bị từ 10 phút xuống dưới 2 phút. (2) Ít nhất 95% bản tóm tắt chứa đầy đủ các thông tin quan trọng (tiền sử bệnh, dị ứng, kết quả xét nghiệm nổi bật, thuốc đang sử dụng).
6. Operational Boundary	AI chỉ được phép tóm tắt và làm nổi bật thông tin trong hồ sơ bệnh án. Không được chẩn đoán bệnh, kê đơn hoặc đưa ra quyết định điều trị. Bác sĩ phải xem lại bản tóm tắt trước khi sử dụng trong quá trình khám (Human-in-the-loop).
Phase 3.3 – Future-State Flow & AI Fit
AI Fit
 Rule
 LLM Feature
 Agentic Loop

Lý do: Dữ liệu chủ yếu là văn bản y khoa và hồ sơ bệnh án, phù hợp với khả năng đọc hiểu và tóm tắt của LLM. AI chỉ đóng vai trò hỗ trợ, không tự đưa ra quyết định điều trị.

Future-State Flow
Bệnh nhân đến khám
        │
        ▼
Hệ thống EMR tự động lấy:
- Hồ sơ bệnh án
- Lịch sử khám
- Kết quả xét nghiệm
        │
        ▼
🔵 AI đọc và tóm tắt hồ sơ
- Tiền sử bệnh
- Dị ứng
- Thuốc đang dùng
- Kết quả bất thường
        │
        ▼
🟢 Bác sĩ xem lại bản tóm tắt
        │
        ▼
Khám và đưa ra chẩn đoán
        │
        ▼
Lưu kết quả khám vào EMR
Human-in-the-loop (HITL)
AI chỉ tạo bản tóm tắt.
Bác sĩ phải kiểm tra và xác nhận thông tin trước khi sử dụng.
Quyết định chẩn đoán và điều trị hoàn toàn do bác sĩ thực hiện.
Fallback

Nếu AI:

Không đọc được hồ sơ.
Thiếu dữ liệu.
Bản tóm tắt không đầy đủ.
Độ tin cậy thấp.

→ Bác sĩ quay lại quy trình cũ: đọc trực tiếp hồ sơ bệnh án điện tử và tự tổng hợp thông tin.

Phase 5 – EVALUATE
AI Readiness Checklist
 Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
Có. Dữ liệu gồm hồ sơ bệnh án điện tử (EMR), kết quả xét nghiệm, lịch sử khám và đơn thuốc.
 Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
Có. AI chỉ hỗ trợ tóm tắt, bác sĩ luôn xem lại trước khi sử dụng. Khi AI lỗi sẽ chuyển sang quy trình đọc hồ sơ thủ công.
 Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?
Có. AI chỉ hỗ trợ giảm thời gian chuẩn bị, không thay đổi vai trò của bác sĩ nên mức độ chấp nhận cao.
Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future
 GO (Bắt đầu xây dựng Prototype)
 NOT YET
 NO-GO
Justification

Dự án có tính khả thi cao vì dữ liệu hồ sơ bệnh án điện tử đã được lưu trữ trên hệ thống EMR và có thể tích hợp với mô hình LLM để tạo bản tóm tắt tự động. AI không thay thế bác sĩ mà chỉ hỗ trợ tổng hợp thông tin, giúp giảm đáng kể thời gian chuẩn bị trước khi khám trong khi vẫn đảm bảo an toàn nhờ cơ chế Human-in-the-loop.