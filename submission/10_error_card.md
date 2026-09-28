# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B2 | MISSING | 4 |
| center | B2 | SPURIOUS | 5 |
| center | C0 | SPURIOUS | 1 |
| edge | B2 | BOX_GEOMETRY | 2 |
| edge | B2 | MISSING | 3 |
| edge | B2 | SPURIOUS | 4 |
| edge | B2 | WRONG_CLASS | 2 |
| mid | B2 | MISSING | 2 |
| mid | B2 | SPURIOUS | 8 |
| mid | C0 | SPURIOUS | 1 |

## Top defects
- SPURIOUS: 19 (ví dụ frame adasind_019560.jpg)
- MISSING: 9 (ví dụ frame adasind_102750.jpg)
- BOX_GEOMETRY: 2 (ví dụ frame adasind_082170.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: TODO
- Cách sửa và ai nhận việc (`owner`): TODO
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): TODO
