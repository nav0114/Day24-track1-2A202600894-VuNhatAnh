# Cross-case Patterns — Giáo dục / AI tutor

## 1. Nhìn chung về 3 case

| Case | Rủi ro nổi bật | Failure mode chính | Layer hay bắt đầu lỗi |
|---|---|---|---|
| LAUSD Ed AI chatbot / AllHere | Dữ liệu học sinh, vendor risk, rollout scale lớn | Privacy leak, escalation failure | Data / Safety / Governance |
| GPT-4 math tutor without guardrails | Học sinh phụ thuộc AI, học kém bền vững | Over-reliance, answer leakage, measurement failure | UX / Prompt / Evaluation |
| Tutor CoPilot | Gợi ý sư phạm chưa đúng level, tutor quá tin AI | Grade-level mismatch, over-reliance, privacy risk | Model / Grounding / UX |

## 2. Pattern 1 — AI tutor dễ trở thành “answer machine”

Rủi ro lặp lại rõ nhất là AI có thể giúp học sinh hoàn thành bài nhanh hơn nhưng không chắc giúp học sinh học thật. Trong case GPT-4 math tutor without guardrails, điểm practice tăng trong lúc học sinh có AI, nhưng khi AI bị lấy đi thì nhóm dùng GPT Base làm kém hơn nhóm không có AI. Điều này cho thấy short-term performance không đủ để chứng minh learning outcome.

Với AI tutor, harm không phải lúc nào cũng là một câu trả lời sai. Harm có thể là học sinh hình thành thói quen hỏi AI để lấy đáp án, không luyện reasoning, không tự sửa lỗi và không phát triển kỹ năng giải quyết vấn đề.

**Product implication:** AI tutor phải được thiết kế theo hướng **tutor-not-solver**. Nghĩa là AI ưu tiên hỏi dẫn dắt, gợi ý từng bước, kiểm tra hiểu bài, và chỉ đưa lời giải đầy đủ khi thật sự cần.

## 3. Pattern 2 — Dữ liệu học sinh là điểm rủi ro lớn

Case LAUSD Ed cho thấy khi AI tutor cá nhân hóa, hệ thống thường cần dùng dữ liệu học sinh như điểm số, attendance, lớp học, nhu cầu học tập hoặc lịch sử tương tác. Đây là dữ liệu nhạy cảm vì liên quan đến trẻ em và có thể ảnh hưởng đến cách nhà trường/phụ huynh nhìn nhận học sinh.

Rủi ro không chỉ là “model có nhớ dữ liệu không”, mà còn là:

- Dữ liệu nào được đưa vào prompt?
- Có cần gửi toàn bộ dữ liệu đó không?
- Dữ liệu có được de-identify không?
- Vendor nào xử lý dữ liệu?
- Log được lưu bao lâu?
- Khi vendor gặp sự cố, ai chịu trách nhiệm?
- Có audit trail và kill switch không?

**Product implication:** Privacy by design phải được làm từ đầu, không phải thêm sau. AI tutor nên dùng data minimization, de-identification, access control, audit log và vendor review trước khi rollout.

## 4. Pattern 3 — Human-in-the-loop chỉ hiệu quả nếu được thiết kế thật

Tutor CoPilot là case tích cực hơn vì AI không trả lời trực tiếp cho học sinh mà gợi ý cho tutor. Tutor vẫn là người chọn, chỉnh sửa hoặc bỏ qua gợi ý. Tuy nhiên, case này cũng cho thấy human-in-the-loop không tự động làm hệ thống an toàn.

Nếu UX khiến tutor chỉ bấm gửi nhanh, nếu tutor không biết AI có thể sai, hoặc nếu không log tỉ lệ accept/edit/reject, thì human review có thể trở thành hình thức. Đặc biệt với tutor mới hoặc tutor rating thấp, AI vừa có thể hỗ trợ rất tốt, vừa có thể tạo automation bias.

**Product implication:** Human-in-the-loop cần có cơ chế bắt buộc review, nút reject/report, giải thích vì sao AI gợi ý như vậy, và monitoring xem human có thật sự chỉnh sửa output không.

## 5. Pattern 4 — Evaluation sai sẽ dẫn đến quyết định rollout sai

Trong giáo dục, metric dễ bị đánh lừa nhất là điểm ngắn hạn. Nếu chỉ đo học sinh làm đúng bao nhiêu câu trong lúc có AI, product team có thể tưởng hệ thống tốt. Nhưng case GPT-4 math tutor cho thấy cần đo thêm khả năng tự làm khi không có AI.

Với AI tutor, các metric cần đo gồm:

