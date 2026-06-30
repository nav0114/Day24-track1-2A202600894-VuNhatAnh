# Case 03 — Tutor CoPilot: Human-AI tutoring support

## A. Brief Case

| Field | Nội dung |
|---|---|
| Tên case | Tutor CoPilot |
| Ngành | Giáo dục / AI tutor |
| Tổ chức / sản phẩm | Tutor CoPilot, nghiên cứu bởi Rose E. Wang và cộng sự; hợp tác với FEV Tutor và một school district ở miền Nam Hoa Kỳ |
| Use case AI | AI hỗ trợ tutor trong phiên dạy live bằng cách gợi ý chiến lược sư phạm và câu trả lời theo thời gian thực. Tutor là người chọn, chỉnh sửa hoặc bỏ qua gợi ý trước khi gửi cho học sinh. |
| Thời điểm | Nghiên cứu bắt đầu cuối tháng 03/2024, kéo dài 2 tháng; preprint 10/2024. |
| Case xảy ra chuyện gì? | Tutor CoPilot được thử nghiệm trong live tutoring K-12. Kết quả cho thấy học sinh có tutor được hỗ trợ bởi AI có xác suất mastery topic cao hơn, đặc biệt khi tutor ban đầu có rating thấp hơn. Tuy vậy, phỏng vấn tutor cũng ghi nhận vấn đề như gợi ý chưa phù hợp grade-level, cho thấy human-in-the-loop giảm rủi ro nhưng không loại bỏ hoàn toàn lỗi chất lượng sư phạm. |
| Stakeholder bị ảnh hưởng | Học sinh K-12, tutor, trường/district, nhà cung cấp tutoring. |
| Số liệu chính | RCT liên quan khoảng **900 tutor** và **1,800 học sinh K-12** từ cộng đồng under-served; kết quả tăng **4 percentage points** về khả năng mastery topic, nhóm tutor lower-rated tăng đến **9 percentage points**; phân tích hơn **550,000 messages**; chi phí ước tính khoảng **20 USD/tutor/năm**. |
| Trích nguồn ngắn | Tutor CoPilot là ví dụ AI có human-in-the-loop: tăng chất lượng tutoring nhưng vẫn có rủi ro nếu gợi ý không đúng trình độ học sinh hoặc tutor quá tin vào AI. |
| Nguồn 1 | Primary preprint — arXiv, “Tutor CoPilot: A Human-AI Approach for Scaling Real-Time Expertise”, 03/10/2024: https://arxiv.org/abs/2410.03017 |
| Nguồn 2 | OSF preregistration được paper nhắc tới: https://osf.io/8d6ha |
| Ghi chú độ tin cậy | Đây là nguồn primary và có preregistration, nhưng vẫn là preprint/arXiv, chưa mạnh bằng paper peer-reviewed. Điểm tốt là có số liệu RCT, quy mô mẫu, message analysis và mô tả rõ safety/privacy design. |

## B. Harm Map Worksheet

