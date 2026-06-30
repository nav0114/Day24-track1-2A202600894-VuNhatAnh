# Brief Case: Turnitin AI Detection False Positives

## 1. Brief Case

| Field | Bạn điền gì |
|---|---|
| Tên case | Turnitin AI Detection False Positives |
| Ngành | Giáo dục / AI tutor (AI detection tool) |
| Tổ chức / sản phẩm | Turnitin |
| Use case AI | Sử dụng AI để phân tích và tính toán xác suất một bài nộp của sinh viên có chứa văn bản do AI (như ChatGPT) tạo ra hay không. |
| Thời điểm | Tháng 4 năm 2023 - nay |
| Case xảy ra chuyện gì? | Công cụ phát hiện AI của Turnitin thỉnh thoảng báo cáo "dương tính giả", đặc biệt đối với các sinh viên sử dụng tiếng Anh như ngôn ngữ thứ hai (ESL) hoặc những người viết theo cấu trúc khuôn mẫu. Việc này dẫn đến các cáo buộc gian lận học thuật sai lệch. |
| Stakeholder bị ảnh hưởng | Sinh viên (đặc biệt sinh viên quốc tế), giáo viên, hội đồng kỷ luật nhà trường. |
| Số liệu chính | Theo Turnitin, tỷ lệ dương tính giả ở cấp độ câu là khoảng 4%. Tuy nhiên, các nghiên cứu độc lập chỉ ra rằng các công cụ phát hiện AI nói chung có thể có tỷ lệ báo cáo sai lên tới hơn 60% đối với sinh viên ESL (nghiên cứu của Stanford). |
| Trích nguồn ngắn | Turnitin đã phải thừa nhận công cụ của họ có tỷ lệ dương tính giả và khuyến cáo giáo viên không nên dùng nó làm cơ sở duy nhất để kỷ luật sinh viên (Washington Post, 2023). |
| Nguồn 1 | [Washington Post, 2023](https://www.washingtonpost.com/technology/2023/04/01/chatgpt-cheating-detection-turnitin/) |
| Nguồn 2 | [Turnitin Blog, 2023](https://www.turnitin.com/blog/understanding-false-positives-within-our-ai-writing-detection-capabilities) |
| Ghi chú độ tin cậy | Primary (từ Turnitin) và Secondary (Báo Washington Post). |

## 2. Harm Map Worksheet

| High-risk moment | Stakeholder bị ảnh hưởng | Failure mode | Layer bắt đầu lỗi | Harm xảy ra là gì? | Harm lens | Severity | Scale | Probability | Frequency | Vì sao? |
|---|---|---|---|---|---|---|---|---|---|---|
| Hệ thống cắm cờ (flag) nhầm một bài luận do sinh viên tự viết là do AI tạo ra | Sinh viên | Bias / fairness, Over-reliance | Model | Sinh viên bị oan, đối mặt với kỷ luật học thuật, đình chỉ học, ảnh hưởng nặng nề đến tâm lý và danh dự. Nhóm sinh viên không bản xứ chịu rủi ro cao hơn. | Dignity loss, Opportunity loss | High | Medium | Medium | Medium | Kỷ luật học thuật có thể hủy hoại sự nghiệp của sinh viên (High Severity). Lỗi này ảnh hưởng hệ thống (Medium Scale) và có xu hướng thiên vị chống lại người không bản xứ (Bias). |
