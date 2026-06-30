# Case Selection Log — Giáo dục / AI tutor

## 1. Mục tiêu tìm case

Mục tiêu là tìm các case AI có thật trong ngành **Giáo dục / AI tutor**, sau đó lọc xuống 3 case mạnh nhất để làm Brief Case và Harm Map Worksheet cho Vũ Nhật Anh.

Case tốt cần có:

- AI được dùng trong bối cảnh giáo dục.
- Có stakeholder rõ: học sinh, giáo viên, nhà trường.
- Có ít nhất 1 số liệu cụ thể.
- Có nguồn đáng tin (Báo chí chính thống, thông cáo báo chí).
- Có đủ dữ kiện để phân tích failure mode, layer, harm.
- Tuyệt đối không dùng ChatGPT, Claude, Perplexity làm nguồn.

## 2. Shortlist case sơ bộ

| # | Case sơ bộ | AI được dùng để làm gì? | Số liệu / evidence có thể dùng | Risk lens chính | Nguồn mạnh/yếu | Quyết định |
|---|---|---|---|---|---|---|
| 1 | Khanmigo Math Errors | AI tutor hướng dẫn học sinh bằng phương pháp Socratic | Sự cố lan rộng buộc kỹ sư phải thiết kế lại hệ thống thêm "math agent" | Misinformation, Opportunity loss | Education Week, Khan Academy Blog (Mạnh) | **Chọn** |
| 2 | Texas A&M ChatGPT Grading Scandal | Giáo sư dùng ChatGPT làm công cụ phát hiện đạo văn để chấm điểm | Hơn một nửa lớp bị đánh trượt tạm thời, một số bị hoãn tốt nghiệp | Over-reliance, Dignity loss, Opportunity loss | Business Insider, Thông cáo trường (Mạnh) | **Chọn** |
| 3 | Turnitin AI Detection False Positives | AI của Turnitin quét bài để báo cáo tỷ lệ dùng AI viết luận | Nghiên cứu của Stanford: AI detector false positive >60% cho người ESL; Turnitin báo 4% cấp câu | Bias/fairness, Dignity loss | Washington Post, Turnitin (Mạnh) | **Chọn** |
| 4 | LAUSD Ed AI chatbot / AllHere | AI chatbot/nền tảng học tập cá nhân hóa | Hợp đồng 6 triệu USD; allegation về dữ liệu học sinh | Privacy loss, vendor governance | Nguồn chính thức LAUSD + The 74 | Lọc đi (Tránh trùng với bạn cùng nhóm) |
| 5 | GPT-4 math tutor without guardrails | GPT-4 hỗ trợ học sinh trung học làm bài | Nhóm dùng GPT Base giảm 17% performance khi không còn dùng AI | Over-reliance, learning loss | Paper PNAS | Lọc đi (Tránh trùng với bạn cùng nhóm) |

## 3. Vì sao chọn 3 case này?

| Case | Lý do chọn |
|---|---|
| Khanmigo Math Errors | Đại diện cho lỗi cốt lõi của LLM (Hallucination) khi làm gia sư, dẫn đến việc phải phát triển hệ thống hybrid (math agent). |
| Texas A&M ChatGPT Grading Scandal | Đại diện cho rủi ro **Over-reliance** và **Automation Bias** từ phía người dùng (giáo sư), dẫn đến hậu quả thực tế nghiêm trọng về điểm số và bằng cấp. |
| Turnitin AI Detection False Positives | Đại diện cho rủi ro **Bias / Fairness** của các công cụ AI trong giáo dục, gây hàm oan cho nhóm sinh viên quốc tế. |

## 4. Xác nhận Checklist

- [x] Không ghi nguồn là ChatGPT, Claude, hay Perplexity.
- [x] Mỗi case đều trích dẫn từ báo chí (The Washington Post, Business Insider, Education Week) hoặc trang thông báo chính thức.
- [x] Mỗi case đều có số liệu hoặc quy mô ảnh hưởng cụ thể.