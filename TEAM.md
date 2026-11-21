# TEAM — Ngày 12

Mã bộ ảnh: **G01** · Hình thức: nhóm

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Dương Quốc Huy | 2A202603311 | có | Đặng Trung Hiếu (2A202603248) | 43 / 56 |
| Đặng Trung Hiếu | 2A202603248 | có | Dương Quốc Huy (2A202603311) | |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- G01 S03_ir / S03_rgb (ghế `rear_left`), S05_ir / S05_rgb (ghế `rear_left`, `rear_right`) — `child_seat.occupied`: guideline v1.0 không có giá trị `yes`. Mentor cho phép `occupied = yes` khi nhìn thấy có gì đó trong ghế. Đã cập nhật GUIDE §4.1, §4.8, §4.9 và `cabin_schema.py` theo hướng dẫn này.

## Cá nhân

Mỗi người một mục, 1–2 dòng mỗi ý.

### DuongQuocHuy-2A202603311
- Phần mình làm (ngoài 22 ảnh của mình): chạy `cabin_check diff` với bài của Hiếu, xử lý `disagreement_log.csv`, hỏi mentor về ca `occupied = yes`, sửa và export lại `export_final_v2.zip`.
- Điều mình học được hôm nay: mỗi label chỉ dùng đúng phần của nó (mình lỡ gán `hand` lên ảnh OMS S02, S04 vì nghĩ "thấy tay thì vẽ"), và trái/phải luôn tính theo người trong ảnh, nhất là trên ảnh D## xoay 90° (mắt trái có y lớn hơn). Diff với bạn giúp lộ ra những lỗi mà `cabin_check` không bắt được, và ca guideline chưa nói tới thì hỏi coach thay vì tự đặt luật.


