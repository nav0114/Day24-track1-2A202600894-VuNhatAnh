# Day24-Track1-2A202600894-VuNhatAnh

## Day 24 Lab — Case Study Hunt và Harm Map theo ngành

**Học viên:** Vũ Nhật Anh  
**Mã học viên:** 2A202600894  
**Track:** Track 1  
**Ngành chọn:** Giáo dục / AI tutor  

## Checklist nộp bài

- [x] 1 Industry Risk Snapshot
- [x] 3 Brief Case trong cùng ngành Giáo dục / AI tutor (Khanmigo, Texas A&M ChatGPT, Turnitin AI Detection)
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
│   ├── case-01-khanmigo-math-errors.md
│   ├── case-02-texas-am-chatgpt-grading.md
│   └── case-03-turnitin-ai-detection-false-positives.md
├── group
│   └── industry-risk-comparison.md
└── sources.md
```

## Danh sách case đã chọn (Cá nhân - Vũ Nhật Anh)

| Case | Ngành | Trọng tâm rủi ro |
|---|---|---|
| Khanmigo Math Errors | Giáo dục / AI tutor | Hallucination, misinformation, thiếu grounding trong tính toán. |
| Texas A&M ChatGPT Grading Scandal | Giáo dục / AI tutor | Over-reliance, automation bias, dignity loss, opportunity loss. |
| Turnitin AI Detection False Positives | Giáo dục / AI tutor | Bias/fairness, false positives, ảnh hưởng sinh viên ESL, dignity loss. |

## Kết luận ngắn

Risk profile của ngành **Giáo dục / AI tutor** là **High**. Rủi ro trong lĩnh vực này không gây sát thương vật lý nhưng tạo ra các hậu quả sâu sắc về **danh dự (dignity loss)** và **cơ hội học tập (opportunity loss)**. Thông qua các case study, có thể thấy xu hướng rủi ro đến từ việc người dùng (đặc biệt là giáo viên) quá phụ thuộc (over-reliance) vào các công cụ AI chưa hoàn thiện để đưa ra các quyết định kỷ luật (Texas A&M, Turnitin), cũng như lỗi hallucination cơ bản khi AI làm gia sư (Khanmigo). Để an toàn, sản phẩm AI trong giáo dục phải minh bạch về ranh giới sai số và bắt buộc có sự can thiệp của con người (human-in-the-loop) trước các quyết định quan trọng.
