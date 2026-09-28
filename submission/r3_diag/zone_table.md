# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 6 | 1 | 1 | 1 | 3 | SPURIOUS (1) |
| mid | 6 | 0 | 1 | 4 | 8 | SPURIOUS (1) |
| edge | 6 | 2 | 2 | 4 | 1 | BOX_GEOMETRY (1) |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: Model gãy nhiều nhất ở **mid** (4 missing `LR_noM`+`R_only`, 8 thừa `M_only`). Người gãy nhiều nhất ở **edge** (2 missing, 2 spurious; lỗi L chính `BOX_GEOMETRY`). Center của L gần khớp reference (1 missing + 1 spurious trên 6 `n_ref`).
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: Edge fisheye làm IoU rơi xuống dưới 0.5 dù cùng vật (`L2+R5` trên `adasind_082170.jpg`) và làm class Truck/ThreeWheeler khó đọc (`L2+R2` trên `adasind_102750.jpg`). Mid là nơi YOLO26m tạo nhiều box thừa, không chứng minh model kém trên bốn camera. Slice chỉ ba frame một camera; `center/mid/edge` là khoảng cách tới tâm vòng kính, không phải khoảng cách tới xe. Export này đã có `ego_body`; khác biệt L/R còn lại không còn là thiếu ignore.
