# Case 01 — LAUSD Ed AI chatbot / AllHere

## A. Brief Case

| Field | Nội dung |
|---|---|
| Tên case | LAUSD Ed AI chatbot / AllHere |
| Ngành | Giáo dục / AI tutor |
| Tổ chức / sản phẩm | Los Angeles Unified School District (LAUSD), AllHere Education, sản phẩm “Ed” |
| Use case AI | AI learning acceleration platform / chatbot cá nhân hóa cho học sinh và phụ huynh: phân tích dữ liệu điểm số, attendance, district offerings; đề xuất tài nguyên học tập, nhắc việc, hỗ trợ nhiều ngôn ngữ. |
| Thời điểm | Launch: 20/03/2024. Chatbot bị tạm vô hiệu hóa sau khủng hoảng AllHere vào tháng 06–07/2024. |
| Case xảy ra chuyện gì? | LAUSD ra mắt Ed như một nền tảng AI cá nhân hóa để hỗ trợ học sinh và phụ huynh. Sau đó, AllHere gặp khủng hoảng tài chính, chatbot bị tạm ngưng, và có cáo buộc từ whistleblower rằng sản phẩm xử lý/chia sẻ dữ liệu học sinh không đúng nguyên tắc tối thiểu hóa dữ liệu. LAUSD cho biết chỉ khôi phục chatbot khi phần human-in-the-loop được tái thiết lập. |
| Stakeholder bị ảnh hưởng | Học sinh K-12, phụ huynh, giáo viên, district, vendor, cộng đồng trường học. |
| Số liệu chính | LAUSD có hơn **520,000 học sinh**; AllHere được mô tả là hỗ trợ hơn **9,100 trường ở 36 bang**. The 74 đưa tin hợp đồng chatbot trị giá **6 triệu USD**, LAUSD đã trả **3 triệu USD**, và whistleblower cáo buộc **7/8 chatbot requests** được gửi tới server ngoài nước Mỹ. |
| Trích nguồn ngắn | LAUSD mô tả Ed là nền tảng AI tạo action plan cá nhân hóa dựa trên dữ liệu học sinh; The 74 đưa tin chatbot bị điều tra vì cáo buộc rủi ro dữ liệu học sinh và tạm disable khi vendor gặp khủng hoảng. |
| Nguồn 1 | Primary — LAUSD Newsroom, “Los Angeles Unified Launches Ed...” 20/03/2024: https://www.lausd.org/apps/news/article/2087148?categoryId=23516 |
| Nguồn 2 | Secondary investigative — The 74, “L.A. Schools Probe Charges its Hyped, Now-Defunct AI Chatbot Misused Student Data”, 10/07/2024: https://www.the74million.org/article/chatbot-los-angeles-whistleblower-allhere-ai/ |
| Ghi chú độ tin cậy | LAUSD là nguồn chính thức về mục tiêu, tính năng, quy mô district. The 74 là nguồn điều tra thứ cấp, có trích lời whistleblower và thông tin hợp đồng; phần “misused student data” nên ghi là **cáo buộc / allegations**, không ghi như kết luận pháp lý cuối cùng. |

## B. Harm Map Worksheet

| High-risk moment | Stakeholder bị ảnh hưởng | Failure mode | Layer bắt đầu lỗi | Harm xảy ra là gì? | Harm lens | Severity | Scale | Probability | Frequency | Vì sao? |
|---|---|---|---|---|---|---|---|---|---|---|
| AI chatbot dùng dữ liệu học sinh để cá nhân hóa câu trả lời | Học sinh, phụ huynh | Privacy leak | Data / Safety / Vendor governance | Dữ liệu học sinh bị đưa vào prompt hoặc chia sẻ cho bên thứ ba nhiều hơn mức cần thiết | Privacy loss | **High** | **High** | **Medium** | **Medium** | Dữ liệu K-12 là nhạy cảm; nếu rollout toàn district thì ảnh hưởng rất rộng. Case này có cáo buộc cụ thể về PII trong prompt và request đi qua server ngoài nước Mỹ. |
| District triển khai AI ở quy mô lớn trước khi audit/ownership rõ | Học sinh, trường, district | Escalation failure | Governance / UX | Khi vendor khủng hoảng, chatbot bị tắt, phụ huynh/học sinh mất kênh hỗ trợ đã được quảng bá | Opportunity loss / Trust loss | **Medium → High** | **High** | **Medium** | **Medium** | AI education product cần continuity plan. Nếu phụ huynh/học sinh phụ thuộc vào kênh này, việc tắt đột ngột làm giảm trust và hỗ trợ học tập. |
| AI đưa đề xuất học tập dựa trên dữ liệu attendance/grades nhưng thiếu human review | Học sinh | Hallucination / Misclassification | Model / Grounding | Gợi ý sai tài nguyên, sai level, hoặc ưu tiên sai nhu cầu học tập | Opportunity loss | **Medium** | **High** | **Medium** | **High** | Với học sinh đông, lỗi nhỏ trong logic cá nhân hóa có thể lặp lại nhiều lần. Không phải lỗi nào cũng nghiêm trọng ngay, nhưng có thể tích lũy thành learning gap. |

## C. Nhận xét case

