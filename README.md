# Day24-Track1-2A202600873-NguyenLamPhuongThao

## Day 24 Lab — Case Study Hunt và Harm Map theo ngành

**Học viên:** Nguyễn Lâm Phương Thảo  
**Mã học viên:** 2A202600873  
**Track:** Track 1  
**Ngành chọn:** Giáo dục / AI tutor  

## Checklist nộp bài

- [x] 1 Industry Risk Snapshot
- [x] 3 Brief Case trong cùng ngành Giáo dục / AI tutor
- [x] 3 Harm Map Worksheet, mỗi case đi kèm 1 worksheet
- [x] 1 đoạn tổng hợp ngắn về pattern rủi ro của ngành
- [x] 1 file tổng hợp nhóm chứa bảng so sánh risk profile giữa các ngành
- [x] Không đưa API key, token, credential, hoặc dữ liệu cá nhân nhạy cảm vào repo

## Cấu trúc repo

```text
.
├── README.md
├── industry-risk-snapshot.md
├── cases
│   ├── case-01-lausd-ed-ai-chatbot.md
│   ├── case-02-gpt4-math-tutor-without-guardrails.md
│   └── case-03-tutor-copilot-human-ai-tutoring.md
├── group
│   └── industry-risk-comparison.md
└── sources.md
```

## Danh sách case đã chọn

| Case | Ngành | Trọng tâm rủi ro |
|---|---|---|
| LAUSD Ed AI chatbot / AllHere | Giáo dục / AI tutor | Privacy leak, vendor governance, escalation failure |
| GPT-4 math tutor without guardrails | Giáo dục / AI tutor | Over-reliance, skill loss, harmful learning design |
| Tutor CoPilot | Giáo dục / AI tutor | Human-AI tutoring quality, grade-level mismatch, privacy minimization |

## Kết luận ngắn

Risk profile của ngành **Giáo dục / AI tutor** là **High**. AI tutor thường không gây hại thể chất trực tiếp như y tế hoặc xe tự hành, nhưng có thể ảnh hưởng tới chất lượng học, cơ hội học tập, dữ liệu trẻ em, niềm tin của phụ huynh và quyết định giáo dục ở quy mô lớn. Điểm rủi ro lặp lại là AI có thể trông “hữu ích” trong từng lượt tương tác nhưng vẫn tạo hại dài hạn nếu học sinh phụ thuộc, nếu câu trả lời thiếu grounding, hoặc nếu hệ thống dùng dữ liệu học sinh mà chưa có kiểm soát quyền riêng tư và human review đủ mạnh.
