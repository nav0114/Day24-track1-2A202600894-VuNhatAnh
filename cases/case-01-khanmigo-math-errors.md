# Brief Case: Khanmigo Math Errors

## 1. Brief Case

| Field | Bạn điền gì |
|---|---|
| Tên case | Khanmigo Math Errors |
| Ngành | Giáo dục / AI tutor |
| Tổ chức / sản phẩm | Khan Academy / Khanmigo |
| Use case AI | AI tutor được thiết kế theo phương pháp Socratic để hỗ trợ học sinh học Toán và các môn khác bằng cách đặt câu hỏi gợi mở thay vì đưa ra đáp án trực tiếp. |
| Thời điểm | Năm 2023 - 2024 |
| Case xảy ra chuyện gì? | Khanmigo thường xuyên gặp lỗi hallucination trong môn Toán, tự tin đưa ra các phép tính sai (như nhân chia, lũy thừa) hoặc các bước giải không hợp lý, khiến học sinh bị hướng dẫn sai. Để khắc phục, Khan Academy đã phải bổ sung một "math agent" (máy tính chạy ngầm) để kiểm tra chéo các phép toán của LLM trước khi phản hồi học sinh. |
| Stakeholder bị ảnh hưởng | Học sinh, giáo viên. |
| Số liệu chính | Mặc dù không công bố số liệu lỗi cụ thể, việc phát hiện lỗi phổ biến đến mức đội ngũ kỹ sư phải tái thiết kế kiến trúc (thêm math agent) để giảm thiểu rủi ro tính toán sai. |
| Trích nguồn ngắn | Khan Academy thừa nhận tính năng AI tutor của họ có thể mắc lỗi toán học cơ bản và cảnh báo người dùng cần kiểm tra lại, đồng thời liên tục nâng cấp hệ thống để cải thiện độ chính xác (Khan Academy, 2023). |
| Nguồn 1 | [WSJ Podcasts, 2023](https://www.wsj.com/podcasts/tech-news-briefing/what-happens-when-an-ai-tutor-struggles-with-basic-math/e99b146e-eff0-4eae-a88e-1d41b11a0eb2) |
| Nguồn 2 | [Khan Academy Blog, 2023](https://blog.khanacademy.org/how-khan-academy-is-building-a-better-ai-tutor-our-most-recent-learnings/) |
| Ghi chú độ tin cậy | Primary và Secondary, không có conflict. |

## 2. Harm Map Worksheet

| High-risk moment | Stakeholder bị ảnh hưởng | Failure mode | Layer bắt đầu lỗi | Harm xảy ra là gì? | Harm lens | Severity | Scale | Probability | Frequency | Vì sao? |
|---|---|---|---|---|---|---|---|---|---|---|
| AI tutor đưa ra các bước giải toán sai hoặc tính toán sai trong quá trình hướng dẫn | Học sinh | Hallucination | Model | Học sinh học sai phương pháp, hiểu lầm kiến thức cơ bản, mất thời gian và có thể mất tự tin vào khả năng học của mình. | Misinformation, Opportunity loss | Medium | High | Medium | Medium | Lỗi sai có thể sửa được (Medium Severity) nhưng nếu hệ thống được triển khai cho hàng triệu học sinh trên nền tảng thì ảnh hưởng là rất rộng (High Scale). Lỗi toán học của LLM xảy ra thường xuyên nếu không có math agent can thiệp. |
