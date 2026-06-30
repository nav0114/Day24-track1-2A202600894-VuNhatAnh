# Case Selection Log — Giáo dục / AI tutor

## 1. Mục tiêu tìm case

Mục tiêu là tìm 5-8 case AI có thật trong ngành **Giáo dục / AI tutor**, sau đó lọc xuống 2-3 case mạnh nhất để làm Brief Case và Harm Map Worksheet.

Case tốt cần có:

- AI được dùng trong bối cảnh giáo dục.
- Có stakeholder rõ: học sinh, phụ huynh, giáo viên, tutor, trường, district.
- Có ít nhất 1 số liệu cụ thể.
- Có nguồn đáng tin.
- Có đủ dữ kiện để phân tích failure mode, layer, harm, severity, scale, probability, frequency.

## 2. Shortlist case sơ bộ

| # | Case sơ bộ | AI được dùng để làm gì? | Số liệu / evidence có thể dùng | Risk lens chính | Nguồn mạnh/yếu | Quyết định |
|---|---|---|---|---|---|---|
| 1 | LAUSD Ed AI chatbot / AllHere | AI chatbot/nền tảng học tập cá nhân hóa cho học sinh và phụ huynh | LAUSD hơn 520,000 học sinh; hợp đồng chatbot được báo chí đưa tin trị giá 6 triệu USD; có allegation về dữ liệu học sinh | Privacy loss, vendor governance, escalation failure | Nguồn chính thức LAUSD + The 74 điều tra | **Chọn** |
| 2 | GPT-4 math tutor without guardrails | GPT-4 hỗ trợ học sinh trung học làm bài toán practice | Gần 1,000 học sinh; GPT Base tăng điểm practice nhưng nhóm này giảm 17% khi không còn dùng AI; GPT Tutor có guardrails giảm harm | Over-reliance, answer leakage, measurement failure | Paper PNAS + SSRN | **Chọn** |
| 3 | Tutor CoPilot | AI gợi ý chiến lược sư phạm cho tutor trong phiên tutoring live | 900 tutor, 1,800 học sinh K-12, hơn 550,000 messages; tăng 4 percentage points mastery, lower-rated tutors tăng 9 percentage points | Human-AI tutoring, grade-level mismatch, privacy minimization | arXiv paper + preregistration | **Chọn** |
| 4 | Khanmigo / Khan Academy | AI tutor và teaching assistant cho học sinh/giáo viên | Khan Academy từng công bố hơn 40 district và 28,000 học sinh/giáo viên trong pilot classroom | Tutor-not-solver, child safety, answer leakage, privacy | Nguồn official/product blog mạnh về rollout nhưng ít incident độc lập | Không chọn vì giống product rollout hơn là harm case rõ |
| 5 | Georgia State “Pounce” chatbot | AI chatbot nhắc việc, trả lời câu hỏi hành chính để giảm summer melt | Georgia State đưa tin summer melt giảm từ 19% xuống 9%; nguồn khác ghi giảm khoảng 22% | Positive case, task navigation, student support equity | Nguồn university/news + academic report | Không chọn vì là higher-ed admin chatbot, không phải AI tutor trực tiếp |
| 6 | OpenAI AI Text Classifier / AI writing detectors | Phát hiện bài viết do AI tạo trong giáo dục | OpenAI từng ghi classifier false positive khoảng 9% trên human-written text và sau đó dừng vì low accuracy | False accusation, dignity loss, academic integrity risk | OpenAI primary source + Turnitin documentation | Không chọn vì là AI detector, không phải tutor |
| 7 | NYC public schools ChatGPT ban/reversal | Chính sách hạn chế rồi mở lại việc dùng ChatGPT trong trường học | NYC là district lớn; ban vì lo ngại learning impact, safety, accuracy; sau đó đảo chiều sang hướng hướng dẫn sử dụng | Policy risk, unequal access, cheating/misinformation | Chalkbeat, Education Week, official statements được báo trích | Không chọn vì là policy case, thiếu worksheet product-level |
| 8 | Michigan Virtual Khanmigo pilot | Pilot Khanmigo trong lớp học, tập trung hỗ trợ Algebra/math | Có số giáo viên, học sinh, district trong pilot; có phản hồi classroom implementation | Implementation risk, teacher adoption, learning quality | Blog/report triển khai thực tế | Không chọn vì nguồn thiên về pilot reflection, chưa đủ harm evidence mạnh |

## 3. Vì sao chọn 3 case cuối?

3 case cuối được chọn vì tạo thành bộ phân tích cân bằng:

| Case | Lý do chọn |
|---|---|
| LAUSD Ed AI chatbot / AllHere | Đại diện cho rủi ro **privacy, vendor governance, rollout ở scale lớn**. Đây là case giúp thấy AI tutor không chỉ có rủi ro model mà còn có rủi ro dữ liệu và vận hành. |
| GPT-4 math tutor without guardrails | Đại diện cho rủi ro **over-reliance và learning loss**. Đây là case học thuật mạnh vì có field experiment và số liệu rõ về tác động khi AI bị lấy đi. |
| Tutor CoPilot | Đại diện cho hướng thiết kế **human-in-the-loop**. Đây là case tích cực hơn, giúp so sánh giữa AI thay thế người dạy và AI hỗ trợ người dạy. |

## 4. Vì sao không chọn các case còn lại?

Các case còn lại vẫn hữu ích để hiểu bối cảnh ngành, nhưng chưa mạnh bằng 3 case chính:

- **Khanmigo** là case lớn và rất liên quan, nhưng nguồn chủ yếu là official/product-facing. Phù hợp làm background hơn là harm map chính.
- **Georgia State Pounce** có số liệu tốt, nhưng là chatbot hỗ trợ hành chính/higher education, không phải AI tutor trực tiếp.
- **AI writing detector** có harm rõ về false accusation, nhưng thuộc nhóm assessment/academic integrity hơn là AI tutor.
- **NYC ChatGPT ban/reversal** cho thấy policy risk, nhưng không có một sản phẩm AI tutor cụ thể để phân tích layer/failure mode sâu.
- **Michigan Virtual Khanmigo pilot** có thông tin thực tế, nhưng thiên về pilot implementation và chưa có incident/risk evidence đủ mạnh.

## 5. Kết luận từ bước chọn case

Sau khi lọc, 3 case chính bao phủ 3 nhóm rủi ro quan trọng của ngành Giáo dục / AI tutor:

1. **Data & governance risk** — AI dùng dữ liệu học sinh, phụ thuộc vendor, rollout scale lớn.
2. **Learning design risk** — AI làm học sinh hoàn thành bài nhưng không học bền vững.
3. **Human-AI workflow risk** — AI hỗ trợ người dạy nhưng vẫn cần review, monitoring và escalation.

Bộ 3 này đủ mạnh để trả lời yêu cầu của đề vì mỗi case đều có số liệu, có nguồn, có stakeholder rõ và có thể điền Harm Map Worksheet đầy đủ.