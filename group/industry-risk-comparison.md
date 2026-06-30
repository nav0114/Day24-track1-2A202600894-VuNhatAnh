# Group Industry Risk Comparison

## 1. Mục đích

File này là phần tổng hợp của nhóm để so sánh **risk profile giữa các ngành** trong bài Day 24 — Case Study Hunt và Harm Map.

Bảng này được dùng để trả lời câu hỏi:

- Ngành nào có harm nghiêm trọng nhất?
- Ngành nào có scale lớn nhất?
- Ngành nào dễ xảy ra lỗi thường xuyên nhất?
- Ngành nào cần human-in-the-loop rõ nhất?
- Ngành nào cần tiêu chuẩn “được ship” cao nhất?

## 2. Lưu ý về phạm vi

Bảng dưới đây là bản tổng hợp theo risk lens của từng ngành trong đề bài. Với ngành **Giáo dục / AI tutor**, phân tích dựa trên 3 case chính trong repo này:

1. Khanmigo Math Errors
2. Texas A&M ChatGPT Grading Scandal
3. Turnitin AI Detection False Positives

Với các ngành còn lại, bảng dùng risk profile chung theo đặc điểm ngành. Khi các thành viên khác trong bàn share case cụ thể, nhóm có thể cập nhật thêm bằng chứng và số liệu cho từng ngành.

## 3. Bảng so sánh risk profile giữa các ngành

| Ngành | Harm dễ gặp nhất | Failure mode hay lặp lại | Layer hay bắt đầu lỗi | Risk profile tổng thể | Vì sao? |
|---|---|---|---|---|---|
| HR / tuyển dụng | Opportunity loss, dignity loss, unfair screening, legal exposure | Bias / fairness, proxy discrimination, poor explainability, automation bias | Data, Model, Evaluation, Governance | High | AI trong tuyển dụng ảnh hưởng trực tiếp đến cơ hội việc làm. Nếu model học từ dữ liệu lịch sử có bias, ứng viên có thể bị loại không công bằng. Harm thường không gây hại thể chất nhưng ảnh hưởng mạnh đến cơ hội kinh tế, danh dự và rủi ro pháp lý. |
| Giáo dục / AI tutor | Learning loss, misinformation, opportunity loss, dignity loss, over-reliance | Hallucination, over-reliance, automation bias, bias/fairness | UX, Grounding, Model, Evaluation, Governance | High | AI trong giáo dục ảnh hưởng tới việc học (lỗi kiến thức) và đánh giá (dương tính giả từ AI detector). Lỗi hệ thống có thể gây ra hàm oan học thuật hoặc hổng kiến thức nghiêm trọng. Human review và tính minh bạch là vô cùng quan trọng. |
| Y tế / symptom checker / health assistant | Injury, harmful advice, delayed intervention, privacy loss | Harmful advice, hallucination, escalation failure, overconfidence | Safety, Model, Grounding, UX, Governance | Critical | Nếu AI y tế tư vấn sai, người dùng có thể trì hoãn đi khám, dùng sai thuốc hoặc bỏ qua dấu hiệu nguy hiểm. Dữ liệu sức khỏe rất nhạy cảm. Đây là ngành có Severity rất cao và cần escalation sang chuyên gia y tế rõ ràng. |
| Mobility / autonomous driving | Physical injury, accident, property damage, loss of life | Perception failure, edge-case failure, sensor/model mismatch, fail-safe failure | Sensor, Model, System, Safety, Operations | Critical | Lỗi AI trong autonomous driving có thể gây tai nạn thật ngoài đời. Harm có thể xảy ra trong thời gian rất ngắn và khó đảo ngược. Ngành này cần tiêu chuẩn safety, simulation, real-world testing và fail-safe rất cao trước khi ship. |
| Media / news / social / political assistant | Misinformation, manipulation, public trust loss, polarization | Hallucination, misinformation amplification, persuasion misuse, weak source grounding | Grounding, Model, UX, Policy, Distribution | High | AI trong media và political assistant có thể ảnh hưởng đến nhận thức cộng đồng ở quy mô lớn. Severity với từng cá nhân có thể không luôn cao, nhưng Scale rất lớn vì nội dung sai có thể lan nhanh và ảnh hưởng đến niềm tin xã hội. |
| Content creator | Copyright risk, misinformation, reputation damage, bias, synthetic media misuse | Misuse / jailbreak, hallucination, copyright leakage, style imitation, deepfake misuse | Model, Data, Policy, UX, Distribution | Medium-High | AI content creator thường không gây hại thể chất trực tiếp, nhưng có rủi ro bản quyền, uy tín, misinformation và lạm dụng synthetic media. Risk tăng mạnh khi nội dung được xuất bản rộng hoặc dùng để giả mạo người thật/thương hiệu. |

