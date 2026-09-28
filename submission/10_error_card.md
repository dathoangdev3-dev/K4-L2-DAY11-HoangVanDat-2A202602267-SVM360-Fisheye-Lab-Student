# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B2 | SPURIOUS | 3 |
| center | C0 | SPURIOUS | 1 |
| edge | B2 | IGNORE_SCOPE | 2 |
| edge | B2 | MISSING | 2 |
| edge | B2 | SPURIOUS | 3 |
| edge | B2 | WRONG_CLASS | 1 |
| mid | B2 | SPURIOUS | 7 |
| mid | C0 | SPURIOUS | 1 |

## Top defects
- SPURIOUS: 15 (ví dụ frame adasind_019560.jpg)
- IGNORE_SCOPE: 2 (ví dụ frame adasind_069450.jpg)
- MISSING: 2 (ví dụ frame adasind_069450.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Box thừa tập trung ở model M_only của vùng mid và một số box learner ở center/edge; đây là dấu hiệu cần kiểm ảnh gốc thay vì coi mọi khác biệt là lỗi reference.
- Cách sửa và ai nhận việc (`owner`): Annotator rà lại box và ignore scope theo R01/R10; ai_team kiểm các M_only và bổ sung hard negative nếu chúng là false positive.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `submission/screenshots/adasind_082170.png`, `submission/screenshots/adasind_102750.png`, `submission/r3_diag/model_compare.html`, `submission/r3_diag/local_quality_conflicts.csv`.
