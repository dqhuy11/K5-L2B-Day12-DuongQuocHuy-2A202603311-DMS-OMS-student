# Tự đánh giá — Dương Quốc Huy · G01

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S02_rgb | `hand` (2 box) | `extra` | Gán `hand` trên ảnh OMS, trong khi `hand` chỉ dùng cho DMS (GUIDE 4.1, 4.3). Cùng lỗi ở S02_ir, S04_ir | Đã sửa trong `export_final_v2.zip` |
| S04_rgb | `hand` (2 box) | `extra` | Cùng lỗi trên, lần sửa đầu còn sót 2 box ở ảnh này, kiểm lại v2 mới phát hiện | Đã sửa trong `export_final_v2.zip` |
| D04 | `face`: `eye_left`, `eye_right` | `lr_flip` | Ghi trạng thái hai mắt ngược bên. Ảnh D## xoay 90°: mắt trái của tài xế là bên có y lớn hơn (GUIDE 4.4-2) | Chưa sửa, ghi nhận tại đây |
| D06 | `face`: `eye_left`, `eye_right` | `ok` | Hai mí khép rõ nên `closed` là đúng (GUIDE 4.5); Hiếu ghi `open` | Không cần sửa |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: gán `hand` trên ảnh OMS (S02_rgb, S02_ir, S04_rgb, S04_ir — 8 box), dù `hand` chỉ là label của DMS.

Vì sao mình mắc: thấy tay rõ trên ảnh là vẽ theo thói quen từ phần DMS, không nhìn lại cột "Dùng ở" trong bảng GUIDE 4.1. `cabin_check` cũng không báo lỗi này nên mình không phát hiện khi tự kiểm.

Lần sau tránh bằng cách: trước khi gán mỗi phần, đọc lại danh sách label của phần đó (ảnh S## chỉ có `frame_meta`, `person`, `face`, `child_seat`, `infant_seat`, `object`). Sau khi export, đếm label theo từng ảnh để chắc ảnh S## không có `hand`, `face13`, `phone`.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: dòng `S02_rgb | hand | box | chỉ có ở mine` — Hiếu không vẽ `hand` trên ảnh OMS và đúng theo GUIDE 4.1. Mình học được là `cabin_check` báo 0 lỗi chưa chắc là bài đúng; so với bản của bạn mới lộ ra những lỗi script không kiểm, nên phải đối chiếu lại guideline chứ không chỉ dựa vào script.
