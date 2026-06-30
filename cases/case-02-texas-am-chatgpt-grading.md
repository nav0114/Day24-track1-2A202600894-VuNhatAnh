# Brief Case: Texas A&M-Commerce ChatGPT Grading Scandal

## 1. Brief Case

| Field | Bạn điền gì |
|---|---|
| Tên case | Texas A&M ChatGPT Grading Scandal |
| Ngành | Giáo dục / AI tutor (AI grading/detection) |
| Tổ chức / sản phẩm | Texas A&M University–Commerce / ChatGPT |
| Use case AI | Giáo sư đại học sử dụng ChatGPT như một công cụ phát hiện văn bản do AI tạo ra để chấm điểm bài luận cuối kỳ của sinh viên. |
| Thời điểm | Tháng 5 năm 2023 |
| Case xảy ra chuyện gì? | Giáo sư Jared Mumm sao chép bài luận của sinh viên vào ChatGPT và hỏi xem ChatGPT có viết bài này không. Do bản chất của LLM thường "hallucinate" trả lời "có", giáo sư đã tin tưởng hoàn toàn và đánh trượt phần lớn sinh viên trong lớp, đồng thời tạm hoãn việc tốt nghiệp của họ. Thực tế ChatGPT không có khả năng phát hiện đạo văn. |
| Stakeholder bị ảnh hưởng | Sinh viên trong lớp, nhà trường. |
| Số liệu chính | Hơn một nửa số sinh viên trong lớp bị đánh trượt (điểm X) tạm thời; một số bị giữ lại bằng tốt nghiệp cho đến khi vụ việc được làm rõ. |
| Trích nguồn ngắn | Một giáo sư tại Texas A&M-Commerce đã vô tình đánh trượt sinh viên của mình do quá tin tưởng vào tính năng phát hiện đạo văn không có thật của ChatGPT, dẫn đến việc nhà trường phải can thiệp (Business Insider, 2023). |
| Nguồn 1 | [Business Insider, 2023](https://www.businessinsider.com/professor-fails-students-after-chatgpt-falsely-said-it-wrote-papers-2023-5) |
| Nguồn 2 | [Thông cáo chính thức của Texas A&M-Commerce, 2023](https://new.tamuc.edu/) |
| Ghi chú độ tin cậy | Secondary (Báo cáo tin tức) và Primary (Thông cáo trường), độ tin cậy cao. |

## 2. Harm Map Worksheet

| High-risk moment | Stakeholder bị ảnh hưởng | Failure mode | Layer bắt đầu lỗi | Harm xảy ra là gì? | Harm lens | Severity | Scale | Probability | Frequency | Vì sao? |
|---|---|---|---|---|---|---|---|---|---|---|
| Giáo sư dùng ChatGPT để kiểm tra xem bài viết có phải do AI viết không và tin tưởng vào câu trả lời sai | Sinh viên | Over-reliance, Hallucination | UX, Grounding | Sinh viên bị hàm oan, bị đánh trượt, hoãn tốt nghiệp, tổn thương tinh thần và uy tín cá nhân. | Dignity loss, Opportunity loss | High | Low | High | Low | Hậu quả rất nghiêm trọng với cá nhân sinh viên (High Severity vì ảnh hưởng bằng cấp), nhưng Scale giới hạn ở một lớp học (Low). Xác suất xảy ra (Probability) cao nếu người dùng thiếu hiểu biết về công nghệ AI. |
