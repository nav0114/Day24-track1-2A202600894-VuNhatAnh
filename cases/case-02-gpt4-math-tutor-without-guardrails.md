# Case 02 — GPT-4 math tutor without guardrails

## A. Brief Case

| Field | Nội dung |
|---|---|
| Tên case | GPT-4 math tutor without guardrails |
| Ngành | Giáo dục / AI tutor |
| Tổ chức / sản phẩm | Nghiên cứu của Hamsa Bastani và cộng sự; 2 phiên bản GPT-4 tutor: “GPT Base” và “GPT Tutor” |
| Use case AI | Dùng GPT-4 như tutor hỗ trợ học sinh trung học học toán trong các buổi practice problem. GPT Base giống giao diện ChatGPT chuẩn; GPT Tutor được prompt/thiết kế để safeguard learning, ví dụ hướng dẫn bằng hint thay vì cho đáp án trực tiếp. |
| Thời điểm | Working paper 2024; bản PNAS 2025. |
| Case xảy ra chuyện gì? | Trong field experiment với gần 1,000 học sinh trung học, việc có GPT-4 hỗ trợ giúp điểm practice tăng mạnh trong lúc được dùng AI. Nhưng khi AI bị lấy đi, nhóm dùng GPT Base làm bài kém hơn nhóm không có AI, cho thấy học sinh có thể dùng AI như “crutch” và học kém bền vững nếu thiếu guardrails. GPT Tutor có safeguard thì giảm đáng kể tác động xấu này. |
| Stakeholder bị ảnh hưởng | Học sinh, giáo viên toán, trường học, product team xây AI tutor. |
| Số liệu chính | GPT Base cải thiện performance khi practice **48%**, GPT Tutor cải thiện **127%**; khi không còn access, nhóm GPT Base giảm **17%** so với nhóm không được dùng AI. Nghiên cứu diễn ra với gần **1,000 học sinh** và phần AI tutor chiếm khoảng **15% curriculum** ở 3 khối lớp. |
| Trích nguồn ngắn | Nghiên cứu cho thấy AI tutor không có guardrails có thể làm học sinh phụ thuộc vào AI, đạt kết quả tốt trong lúc practice nhưng giảm năng lực tự làm khi AI không còn. |
| Nguồn 1 | Primary peer-reviewed — PNAS, “Generative AI without guardrails can harm learning”, 2025: https://www.pnas.org/doi/10.1073/pnas.2422633122 |
| Nguồn 2 | Primary preprint/working paper — SSRN, “Generative AI Can Harm Learning”, 15/07/2024: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4895486 |
| Ghi chú độ tin cậy | Đây là nguồn nghiên cứu primary, có thiết kế field experiment. PNAS là nguồn học thuật mạnh; SSRN dùng để đối chiếu abstract và số liệu. Cần lưu ý đây là ngữ cảnh học toán trung học, không tự động suy rộng sang mọi môn học. |

## B. Harm Map Worksheet

| High-risk moment | Stakeholder bị ảnh hưởng | Failure mode | Layer bắt đầu lỗi | Harm xảy ra là gì? | Harm lens | Severity | Scale | Probability | Frequency | Vì sao? |
|---|---|---|---|---|---|---|---|---|---|---|
| Học sinh dùng AI trong practice và nhận lời giải quá trực tiếp | Học sinh | Over-reliance | UX / Prompt / Safety | Học sinh hoàn thành bài nhưng không hình thành kỹ năng tự giải | Opportunity loss / Learning loss | **High** | **Medium → High** | **High** | **High** | Số liệu 17% giảm khi mất access cho thấy harm có thể xuất hiện sau giai đoạn practice. Đây là lỗi thiết kế tutor-not-solver. |
| AI ưu tiên đáp án đúng thay vì quá trình học | Học sinh, giáo viên | Harmful advice / Sycophancy | Model / UX | AI làm học sinh tưởng mình hiểu bài, nhưng thực ra chỉ theo lời giải AI | Misinformation / Learning quality | **Medium → High** | **Medium** | **High** | **High** | LLM dễ tối ưu theo “giải xong bài” thay vì kiểm tra understanding. |
| Trường/product team nhìn vào short-term score và tưởng sản phẩm hiệu quả | Nhà trường, product team, học sinh | Measurement failure | Evaluation / Governance | Ship AI tutor dựa trên metric ngắn hạn, bỏ qua skill retention | Opportunity loss | **High** | **High** | **Medium** | **Medium** | Case này cho thấy điểm practice tăng nhưng learning dài hạn có thể giảm. Nếu metric sai, rollout rộng sẽ khuếch đại harm. |

## C. Nhận xét case

Case này là bằng chứng mạnh cho nguyên tắc **“AI tutor không được chỉ là answer machine”**. Với sản phẩm học tập, metric chính không nên chỉ là số câu đúng trong lúc có AI, mà phải đo retention, transfer, khả năng tự làm khi không có AI, mức độ AI “give away answer”, và chất lượng hint. Guardrails quan trọng nhất là ép AI hỏi dẫn dắt, kiểm tra từng bước, và chỉ đưa đáp án khi đã đủ scaffold.

## D. Product Recommendation / Fix First

Nếu là product team xây AI math tutor, tôi sẽ ưu tiên sửa theo hướng **tutor-not-solver**. Mục tiêu không phải là giúp học sinh có đáp án nhanh nhất, mà là giúp học sinh tự hình thành năng lực giải bài.

### 1. Chặn answer leakage

