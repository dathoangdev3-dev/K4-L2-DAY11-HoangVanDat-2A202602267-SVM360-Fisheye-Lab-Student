# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 6 | 1 | 1 | 1 | 3 | SPURIOUS (1) |
| mid | 6 | 0 | 1 | 4 | 8 | SPURIOUS (1) |
| edge | 6 | 2 | 2 | 4 | 1 | BOX_GEOMETRY (1) |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: Model gãy nhiều nhất ở mid với 4 missing và 8 thừa; người gãy nhiều nhất ở edge với 2 missing và 2 thừa.
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: Ở edge hình học fisheye làm box khó bám vật và dễ bị cắt; ở mid model có nhiều box thừa. Slice chỉ có ba frame nên không đủ để kết luận theo thời gian hoặc theo camera khác.