## 4. So sánh theo 4 trục Severity / Scale / Probability / Frequency

| Trục so sánh | Ngành nổi bật nhất | Lý do |
|---|---|---|
| Severity cao nhất | Y tế và Mobility | Lỗi AI có thể gây injury, delayed intervention, accident hoặc hậu quả khó đảo ngược. |
| Scale lớn nhất | Media / news / social / political assistant | Một nội dung sai hoặc bị thao túng có thể lan đến rất nhiều người trong thời gian ngắn. |
| Probability cao nhất | Content creator và Media | Người dùng tạo nội dung liên tục, prompt đa dạng, khả năng hallucination/misuse xuất hiện thường xuyên. |
| Frequency cao nhất | Giáo dục / AI tutor, Content creator, Media | Các ngành này có nhiều lượt tương tác lặp lại mỗi ngày. Một lỗi nhỏ có thể lặp lại qua nhiều phiên chat hoặc nhiều nội dung. |
| Dữ liệu nhạy cảm rõ nhất | Y tế, Giáo dục, HR | Y tế có dữ liệu sức khỏe; giáo dục có dữ liệu học sinh/trẻ em; HR có dữ liệu ứng viên và cơ hội việc làm. |
| Cần human-in-the-loop rõ nhất | Y tế, HR, Giáo dục | Các ngành này ảnh hưởng đến quyết định hệ trọng: sức khỏe, cơ hội việc làm, chất lượng học tập và hỗ trợ học sinh. |
| Cần bar “được ship” cao nhất | Y tế và Mobility | Lỗi có thể gây hại thể chất hoặc hậu quả khó đảo ngược, nên yêu cầu testing, monitoring, escalation và fail-safe cao hơn các ngành khác. |

## 5. Câu hỏi thảo luận

### 5.1. Ngành nào có Severity tiềm năng cao nhất?

**Y tế / symptom checker / health assistant** và **Mobility / autonomous driving** có Severity cao nhất.

Lý do là lỗi AI trong hai ngành này có thể gây hậu quả trực tiếp đến sức khỏe, an toàn thể chất hoặc tính mạng. Với y tế, AI có thể đưa lời khuyên sai hoặc làm người dùng chậm đi khám. Với autonomous driving, lỗi perception, planning hoặc fail-safe có thể dẫn đến tai nạn thật.

### 5.2. Ngành nào có Scale tiềm năng lớn nhất?

**Media / news / social / political assistant** có Scale lớn nhất.

Một câu trả lời sai, một nội dung chính trị bị thao túng, hoặc một thông tin giả có thể được phát tán đến rất nhiều người. Scale của ngành media không chỉ nằm ở số người dùng trực tiếp, mà còn ở khả năng nội dung được chia sẻ lại qua mạng xã hội.

### 5.3. Ngành nào có Probability hoặc Frequency cao nhất?

**Content creator**, **Media**, và **Giáo dục / AI tutor** có Probability/Frequency cao.

Lý do là các ngành này có số lượt tương tác lặp lại lớn. Người dùng tạo nhiều prompt, nhiều nội dung, nhiều phiên học hoặc nhiều lượt hỏi đáp. Vì vậy, ngay cả lỗi nhỏ như hallucination, bias, answer leakage hoặc misinformation cũng có thể xuất hiện nhiều lần.

### 5.4. Ngành nào xử lý dữ liệu nhạy cảm rõ nhất?

Ba ngành xử lý dữ liệu nhạy cảm rõ nhất là:

1. **Y tế** — dữ liệu triệu chứng, bệnh lý, thuốc, tình trạng sức khỏe.
2. **Giáo dục** — dữ liệu học sinh, trẻ em, điểm số, quá trình học, hành vi học tập.
3. **HR / tuyển dụng** — CV, lịch sử làm việc, thông tin cá nhân, đánh giá ứng viên.