Case LAUSD Ed cho thấy rủi ro của AI tutor không chỉ là “model trả lời sai”, mà còn nằm ở **governance, vendor risk, privacy architecture và rollout discipline**. Khi sản phẩm dùng dữ liệu học sinh để cá nhân hóa, team cần chứng minh được dữ liệu nào được gửi đi, gửi cho ai, lưu ở đâu, có de-identify không, có human-in-the-loop không và có kill switch/rollback plan không.

## D. Product Recommendation / Fix First

Nếu là product team phụ trách một AI tutor hoặc learning chatbot triển khai ở quy mô district, tôi sẽ ưu tiên sửa các điểm sau:

### 1. Làm rõ data flow trước khi rollout

Trước khi chatbot được dùng thật, team cần có sơ đồ dữ liệu rõ ràng:

- Dữ liệu học sinh nào được lấy từ SIS/LMS?
- Dữ liệu nào được đưa vào prompt?
- Dữ liệu nào được gửi cho LLM/vendor?
- Dữ liệu nào được lưu lại trong log?
- Log lưu bao lâu?
- Ai có quyền truy cập?
- Khi phụ huynh/học sinh yêu cầu xóa dữ liệu thì xử lý thế nào?

Với sản phẩm cho học sinh K-12, nguyên tắc nên là **minimum necessary data**. Nếu chỉ cần biết grade level và topic đang học, không nên gửi thêm tên, attendance, điểm số đầy đủ hoặc thông tin gia đình.

### 2. Tách PII khỏi prompt mặc định

AI tutor không nên mặc định đưa PII vào prompt. Cần có lớp xử lý trước model:

- Redact tên học sinh nếu không cần thiết.
- Không gửi email, số điện thoại, địa chỉ, student ID.
- Dùng pseudonymous user ID thay vì định danh thật.
- Chỉ lấy vài field cần thiết cho câu trả lời hiện tại.
- Có test tự động để phát hiện prompt chứa PII.

### 3. Vendor governance phải là requirement sản phẩm

Case này cho thấy rủi ro không chỉ nằm ở model mà còn nằm ở vendor. Vì vậy, trước khi ký hoặc rollout, cần yêu cầu:

- Data Processing Agreement rõ ràng.
- Danh sách subprocessor.
- Quy định dữ liệu được xử lý ở đâu.
- Cam kết không dùng dữ liệu học sinh để train model ngoài phạm vi hợp đồng.
- Audit log và quyền kiểm tra.
- Kế hoạch exit nếu vendor phá sản, bị mua lại, hoặc dừng dịch vụ.

### 4. Human-in-the-loop cho nội dung ảnh hưởng học tập

Nếu chatbot đưa gợi ý liên quan đến lộ trình học, can thiệp học tập, hoặc thông tin quan trọng cho phụ huynh, cần có cơ chế human review:

- AI chỉ gợi ý, không ra quyết định cuối.
- Giáo viên/counselor có dashboard xem các gợi ý quan trọng.
- Những câu trả lời có confidence thấp phải được chuyển người thật.
- Phụ huynh/học sinh có nút report câu trả lời sai.

### 5. Rollout theo giai đoạn, không mở rộng ngay

Không nên triển khai toàn district ngay từ đầu. Nên rollout theo các bước:

1. Internal test với dữ liệu giả.
2. Pilot nhỏ với một số lớp/trường.
3. Review privacy + safety + learning quality.
4. Mở rộng có giới hạn.
5. Chỉ rollout rộng khi metric ổn định.

Mỗi giai đoạn cần có threshold dừng lại, ví dụ:

- Tỉ lệ câu trả lời bị report vượt ngưỡng.
- Phát hiện prompt chứa PII.
- Vendor downtime kéo dài.
- AI đưa gợi ý sai nghiêm trọng.
- Human review backlog quá lớn.

### 6. Chuẩn bị kill switch và fallback

Với AI chatbot cho trường học, không thể chỉ có “on/off” thủ công sau khi sự cố xảy ra. Cần chuẩn bị trước:

- Kill switch cho từng tính năng.
- Fallback sang FAQ/static resources.
- Fallback sang giáo viên/counselor/support staff.
- Thông báo minh bạch cho phụ huynh/học sinh khi tính năng bị tắt.
- Kế hoạch khôi phục sau sự cố.

### 7. Evidence cần thu thập

Để chứng minh hệ thống an toàn hơn, product team nên lưu các bằng chứng sau:

| Evidence | Mục đích |
|---|---|
| Data flow diagram | Chứng minh dữ liệu đi qua đâu |
| Prompt PII audit report | Chứng minh prompt không chứa dữ liệu nhạy cảm không cần thiết |
| Vendor review checklist | Chứng minh đã kiểm tra vendor/subprocessor |
| Incident response plan | Chứng minh có kế hoạch xử lý sự cố |
| Human escalation logs | Chứng minh AI không tự xử lý các case rủi ro cao |
| Pilot evaluation report | Chứng minh đã test trước khi rollout rộng |

### Kết luận recommendation

Ưu tiên số 1 của case LAUSD Ed không phải là làm chatbot thông minh hơn, mà là làm hệ thống **kiểm soát dữ liệu, vendor, human review và rollback** tốt hơn. Với AI giáo dục, privacy và governance phải được xem là core product feature, không phải phần phụ sau khi launch.