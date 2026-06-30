
# Methodology — Case Study Hunt và Harm Map

## 1. Scope

Ngành được chọn là **Giáo dục / AI tutor**. Phạm vi case bao gồm các hệ thống AI được dùng để hỗ trợ học sinh, giáo viên, tutor, phụ huynh hoặc nhà trường trong quá trình học tập. Bài này ưu tiên các case có liên quan trực tiếp đến AI tutor, learning chatbot, human-AI tutoring, hoặc công cụ AI ảnh hưởng đến quyết định học tập.

## 2. Cách tìm case

Quy trình tìm case gồm 4 bước:

1. Tìm rộng 5-8 case sơ bộ trong ngành Giáo dục / AI tutor.
2. Loại case thiếu số liệu, thiếu nguồn rõ ràng, hoặc chỉ là quảng cáo sản phẩm.
3. Ưu tiên case có nguồn primary hoặc nguồn học thuật.
4. Chọn 3 case mạnh nhất để viết Brief Case và Harm Map Worksheet.

Từ khóa tìm kiếm đã dùng:

- AI tutor case study education risk
- generative AI tutor learning harm guardrails
- AI chatbot student data privacy school district
- human AI tutoring randomized controlled trial
- AI education chatbot student outcomes
- AI writing detector false positive education
- Khanmigo pilot AI tutor classroom
- school district ChatGPT ban education risk

## 3. Tiêu chí chọn case cuối cùng

Một case được chọn nếu đáp ứng phần lớn các điều kiện sau:

| Tiêu chí | Cách kiểm |
|---|---|
| Có thật | Có tổ chức/sản phẩm/nghiên cứu cụ thể, không phải ví dụ giả định |
| Cùng ngành | Liên quan rõ đến giáo dục, AI tutor, học sinh, tutor, giáo viên hoặc nhà trường |
| Có số liệu | Có ít nhất 1 con số có ý nghĩa: số học sinh, số trường, tỉ lệ tác động, chi phí, số tin nhắn, giá trị hợp đồng... |
| Có nguồn đáng tin | Ưu tiên primary source, paper, official announcement, report, hoặc báo điều tra có fact rõ |
| Có harm map được | Có đủ dữ kiện để phân tích failure mode, layer, stakeholder, harm, severity, scale, probability, frequency |
| Có giá trị học từ case | Case giúp rút ra bài học sản phẩm, guardrails, evaluation, human review hoặc governance |

## 4. Cách đánh giá độ tin cậy nguồn

| Loại nguồn | Độ tin cậy | Cách dùng trong bài |
|---|---|---|
| Primary source | Cao | Dùng để lấy fact chính: paper, official announcement, report, court/regulator filing |
| Academic paper / RCT | Cao | Dùng để lấy số liệu về tác động, method, limitation |
| Official company / district source | Trung bình đến cao | Dùng để lấy thông tin sản phẩm, scope, mục tiêu, nhưng cần đối chiếu khi có claim quảng bá |
| Investigative journalism | Trung bình đến cao | Dùng để lấy allegation, timeline, stakeholder impact; không ghi allegation như kết luận pháp lý |
| Blog / explainer | Trung bình | Chỉ dùng để đối chiếu hoặc làm case sơ bộ |
| AI assistant output | Không dùng làm nguồn | Chỉ dùng để gợi ý hướng tìm, không đưa vào citation |

## 5. Cách chấm Harm Map

### Severity

Severity trả lời câu hỏi: **Nếu harm xảy ra, hậu quả nặng đến đâu?**

| Mức | Ý nghĩa trong ngành Giáo dục / AI tutor |
|---|---|
| Low | Bất tiện nhẹ, học sinh nhận gợi ý chưa tối ưu nhưng dễ sửa |
| Medium | Ảnh hưởng thật đến trải nghiệm học, hiểu sai bài, mất thời gian, cần giáo viên sửa lại |
| High | Mất cơ hội học tập, tạo learning gap, rủi ro dữ liệu học sinh, ảnh hưởng công bằng hoặc pháp lý |
| Critical | Có thể ảnh hưởng an toàn thể chất/tinh thần, khủng hoảng cá nhân, hoặc hậu quả rất khó đảo ngược |

### Scale

Scale trả lời câu hỏi: **Harm ảnh hưởng rộng đến bao nhiêu người hoặc nhóm?**

| Mức | Ý nghĩa |
|---|---|
| Low | Một học sinh hoặc một nhóm nhỏ |
| Medium | Một lớp, một nhóm tutor, một trường hoặc một pilot |
| High | Nhiều trường, một district, nhiều district, hoặc nền tảng có nhiều người dùng |

### Probability

Probability trả lời câu hỏi: **Harm này có dễ xảy ra không?**

| Mức | Ý nghĩa |
|---|---|
| Low | Chỉ xảy ra trong edge case hoặc khi có nhiều điều kiện xấu cùng lúc |
| Medium | Có khả năng xảy ra trong usage bình thường nếu thiếu guardrails |
| High | Dễ xảy ra thường xuyên vì gắn với cách người dùng tương tác với AI |

### Frequency

Frequency trả lời câu hỏi: **Nếu harm có thể xảy ra, nó lặp lại thường xuyên đến mức nào?**

| Mức | Ý nghĩa |
|---|---|
| Low | Ít lặp lại, thường là incident đơn lẻ |
| Medium | Lặp lại theo phiên học, theo lớp, hoặc theo nhóm người dùng |
| High | Lặp lại trong nhiều lượt chat, nhiều bài tập, nhiều học sinh hoặc nhiều ngày học |

## 6. Lưu ý khi phân tích

Trong bài này, **Severity không được đánh đồng với Probability**. Một harm có thể rất nghiêm trọng nhưng xác suất thấp, ví dụ privacy leak dữ liệu học sinh. Ngược lại, một harm có thể không gây hậu quả ngay lập tức nhưng xảy ra thường xuyên, ví dụ AI cho gợi ý quá trực tiếp làm học sinh phụ thuộc.

Tương tự, **Scale không phải Severity**. Một lỗi nhỏ nhưng triển khai trên toàn district vẫn có scale cao. Một lỗi nghiêm trọng ở một học sinh có severity cao nhưng scale thấp.

## 7. Assumption và limitation

Bài này không kết luận rằng AI tutor luôn có hại. Một số case như Tutor CoPilot cho thấy AI có thể cải thiện kết quả học tập nếu được thiết kế theo hướng hỗ trợ con người. Tuy nhiên, bài tập tập trung vào risk profile, nên phân tích ưu tiên các failure mode, harm và guardrails cần thiết trước khi rollout rộng.

Một số case có nguồn dạng investigative journalism hoặc allegation. Với các case đó, bài dùng từ **“cáo buộc”**, **“reported”**, hoặc **“whistleblower alleged”** thay vì ghi như kết luận pháp lý cuối cùng.