AI không nên đưa lời giải đầy đủ ngay từ lượt đầu. Thay vào đó, hệ thống nên dùng progressive disclosure:

1. Hỏi học sinh đã hiểu đề chưa.
2. Gợi ý bước đầu tiên.
3. Yêu cầu học sinh thử làm.
4. Phản hồi lỗi cụ thể.
5. Gợi ý tiếp nếu học sinh vẫn kẹt.
6. Chỉ đưa lời giải đầy đủ khi đã qua nhiều bước scaffold.

Ví dụ policy:

| Tình huống | AI nên làm | AI không nên làm |
|---|---|---|
| Học sinh hỏi “đáp án là gì?” | Hỏi lại cách em đang nghĩ, gợi ý bước đầu | Đưa ngay đáp án cuối |
| Học sinh làm sai một bước | Chỉ ra lỗi ở bước đó | Làm lại toàn bộ bài |
| Học sinh bế tắc | Đưa hint nhỏ hơn | Copy lời giải mẫu |
| Học sinh đã thử nhiều lần | Cho lời giải có giải thích | Chỉ đưa đáp án không giải thích |

### 2. Thêm “struggle time” hợp lý

Nếu AI can thiệp quá sớm, học sinh không có thời gian tự suy nghĩ. Product nên có cơ chế giữ một khoảng “productive struggle”:

- Không đưa hint ngay khi học sinh vừa đọc đề.
- Yêu cầu học sinh thử ít nhất một bước.
- Cho phép học sinh chọn mức hint: nhẹ, vừa, mạnh.
- Ghi lại số lần học sinh xin hint.
- Cảnh báo giáo viên nếu học sinh luôn xin đáp án ngay.

### 3. Đo retention, không chỉ đo practice score

Case này cho thấy practice score có thể tăng nhưng learning thật lại giảm. Vì vậy, evaluation cần có nhiều tầng:

| Metric | Câu hỏi cần trả lời |
|---|---|
| Practice accuracy | Học sinh làm đúng trong lúc có AI không? |
| Hint usage | Học sinh cần bao nhiêu hint để làm được? |
| Answer leakage rate | AI có đưa đáp án quá sớm không? |
| Retention test | Sau vài ngày, học sinh còn làm được không? |
| No-AI test | Khi không có AI, học sinh tự làm được không? |
| Transfer test | Học sinh giải được bài biến thể không? |
| Confidence calibration | Học sinh có tưởng mình hiểu bài quá mức không? |

Metric quan trọng nhất là **khả năng tự làm khi không có AI**, không phải chỉ là số câu đúng trong lúc dùng AI.

### 4. Thiết kế AI như Socratic tutor

Prompt và UX nên buộc AI dạy theo kiểu hỏi dẫn dắt:

- “Em thử nêu bước đầu tiên xem?”
- “Vì sao em chọn công thức đó?”
- “Có cách nào kiểm tra lại đáp án không?”
- “Nếu thay số khác vào thì cách làm có đổi không?”
- “Em giải thích lại bằng lời của em được không?”

AI nên đóng vai trò người hướng dẫn, không phải máy giải bài.

### 5. Phát hiện dấu hiệu phụ thuộc AI

Product nên có tín hiệu cảnh báo khi học sinh có pattern phụ thuộc:

| Tín hiệu | Ý nghĩa |
|---|---|
| Hỏi đáp án ngay ở hầu hết bài | Có thể đang dùng AI như answer machine |
| Không nhập bước giải nào | Chưa có evidence về reasoning |
| Copy lại lời AI gần như nguyên văn | Có thể không hiểu thật |
| Điểm practice cao nhưng no-AI quiz thấp | Learning không bền |
| Xin hint mạnh quá thường xuyên | Cần giáo viên can thiệp |

Khi có dấu hiệu này, AI nên giảm mức trợ giúp và chuyển sang hỏi dẫn dắt nhiều hơn.

### 6. Teacher dashboard

Giáo viên cần nhìn thấy không chỉ điểm số, mà cả cách học sinh dùng AI:

- Học sinh dùng bao nhiêu hint.
- Bài nào AI phải can thiệp nhiều.
- Bài nào học sinh xin đáp án sớm.
- Chủ đề nào học sinh fail khi không có AI.
- AI có bị report vì cho lời giải quá trực tiếp không.

Teacher dashboard giúp biến AI tutor thành công cụ hỗ trợ giáo viên thay vì thay thế giáo viên.

### 7. Evaluation test set trước khi ship

Trước khi ship, team nên có test set cho từng dạng bài:

| Test | Mục tiêu |
|---|---|
| Direct answer request test | Kiểm tra AI có từ chối đưa đáp án ngay không |
| Wrong student reasoning test | Kiểm tra AI có sửa đúng lỗi tư duy không |
| Multi-step problem test | Kiểm tra AI có scaffold từng bước không |
| Confused student test | Kiểm tra AI có giải thích đơn giản hơn không |
| Retention simulation | Kiểm tra học sinh có thể tự làm lại không |
| Grade-level language test | Kiểm tra câu trả lời có phù hợp độ tuổi không |

### Kết luận recommendation

Ưu tiên số 1 của case GPT-4 math tutor là sửa **learning design**. AI tutor không được tối ưu cho “làm xong bài”, mà phải tối ưu cho “học sinh tự giải được bài sau đó”. Vì vậy, guardrails quan trọng nhất là chống answer leakage, đo retention/no-AI performance và thiết kế AI theo hướng hỏi dẫn dắt.