# Danh sách lớp v0 — Dương Quốc Huy · G01

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_left / eye_right | open / closed / unknown | Phát hiện buồn ngủ: mắt nhắm kéo dài qua nhiều khung hình | Có, trừ khi phản xạ đèn NIR trên kính hoặc kính râm che mắt (ví dụ D03) thì phải `unknown` |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung (nhìn khỏi đường quá lâu); kiểm tra tài xế có nhìn gương trước khi chuyển làn | Có, dựa vào hướng đầu và mắt; kém tin cậy khi mắt bị che |
| 3 | glasses | none / clear / sun / unknown | Cho model biết khi nào trạng thái mắt không đáng tin, để không báo buồn ngủ sai | Một phần: trên NIR kính râm có thể trông như kính trong, không chắc thì `unknown` |
| 4 | hand.on_wheel | yes / no / unknown | Cảnh báo rời tay vô lăng khi xe không ở chế độ tự lái; đánh giá tài xế sẵn sàng tiếp quản | Có, nhận bằng hình dạng bàn tay và vị trí so với vô lăng |
| 5 | phone.state | held / mounted / lap | Phát hiện dùng điện thoại khi lái (`held`), phân biệt với điện thoại trên giá (`mounted`) | Có nếu thấy cạnh, góc hoặc màn hình; vật tối áp tai không rõ hình thì không gán |
| 6 | face13 | 13 điểm mặt, cờ occluded / outside | Đo độ mở mắt, phát hiện ngáp (khoảng cách môi), ước lượng tư thế đầu cho gaze | Có, trừ các điểm bị phản xạ hoặc bị che (đánh cờ thay vì đoán) |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person.seat | driver / front_passenger / rear_left / rear_middle / rear_right | Đếm người theo từng ghế; nhắc thắt dây đúng ghế; điều chỉnh túi khí theo ghế có người | Có, theo hình dạng và vị trí; ghế gọi theo xe, không theo ảnh |
| 2 | person.seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Cảnh báo hành khách không thắt dây hoặc thắt sai | Khó: dây tối chìm trên áo tối nên thường phải `unknown` |
| 3 | child_seat.occupied | no / yes / unknown | Nhắc quên trẻ hoặc đồ trong ghế khi rời xe; biết ghế có ghế trẻ em để điều chỉnh túi khí | Có hình dạng ghế; bên trong ghế đôi khi khó thấy (ví dụ S03_ir, S05_ir nhận bằng hình dạng) |
| 4 | infant_seat.facing | rear / front | Ghế em bé quay về sau đặt ở ghế trước thì phải tắt túi khí | Có, nhận bằng hình dạng nôi |
| 5 | object.type | bag / box / cup / other | Nhắc quên đồ khi rời xe | Có hình dạng; không dùng màu để phân biệt, không chắc thì `other` |
| 6 | frame_meta.camera_blocked | yes / no | Biết khi camera bị che để không tin kết quả các lớp khác và báo lỗi hệ thống | Có: khung hình tối đều hoặc bị vật che sát ống kính |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Điểm mắt nằm sau tròng kính bị lóa phản xạ một phần thì đánh `occluded` hay `outside`? GUIDE 4.6 chỉ nói "`occluded` nếu đoán chắc vị trí", không nói thế nào là đủ chắc; mình và bạn review chọn khác nhau.
   Khung ví dụ: G01 D03 (điểm mắt của tài xế).
   Bạn tạm gán thế nào và vì sao: mắt còn thấy khóe để ước lượng thì `occluded`, mắt không thấy gì thì `outside`, để không đặt điểm "cho đủ".
2. Câu hỏi: Khi hướng nhìn nằm giữa `road` và một vùng khác, không rõ hẳn thuộc vùng nào, có ngưỡng góc nào để chọn không, hay luôn ghi `other`?
   Khung ví dụ: G01 D04 (`gaze_zone`: mình ghi `other`, bạn review ghi `road`).
   Bạn tạm gán thế nào và vì sao: `other` kèm ghi chú, vì GUIDE 4.5 nói không chắc thì chọn `other`; ghi `road` sai sẽ dạy model rằng tài xế đang nhìn đường.
