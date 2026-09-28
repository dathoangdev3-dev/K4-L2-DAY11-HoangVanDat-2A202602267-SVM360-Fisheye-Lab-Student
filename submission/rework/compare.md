# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_069450.jpg
- L5 mid SPURIOUS
## adasind_082170.jpg
- L2+R5 edge BOX_GEOMETRY
## adasind_102750.jpg
- L2+R2 edge WRONG_CLASS
- L5 center SPURIOUS
- R5 center MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 6 | 5 | 1 | 1 |
| mid | 6 | 6 | 0 | 1 |
| edge | 6 | 4 | 2 | 2 |
