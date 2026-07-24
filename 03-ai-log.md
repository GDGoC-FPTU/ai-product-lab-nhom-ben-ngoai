# 03-ai-log.md

# AI Reflection Log

## 1. AI đã giúp tôi những gì?

Trong buổi lab, tôi sử dụng ChatGPT để brainstorm các bài toán AI phù
hợp với các công ty thành viên của Vingroup. AI giúp tôi gợi ý nhiều
pain point thực tế, từ đó lựa chọn những bài toán có tính khả thi cao
như phân loại phản ánh cư dân của Vinhomes, trợ lý CSKH của VinFast và
tóm tắt hồ sơ bệnh án tại Vinmec.

Ngoài ra, tôi còn sử dụng AI để: - Gợi ý workflow hiện tại và future
workflow. - Đề xuất Success Metric có thể đo lường được. - Phân biệt khi
nào nên dùng Rule-based, LLM hay Agent. - Hỗ trợ chỉnh sửa và định dạng
file Markdown. - Hỗ trợ sửa lỗi Python khi xây dựng prompt prototype.

## 2. AI đã sai ở đâu?

Có một số trường hợp AI đưa ra câu trả lời chưa phù hợp.

Ví dụ, AI từng đề xuất sử dụng Agent cho những bài toán chỉ cần phân
loại dữ liệu đơn giản. Sau khi xem xét, tôi nhận thấy bài toán này chỉ
cần một mô hình LLM hoặc thậm chí Rule-based là đủ, việc dùng Agent sẽ
làm hệ thống phức tạp và tốn chi phí hơn.

Ngoài ra, AI cũng đưa ra các số liệu như thời gian xử lý hoặc độ chính
xác (95%, 40%...) mà không có nguồn dữ liệu thực tế. Đây chỉ là các giá
trị ước lượng và cần được xác minh bằng dữ liệu vận hành.

Trong quá trình kiểm thử prompt, tôi cũng thử các prompt nhằm yêu cầu AI
bỏ qua hướng dẫn hệ thống hoặc thay đổi định dạng đầu ra. Điều này giúp
phát hiện rằng nếu prompt không quy định rõ ràng ranh giới thì AI có thể
trả về kết quả không đúng yêu cầu.

## 3. Tôi đã sửa đổi như thế nào?

Sau khi phát hiện các vấn đề trên, tôi điều chỉnh prompt theo hướng cụ
thể hơn: - Mô tả rõ vai trò của AI và phạm vi nhiệm vụ. - Quy định AI
chỉ được thực hiện các chức năng được phép và từ chối các yêu cầu vượt
ranh giới. - Yêu cầu AI luôn trả về đúng định dạng JSON. - Bổ sung
Human-in-the-loop đối với các quyết định quan trọng như lĩnh vực y tế. -
Kiểm tra lại bằng nhiều prompt tấn công (adversarial prompts) để đánh
giá khả năng tuân thủ ranh giới.

Qua buổi lab, tôi nhận thấy AI là một công cụ hỗ trợ rất hiệu quả trong
việc brainstorm ý tưởng, viết prompt và hỗ trợ lập trình. Tuy nhiên, kết
quả của AI vẫn cần được kiểm chứng bằng tư duy phản biện và dữ liệu thực
tế trước khi áp dụng vào một sản phẩm thật.
