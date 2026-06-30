# Industry Risk Snapshot — Giáo dục / AI tutor

## 1. Bảng chấm Risk Profile

| Câu hỏi | Low / Medium / High / Critical | Vì sao? |
|---|---|---|
| Nếu AI sai, có thể gây hại thể chất không? | **Low → Medium** | Sai trong giáo dục thường không gây thương tích trực tiếp. Tuy nhiên, nếu AI đưa lời khuyên liên quan đến sức khỏe tinh thần, an toàn học đường, hoặc khủng hoảng cá nhân thì rủi ro có thể tăng lên Medium. |
| AI có ảnh hưởng đến quyết định hệ trọng không? | **High** | AI tutor có thể ảnh hưởng đến lộ trình học, đánh giá năng lực, lựa chọn nội dung luyện tập, cách phụ huynh/giáo viên nhìn nhận năng lực học sinh, và cơ hội được hỗ trợ đúng lúc. |
| Hệ thống có động tới dữ liệu nhạy cảm không? | **High** | Dữ liệu học sinh thường gồm tuổi, lớp, điểm số, attendance, hành vi học tập, nhu cầu hỗ trợ, đôi khi có dữ liệu gia đình hoặc social-emotional. Đây là dữ liệu nhạy cảm vì liên quan đến trẻ vị thành niên. |
| Nếu sai, hậu quả có khó đảo ngược không? | **Medium → High** | Một câu trả lời sai có thể sửa được, nhưng learning gap, over-reliance, mất động lực học hoặc placement sai có thể tích lũy qua nhiều tuần/tháng và khó đảo ngược. |
| Nếu triển khai rộng, blast radius có lớn không? | **High** | Sản phẩm AI tutor thường được triển khai theo trường, district, hoặc nền tảng online. Một lỗi trong model, prompt, dữ liệu hoặc UX có thể ảnh hưởng hàng nghìn đến hàng trăm nghìn học sinh. |
| Có cần human review hoặc escalation không? | **High** | Cần giáo viên/phụ huynh/counselor tham gia khi AI không chắc, khi có dấu hiệu khủng hoảng, khi gợi ý ảnh hưởng đến lộ trình học, hoặc khi có lỗi dữ liệu cá nhân. |
| Risk profile tổng thể của ngành | **High** | Không cao về physical injury như y tế/mobility, nhưng cao về học tập dài hạn, quyền riêng tư của trẻ em, công bằng giáo dục, scale, và trust. |

## 2. Pattern rủi ro của ngành Giáo dục / AI tutor

Trong 3 case đã phân tích, rủi ro lặp lại không chỉ nằm ở “AI trả lời sai một câu”. Rủi ro lớn hơn là **AI tạo cảm giác cá nhân hóa và hữu ích**, khiến học sinh, phụ huynh hoặc tutor tin tưởng quá mức trong khi hệ thống vẫn có thể thiếu grounding, thiếu hiểu biết bối cảnh học sinh, hoặc không bảo vệ dữ liệu đủ tốt. Với AI tutor, harm thường tích lũy chậm: học sinh được giải hộ thay vì học thật, giáo viên/tutor nhận gợi ý không đúng trình độ, phụ huynh nhận thông tin sai, hoặc dữ liệu học sinh bị chia sẻ rộng hơn mức cần thiết. Vì vậy, ngành này cần thiết kế theo hướng **tutor-not-solver**, có benchmark theo môn học/độ tuổi, privacy minimization, human-in-the-loop, escalation rõ ràng và pilot nhỏ trước khi rollout diện rộng.

## 3. Nếu là team sản phẩm, sửa gì trước?

1. **Không để AI “giải hộ” quá dễ:** AI phải ưu tiên gợi ý, hỏi dẫn dắt, kiểm tra hiểu bài, không đưa đáp án ngay.
2. **Grounding theo nội dung học:** Câu trả lời phải dựa trên SGK/curriculum/lesson objective, có kiểm soát level và vocabulary.
3. **Privacy by design:** Chỉ gửi dữ liệu tối thiểu cần thiết, de-identify dữ liệu học sinh, log rõ dữ liệu nào đi qua model/vendor nào.
4. **Human escalation:** Khi AI không chắc, khi có dấu hiệu khủng hoảng, hoặc khi ảnh hưởng đến quyết định học tập quan trọng, phải chuyển cho giáo viên/phụ huynh/counselor.
5. **Evaluation trước rollout:** Có test set theo từng môn, từng grade, từng dạng lỗi; đo hallucination, hint quality, answer leakage, age appropriateness, privacy leakage.
6. **Rollout có kiểm soát:** Pilot nhỏ, đo lỗi thật, có kill switch và rollback plan trước khi mở rộng toàn trường/district.
