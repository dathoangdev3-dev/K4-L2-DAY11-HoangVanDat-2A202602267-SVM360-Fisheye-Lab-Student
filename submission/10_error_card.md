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

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này.

### Lỗi nổi bật nhất: SPURIOUS (19 ca) — tập trung ở mid và center

**Nguyên nhân khả dĩ (`why`):**
- `E0_reference_defect` (mid/center): Vật nhìn thấy rõ ≥40 px nhưng teaching reference không box, ví dụ `adasind_069450.jpg` L5 — xe cart/e-rickshaw xanh bên phải. Số SPURIOUS cao một phần do reference thiếu box cho vật nhỏ/tĩnh ở mid mà annotator thêm vào đúng luật.
- `E4_model_domain` (mid): YOLO26m tạo nhiều `M_only` ở zone mid (8 ca, `zone_table.md`) — các box model này không có ở L hay R, góp vào bức tranh SPURIOUS ở mid khi nhìn từ góc độ ba nguồn (L/R/M).
- `E2_guideline_gap` (edge): `adasind_082170.jpg` L2+R5 — cùng một Bike sát mép trái kính, IoU rơi xuống [0.3, 0.5] do fisheye kéo méo box; L và R đều thấy vật nhưng ghép hình học thất bại → vật bị tính là L_only (spurious) và R_only (missing) cùng lúc.

**Cách sửa và ai nhận việc (`owner`):**
- `guideline` (Ticket 1, `30_escalation_ticket.md`): Bổ sung ví dụ R04 cho Truck vs ThreeWheeler mép trái bị cắt và lóa nắng; làm rõ ngưỡng khi dùng `ignore_region reason=unreadable` thay vì đoán class.
- `annotator` (tự sửa): Ca `adasind_102750.jpg` R5+M8 — Truck nhỏ ở center mà L bỏ sót; thêm box sau khi xác nhận H≥40 trên ảnh gốc.
- `ai_team` (Ticket 2, `30_escalation_ticket.md`): Soi hard negative mid/edge của YOLO26m trên ảnh fisheye gốc — nhiều `M_only` ở mid gây nhiễu prefill.

**Bằng chứng:**
- Ảnh gốc `adasind_069450.jpg` + `r1_craft/compare.html`: L5 mid SPURIOUS — vật nhìn thấy, reference không có box → `E0_reference_defect`, `action=keep_with_reason`.
- `local_quality.md`: ThreeWheeler precision=0.667 (3 FP); Truck recall=0.333 (2 FN) — class yếu nhất là Truck, chủ yếu do ca `adasind_102750.jpg` (`local_quality_conflicts.csv`).
- `r3_diag/model_compare.html`: `adasind_082170.jpg` M2/M5/M6/M7/M9 đều `M_only` ở mid — 5 box model không có đối chiếu trong L hay R.
- `iou_sweep.md`: Kết quả ghép ở IoU=0.3 cao hơn đáng kể so với IoU=0.5 tại zone edge, xác nhận BOX_GEOMETRY là hiện tượng fisheye chứ không phải vẽ sai class.
- `screenshots/adasind_102750.png`, `screenshots/adasind_082170.png`: ảnh chụp minh chứng được dẫn từ `30_escalation_ticket.md`.
