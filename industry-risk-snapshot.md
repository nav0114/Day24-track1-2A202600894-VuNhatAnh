# Industry Risk Snapshot — Giáo dục / AI tutor

## 1. Bảng chấm Risk Profile

| Câu hỏi | Low / Medium / High / Critical | Vì sao? |
|---|---|---|
| Nếu AI sai, có thể gây hại thể chất không? | **Low** | Các lỗi trong giáo dục thường không liên quan đến thương tích vật lý hay đe dọa tính mạng. |
| AI có ảnh hưởng đến quyết định hệ trọng không? | **High** | Có. Việc sử dụng AI để chấm điểm, phát hiện đạo văn hay định hướng học tập ảnh hưởng trực tiếp đến điểm số, khả năng tốt nghiệp và danh dự học thuật của sinh viên. |
| Hệ thống có động tới dữ liệu nhạy cảm không? | **High** | Có, hệ thống thu thập dữ liệu học tập cá nhân, bài làm, thói quen học, đôi khi cả thông tin định danh của người học (bao gồm trẻ vị thành niên). |
| Nếu sai, hậu quả có khó đảo ngược không? | **High** | Một cáo buộc gian lận học thuật sai (dương tính giả từ AI detector) hoặc một lỗ hổng kiến thức do AI tutor dạy sai có thể làm mất thời gian, tiền bạc, và gây tổn thương tinh thần khó phục hồi. |
| Nếu triển khai rộng, blast radius có lớn không? | **High** | Sản phẩm giáo dục thường được áp dụng cho toàn trường hoặc toàn quận học khu, một lỗi thuật toán có thể ảnh hưởng oan hàng chục ngàn sinh viên. |
| Có cần human review hoặc escalation không? | **High** | Cực kỳ cần thiết. Bất kỳ quyết định kỷ luật nào dựa trên AI detection, hoặc khi AI tutor không giải quyết được vấn đề học tập, đều cần giáo viên con người xem xét độc lập. |
| Risk profile tổng thể của ngành | **High** | Rủi ro xoay quanh cơ hội học tập (Opportunity loss), danh dự (Dignity loss) và sự phụ thuộc mù quáng vào công nghệ của cả người học lẫn người dạy. |

## 2. Pattern rủi ro của ngành Giáo dục / AI tutor

Qua 3 case study (Khanmigo, Texas A&M, Turnitin), pattern rủi ro lớn nhất trong giáo dục không chỉ là **Hallucination** (AI trả lời sai) mà là **Over-reliance** (sự phụ thuộc thái quá) và **Automation Bias** từ phía người dùng (cả học sinh lẫn giáo viên). 
1. Khi AI đóng vai trò tutor, học sinh dễ bị hấp thu kiến thức sai lệch nếu AI tính toán sai (Khanmigo). 
2. Khi AI đóng vai trò công cụ quản lý/đánh giá, giáo viên có xu hướng tin tưởng tuyệt đối vào phán quyết của máy móc, dẫn đến các hình phạt oan sai tàn khốc cho sinh viên (Turnitin, Texas A&M).
Đặc biệt, hệ thống phát hiện AI (AI detection) hiện nay có **Bias** rõ rệt đối với sinh viên quốc tế, tạo ra sự bất công có hệ thống.

## 3. Nếu là team sản phẩm, sửa gì trước?

1. **Minh bạch về giới hạn của AI (UX layer):** Cảnh báo rõ ràng trên giao diện cho cả giáo viên và học sinh rằng AI có thể tính toán sai, và công cụ phát hiện AI không thể được dùng làm bằng chứng duy nhất để kỷ luật.
2. **Thiết kế "Human-in-the-loop" bắt buộc:** Mọi cảnh báo về đạo văn do AI (Turnitin) phải đi kèm yêu cầu giáo viên thực hiện quy trình phỏng vấn học sinh hoặc kiểm tra lịch sử nháp bài trước khi kết luận.
3. **Cải thiện Grounding và Guardrails (Model layer):** Đối với AI tutor (Khanmigo), tích hợp các công cụ kiểm tra logic bên ngoài (như math agent) để xác minh kết quả tính toán trước khi xuất ra cho người dùng.
4. **Kiểm tra công bằng (Fairness Evaluation):** Trước khi phát hành công cụ đánh giá, cần kiểm tra tỷ lệ dương tính giả trên các tập dữ liệu đa dạng (ví dụ: bài viết của người bản xứ vs. người không bản xứ) để tránh thiên vị.