| High-risk moment | Stakeholder bị ảnh hưởng | Failure mode | Layer bắt đầu lỗi | Harm xảy ra là gì? | Harm lens | Severity | Scale | Probability | Frequency | Vì sao? |
|---|---|---|---|---|---|---|---|---|---|---|
| AI gợi ý câu trả lời không phù hợp grade-level | Học sinh, tutor | Hallucination / Bad pedagogy | Model / Grounding | Học sinh nhận lời giải quá khó/quá dễ, không đúng trình độ | Learning quality / Opportunity loss | **Medium** | **Medium** | **Medium** | **Medium** | Paper ghi nhận tutor flag vấn đề về grade-level language. Có human tutor nên severity giảm, nhưng nếu tutor mới quá tin AI thì vẫn gây hại. |
| Tutor dùng gợi ý AI mà không kiểm tra kỹ | Học sinh | Over-reliance | UX / Human factors | Tutor mất autonomy, gửi gợi ý chưa phù hợp hoặc cho đáp án quá nhanh | Opportunity loss | **Medium → High** | **Medium** | **Medium** | **Medium** | Human-in-the-loop chỉ hiệu quả nếu human thật sự review. Với novice tutor, AI có thể vừa hỗ trợ vừa tạo phụ thuộc. |
| Dữ liệu phiên tutoring gửi sang external LM service | Học sinh, tutor | Privacy leak | Data / Safety | Conversation context bị chia sẻ quá rộng hoặc không de-identify đủ | Privacy loss | **High** | **Medium** | **Low → Medium** | **Medium** | Paper đã nêu biện pháp de-identify tên và giới hạn 10 messages gần nhất, nên probability thấp hơn, nhưng dữ liệu trẻ em vẫn nhạy cảm. |
| Product team tối ưu cost/scale và bỏ qua quality monitoring | Học sinh underserved | Escalation failure | Governance / Evaluation | AI mở rộng nhanh nhưng không phát hiện lỗi sư phạm theo từng nhóm học sinh | Unequal support | **High** | **High** | **Medium** | **Medium** | Case có lợi ích lớn cho under-served students, nhưng nếu kiểm soát kém có thể tạo hỗ trợ không đồng đều cho nhóm vốn đã dễ bị thiệt thòi. |

## C. Nhận xét case

Tutor CoPilot cho thấy hướng thiết kế an toàn hơn cho AI trong giáo dục: **AI hỗ trợ người dạy, không thay thế người dạy**. Tuy nhiên, case này cũng nhắc rằng human-in-the-loop không phải “lá chắn tự động”. Product vẫn cần UX buộc tutor review, log việc AI suggestion có được chỉnh sửa không, benchmark grade-level appropriateness, và cơ chế báo lỗi nhanh từ tutor.

## D. Product Recommendation / Fix First

Tutor CoPilot là case tích cực hơn vì AI hỗ trợ tutor thay vì trả lời trực tiếp cho học sinh. Tuy nhiên, để human-in-the-loop thật sự hiệu quả, product team vẫn cần thiết kế UX, logging và quality control rất rõ.

### 1. Làm rõ vai trò của AI: suggest, not decide

AI chỉ nên là người gợi ý. Tutor phải là người quyết định cuối cùng. UX nên thể hiện rõ:

- Đây là suggestion, không phải đáp án bắt buộc.
- Tutor có thể chỉnh sửa trước khi gửi.
- Tutor có thể bỏ qua suggestion.
- Tutor có thể report suggestion không phù hợp.
- AI không được tự động gửi nội dung cho học sinh.

Nếu AI suggestion được gửi tự động hoặc quá dễ bấm gửi mà không đọc, human-in-the-loop sẽ yếu đi.

### 2. Ghi nhận accept / edit / reject

Product nên log cách tutor tương tác với từng AI suggestion:

| Hành động | Ý nghĩa |
|---|---|
| Accept without edit | Tutor tin hoàn toàn vào AI |
| Edit before send | Tutor dùng AI như draft và có review |
| Reject | AI suggestion không hữu ích hoặc không phù hợp |
| Report | Có lỗi chất lượng/safety cần kiểm tra |
| Ignore | Tutor không cần hỗ trợ ở thời điểm đó |

Những log này giúp product team đo automation bias. Nếu tỉ lệ “accept without edit” quá cao ở tutor mới, có thể tutor đang phụ thuộc AI.

### 3. Kiểm tra grade-level appropriateness

Paper ghi nhận vấn đề gợi ý chưa phù hợp grade-level. Đây là rủi ro quan trọng trong giáo dục K-12. Product nên có kiểm tra tự động:

- Câu trả lời có quá khó so với lớp không?
- Từ vựng có phù hợp độ tuổi không?
- Lời giải có bỏ qua bước nền tảng không?
- Có dùng khái niệm học sinh chưa học không?
- Có giải thích đủ đơn giản không?

Có thể thêm một rubric trước khi suggestion hiện cho tutor:

