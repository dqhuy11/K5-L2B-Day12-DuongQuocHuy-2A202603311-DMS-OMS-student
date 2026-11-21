# Khai báo dùng AI — Dương Quốc Huy

Nhắc lại: không đưa ảnh cabin hay ảnh tài xế (kể cả ảnh chụp màn hình) cho bất kỳ công cụ AI nào. AI chỉ đọc file văn bản (CSV, XML export không kèm ảnh, guideline, script), không xem ảnh.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Claude Code (Claude Opus 5.5) | Giải thích `disagreement_log.csv` và cách điền `verdict` / `guideline_rule` / `action` | Dùng gợi ý mục guideline cho từng nhóm bất đồng; các dòng D## tự xem ảnh trên CVAT cùng bạn review rồi chốt | Đối chiếu với GUIDE §4 và CHECKPOINTS |
| 2 | Claude Code | Cập nhật GUIDE, `labels_cabin_v1.json`, `cabin_schema.py` để thêm `child_seat.occupied = yes` (mentor đã cho phép) | Giữ lại phần sửa | Hỏi mentor trước; chạy lại `cabin_check` |
| 3 | Claude Code | Điền sẵn các dòng chắc chắn trong `disagreement_log.csv` (modality, `hand` và `face` trên ảnh S##, D03 `eye_left`) | Giữ các dòng đó; dòng còn lại tự xử lý | Đối chiếu tên file ảnh, GUIDE §4.1–4.3, cảnh báo của `cabin_check` |
| 4 | Claude Code | Phát hiện box `hand` còn sót trên ảnh OMS trong `export_final_v2.zip` | Tự xóa trên CVAT, export lại | Chạy lại `cabin_check check --expect 22` |
| 5 | Claude Code | Tạo khung các file nộp (TEAM, prompts, tiêu đề các file mẫu) | Tự viết nội dung class list, self review, ir_log, exit ticket | Tự đọc lại |
| 6 | Claude Code | Viết nháp mục "Điều mình học được hôm nay" trong TEAM.md, dựa trên các lỗi thật trong bài | Giữ lại sau khi đọc lại | Đối chiếu với disagreement_log và các lần sửa v2 |
| 7 | Claude Code | Điền `self_review.md` từ các lỗi thật của mình (diff v1/v2, diff với Hiếu): `hand` trên ảnh OMS, đảo trái/phải mắt ở D04 | Giữ lại sau khi đọc lại | Đối chiếu kết quả `cabin_check diff` và ảnh trên CVAT |
| 8 | Claude Code | Nháp `ir_log.csv` từ nhãn trong `export_final_v2.zip` (mắt unknown, cờ face13, ghế S03/S05) | Tự xem lại ảnh trên CVAT để xác nhận hiện tượng rồi mới giữ | Ảnh trên CVAT local |
| 9 | Claude Code | Điền sẵn cột lớp và giá trị của `class_list_v0.md` từ GUIDE 4.1 | Tự viết cột "để làm gì", cột IR và 2 câu hỏi leo thang | Đối chiếu slide 54 |
