# Danh sách lớp v0 — Dương Quốc Huy · G01

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_left / eye_right | open / closed / unknown | | |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | | |
| 3 | glasses | none / clear / sun / unknown | | |
| 4 | hand.on_wheel | yes / no / unknown | | |
| 5 | phone.state | held / mounted / lap | | |
| 6 | face13 | 13 điểm mặt, cờ occluded / outside | | |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person.seat | driver / front_passenger / rear_left / rear_middle / rear_right | | |
| 2 | person.seatbelt | worn_correct / worn_incorrect / not_worn / unknown | | |
| 3 | child_seat.occupied | no / yes / unknown | | |
| 4 | infant_seat.facing | rear / front | | |
| 5 | object.type | bag / box / cup / other | | |
| 6 | frame_meta.camera_blocked | yes / no | | |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: …
   Khung ví dụ: …
   Bạn tạm gán thế nào và vì sao: …
2. Câu hỏi: …
   Khung ví dụ: …
   Bạn tạm gán thế nào và vì sao: …