| Tiêu chí | Câu hỏi kiểm tra |
|---|---|
| Grade-level fit | Học sinh lớp này có hiểu được không? |
| Pedagogical quality | Suggestion có hỏi dẫn dắt hay chỉ cho đáp án? |
| Student context | Suggestion có bám vào lỗi hiện tại của học sinh không? |
| Safety | Có nội dung không phù hợp không? |
| Clarity | Tutor có thể dùng ngay không? |

### 4. Thiết kế suggestion theo chiến lược sư phạm

AI không nên chỉ viết một câu trả lời. AI nên gợi ý theo loại chiến lược:

- Ask a guiding question.
- Break the problem into smaller steps.
- Diagnose misconception.
- Give a simpler example.
- Encourage student to explain their reasoning.
- Check understanding.
- Avoid giving away the answer.

Khi suggestion có nhãn chiến lược, tutor dễ hiểu vì sao AI đề xuất như vậy và dễ chọn cách phù hợp.

### 5. Privacy minimization trong live tutoring

Dù case này đã có de-identification và giới hạn context, live tutoring vẫn có dữ liệu nhạy cảm. Product nên tiếp tục giảm rủi ro:

- Chỉ gửi vài message gần nhất, không gửi toàn bộ lịch sử nếu không cần.
- Redact tên học sinh, email, phone, địa chỉ, school ID.
- Không gửi thông tin gia đình hoặc thông tin sức khỏe/tâm lý nếu không liên quan.
- Có policy rõ về retention log.
- Có quyền xóa/anonymize dữ liệu sau thời gian cần thiết.
- Tách log phục vụ product analytics khỏi dữ liệu nhận dạng học sinh.

### 6. Feedback loop từ tutor

Tutor là người gần học sinh nhất trong workflow này. Product nên tạo feedback loop nhanh:

- Nút “Not grade appropriate”.
- Nút “Too much answer”.
- Nút “Too vague”.
- Nút “Unsafe / sensitive”.
- Nút “Good suggestion”.
- Ô ghi chú ngắn cho tutor.

Các report này nên được dùng để cải thiện prompt, retrieval, rubric và evaluation set.

### 7. Monitoring theo nhóm tutor và nhóm học sinh

Vì Tutor CoPilot có lợi ích lớn hơn với lower-rated tutors, product team cần theo dõi rủi ro không đồng đều:

| Nhóm cần theo dõi | Lý do |
|---|---|
| Tutor mới | Dễ phụ thuộc AI hơn |
| Tutor rating thấp | AI giúp nhiều nhưng cũng dễ bị automation bias |
| Học sinh under-served | Cần đảm bảo hỗ trợ không thấp chất lượng |
| Học sinh grade thấp | Dễ bị ảnh hưởng bởi ngôn ngữ quá khó |
| Môn/chủ đề khó | Dễ phát sinh suggestion sai hoặc quá trực tiếp |

Monitoring theo nhóm giúp phát hiện nếu AI cải thiện trung bình nhưng gây hại cho một subgroup.

### 8. Evaluation trước khi mở rộng

Trước khi scale, nên có evaluation định kỳ:

| Evaluation | Mục tiêu |
|---|---|
| Suggestion quality audit | Đánh giá suggestion có đúng, rõ, phù hợp sư phạm không |
| Grade-level audit | Kiểm tra ngôn ngữ và độ khó |
| Answer leakage audit | Kiểm tra AI có cho đáp án quá nhanh không |
| Tutor behavior audit | Kiểm tra tutor có review thật không |
| Student outcome analysis | Đo mastery, retention, engagement |
| Privacy audit | Kiểm tra context gửi sang model có chứa PII không |

### Kết luận recommendation

Ưu tiên số 1 của Tutor CoPilot là làm human-in-the-loop trở thành **workflow thật**, không chỉ là nhãn an toàn. AI nên giúp tutor tốt hơn, nhưng product phải đo được tutor có review không, suggestion có đúng level không, dữ liệu học sinh có được giảm thiểu không, và nhóm học sinh yếu hơn có thật sự được hỗ trợ tốt hơn không.