| Nhóm metric | Cần đo gì? |
|---|---|
| Learning outcome | Retention, transfer, khả năng tự làm khi không có AI |
| Tutor behavior | AI có cho đáp án quá sớm không, có hỏi dẫn dắt không |
| Safety | Có trả lời nội dung ngoài phạm vi, độc hại, hoặc không phù hợp tuổi không |
| Grounding | Có bám curriculum/SGK/lesson objective không |
| Privacy | Có đưa PII vào prompt/log/output không |
| Equity | Nhóm học sinh yếu hơn có được hỗ trợ tốt hơn hay bị bỏ lại không |
| Human review | Giáo viên/tutor có chỉnh sửa output AI không, tỉ lệ reject/report là bao nhiêu |

**Product implication:** Trước khi ship rộng, AI tutor phải có evaluation theo cả short-term performance và long-term learning.

## 6. Pattern 5 — Scale làm harm nhỏ trở thành harm lớn

Trong giáo dục, một lỗi nhỏ có thể lặp lại hàng nghìn lần nếu sản phẩm được triển khai theo district hoặc nền tảng online. Một gợi ý sai level có thể không nghiêm trọng với một học sinh, nhưng nếu xảy ra đều đặn trong nhiều phiên học, nó tạo learning gap. Một lỗi privacy nhỏ cũng trở nên nghiêm trọng nếu liên quan đến dữ liệu của hàng trăm nghìn học sinh.

**Product implication:** Rollout AI tutor nên đi từ pilot nhỏ, có monitoring, có threshold dừng rollout, có rollback plan, và có review định kỳ theo từng nhóm học sinh.

## 7. Pattern rủi ro chung của ngành

Risk profile của ngành **Giáo dục / AI tutor** là **High**.

Ngành này thường không có physical injury trực tiếp như y tế hoặc autonomous driving, nhưng có 4 nhóm rủi ro rất đáng chú ý:

1. **Learning loss:** Học sinh phụ thuộc AI, không học bền vững.
2. **Opportunity loss:** Học sinh nhận hỗ trợ sai level, sai nhu cầu, hoặc bị định hướng sai.
3. **Privacy loss:** Dữ liệu học sinh/trẻ em bị dùng quá mức hoặc chia sẻ cho vendor không rõ.
4. **Trust loss:** Phụ huynh, giáo viên và học sinh mất niềm tin nếu AI bị tắt, trả lời sai, hoặc bị phát hiện xử lý dữ liệu không minh bạch.

## 8. Nếu là team sản phẩm, tôi sẽ sửa gì trước?

Ưu tiên sửa theo thứ tự:

1. **Thiết kế tutor-not-solver:** Không cho AI đưa đáp án ngay. AI phải hỏi dẫn dắt, gợi ý từng bước, và kiểm tra hiểu bài.
2. **Grounding theo curriculum:** AI phải bám bài học, level, vocabulary, mục tiêu buổi học và năng lực hiện tại của học sinh.
3. **Privacy minimization:** Chỉ gửi dữ liệu tối thiểu cần thiết vào model. Không đưa PII vào prompt nếu không cần.
4. **Human escalation:** Khi AI không chắc, khi học sinh bế tắc lâu, hoặc khi có tín hiệu nhạy cảm, phải chuyển cho giáo viên/phụ huynh/counselor.
5. **Evaluation thật:** Đo retention, transfer, answer leakage, grade-level appropriateness, hallucination, privacy leakage.
6. **Pilot trước rollout:** Chạy thử ở nhóm nhỏ, có monitoring và rollback trước khi mở rộng.

## 9. Red flags trước khi ship AI tutor

Không nên ship rộng nếu còn các dấu hiệu sau:

- AI thường xuyên cho đáp án cuối mà không hỏi dẫn dắt.
- Không có benchmark theo grade level.
- Không biết dữ liệu học sinh nào được gửi sang model/vendor.
- Không có audit log cho prompt/output.
- Không có cách report câu trả lời sai hoặc không phù hợp.
- Không có dashboard để giáo viên/phụ huynh xem tiến độ và lỗi.
- Không đo learning retention sau khi học sinh không dùng AI.
- Không có kill switch hoặc rollback plan khi vendor/model gặp sự cố.

## 10. Kết luận

Bài học lớn nhất từ 3 case là AI tutor không nên được đánh giá bằng cảm giác “trả lời thông minh” hay “học sinh làm được nhiều bài hơn trong lúc dùng AI”. Một AI tutor an toàn phải chứng minh được rằng nó giúp học sinh học bền vững, bảo vệ dữ liệu học sinh, có human review thật, và có evaluation đủ mạnh trước khi triển khai ở quy mô lớn.