Trong ba ngành này, privacy không phải là tính năng phụ. Privacy phải được thiết kế như một yêu cầu cốt lõi của sản phẩm.

### 5.5. Ngành nào cần human-in-the-loop rõ nhất?

**Y tế**, **HR**, và **Giáo dục** cần human-in-the-loop rõ nhất.

- Y tế cần bác sĩ/chuyên gia y tế khi có dấu hiệu nguy hiểm.
- HR cần recruiter hoặc hiring manager review trước khi loại ứng viên.
- Giáo dục cần giáo viên/tutor/phụ huynh khi AI không chắc, học sinh bị kẹt lâu, hoặc có dấu hiệu phụ thuộc AI.

Human-in-the-loop chỉ có ý nghĩa nếu con người thật sự có quyền xem, sửa, reject và escalation. Nếu chỉ đặt con người ở cuối quy trình nhưng không có thông tin hoặc thời gian review, cơ chế này sẽ yếu.

### 5.6. Ngành nào cần bar “được ship” cao nhất?

**Y tế** và **Mobility** cần bar “được ship” cao nhất.

Hai ngành này cần yêu cầu nghiêm ngặt hơn về:

- Pre-release testing
- Safety benchmark
- Red-team testing
- Escalation
- Fail-safe
- Incident response
- Monitoring sau khi ship
- Rollback hoặc kill switch

Với các ngành như giáo dục, HR và media, bar ship cũng cao nhưng trọng tâm khác hơn: fairness, privacy, grounding, human review và long-term harm.

## 6. Risk profile tổng hợp giữa các ngành

Nhìn chung, risk profile giữa các ngành khác nhau ở 3 điểm chính:

### 6.1. Ngành có physical harm cần tiêu chuẩn safety cao nhất

Y tế và Mobility là hai ngành có rủi ro physical harm rõ nhất. Lỗi AI trong các ngành này có thể dẫn đến chấn thương, tai nạn hoặc trì hoãn can thiệp. Vì vậy, các hệ thống AI trong hai ngành này không nên được ship chỉ vì demo hoạt động tốt. Chúng cần kiểm thử safety, edge case, fail-safe và escalation rất kỹ.

### 6.2. Ngành có social-scale harm cần kiểm soát distribution

Media và political assistant có thể tạo harm ở quy mô xã hội. Một lỗi hallucination hoặc misinformation không chỉ ảnh hưởng một người, mà có thể làm suy giảm public trust hoặc gây thao túng nhận thức. Với nhóm này, vấn đề không chỉ là model trả lời đúng hay sai, mà còn là nội dung được phân phối, khuếch đại và tái sử dụng như thế nào.

### 6.3. Ngành có opportunity/data harm cần fairness và privacy

HR và Giáo dục không thường gây physical harm trực tiếp, nhưng ảnh hưởng đến cơ hội học tập, cơ hội việc làm, dignity và dữ liệu cá nhân. Đây là harm ít “gây sốc” hơn tai nạn hay y tế, nhưng có thể tích lũy lâu dài và khó phát hiện. Các ngành này cần fairness audit, privacy minimization, explainability và human review.

## 7. Kết luận của nhóm

Nếu xếp mức độ rủi ro tổng thể:

| Nhóm risk | Ngành |
|---|---|
| Critical | Y tế, Mobility |
| High | HR, Giáo dục / AI tutor, Media / political assistant |
| Medium-High | Content creator |

Không có ngành nào là “risk thấp” hoàn toàn. Điểm khác nhau là loại harm chính:

- **Y tế/Mobility:** harm nặng, khó đảo ngược.
- **Media:** scale lớn, ảnh hưởng niềm tin xã hội.
- **HR/Giáo dục:** harm về cơ hội, dữ liệu, fairness và phát triển con người.
- **Content creator:** harm về bản quyền, uy tín, synthetic media và misinformation.

Với ngành **Giáo dục / AI tutor**, bài học quan trọng nhất là con người không nên quá phụ thuộc (over-reliance) vào phán quyết của AI, đặc biệt là trong chấm điểm hoặc phát hiện gian lận. Sản phẩm cần minh bạch về giới hạn sai số (hallucination), tránh thiên vị (bias), và luôn yêu cầu sự kiểm chứng của con người (human-in-the-loop) để bảo vệ danh dự và cơ hội học tập của học sinh.