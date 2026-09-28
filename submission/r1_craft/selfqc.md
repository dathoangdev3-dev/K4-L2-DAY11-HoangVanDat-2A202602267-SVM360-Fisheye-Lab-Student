# Tự soát

Nguồn: `final_b2_day11.zip` đã khóa mã `E999-723D` (SHA256 `e999723dd7f47603e85221ccad8c6a37508daac2ebcae44f7d165a4e4fa7a9e5`). Bản nháp `exports/r1-draft.xml` được tạo lại từ cùng ZIP.

- Tên task thiếu raw_fisheye

Ghi chú sau khi soát ảnh gốc B2-edge (`adasind_069450.jpg`, `adasind_082170.jpg`, `adasind_102750.jpg`):

- Đã bỏ box cao dưới H=40 px so với khóa cũ `CF0B-A49C`.
- Mỗi frame có `ignore_region` `lens_border` và `ego_body` (thân xe/tay lái nhìn thấy).
- Cảnh báo tên task: meta XML là `Bus`, không chứa `raw_fisheye`; định dạng vẫn CVAT for images 1.1. Đã ghi `40_decision_log.csv`.
- Không vẽ polygon K12 (`degrade k12`).

## Checklist thủ công
- [x] Phạm vi H=40 và vật cần vẽ
- [x] lens_border và ego_body
- [x] Class sáu nhãn
- [x] Rider và Bike
- [x] Geometry trên ảnh fisheye gốc
- [x] truncated và occluded
- [x] Vật thiếu hoặc box trùng
- [x] ignore_region có reason
- [ ] Tên task raw_fisheye và export CVAT 1.1

## Fill ratio (K12)
chưa vẽ polygon K12 (degrade)
